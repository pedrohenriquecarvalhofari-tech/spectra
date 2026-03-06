--[[
	WARNING: Heads up! This script has not been verified by ScriptBlox. Use at your own risk!
]]
--// SERVICES
local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")
local RunService = game:GetService("RunService")

local plr = Players.LocalPlayer
local character = plr.Character or plr.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

plr.CharacterAdded:Connect(function(char)
    character = char
    humanoid = char:WaitForChild("Humanoid")
end)

--// UI LIB
local Library = loadstring(game:HttpGet("https://pastefy.app/TYVuPNOS/raw"))()

local Window = Library:MakeWindow({
    Title = "SPECTRA HUB",
    SubTitle = "DESOFUSCADO POR GPT E GTVZ MODDED CRACKED",
    LoadText = "Carregando Spectra",
    Flags = "Spectrahub_Brookhaven"
})

Window:AddMinimizeButton({
    Button = { Image = "rbxassetid://102760953257719", BackgroundTransparency = 0 },
    Corner = { CornerRadius = UDim.new(35, 1) }
})

--////////////////////////////////////////////////////
--// TAB CRÉDITOS
local Tab1 = Window:MakeTab({
    Title = "Créditos",
    Icon = "rbxassetid://76311199408449"
})

--==============================
-- CRÉDITOS DO HUB
--==============================
Tab1:AddSection({"Créditos do Hub"})

Tab1:AddDiscordInvite({
    Name = "Spectra Hub",
    Description = "Comunidade oficial do Hub",
    Logo = "rbxassetid://ID IMAGEM",
    Invite = "",
})

--==============================
-- DETECTOR DE EXECUTOR
--==============================
local function detectExecutor()
    if identifyexecutor then
        return identifyexecutor()
    elseif syn then
        return "Synapse X"
    elseif KRNL_LOADED then
        return "KRNL"
    elseif is_sirhurt_closure then
        return "SirHurt"
    elseif pebc_execute then
        return "ProtoSmasher"
    elseif getexecutorname then
        return getexecutorname()
    else
        return "Executor Desconhecido"
    end
end

local executorName = detectExecutor()

-- Executor
Tab1:AddParagraph({
    "Executor",
    executorName
})

-- 👇 NOME REAL DO JOGADOR (LOGADO)
Tab1:AddParagraph({
    "Jogador",
    game:GetService("Players").LocalPlayer.Name
})

--==============================
-- VERSÃO DO HUB
--==============================
Tab1:AddSection({"Versão do Hub"})

Tab1:AddParagraph({
    "Inversão do Hub",
    "V9999999"
})

--==============================
-- CRIADORES
--==============================
Tab1:AddSection({"Criadores"})

Tab1:AddParagraph({
    "Desenvolvedor Principal",
    "TITIO RAUZITO"
})

Tab1:AddParagraph({
    "Projeto",
    "Spectra Hub"
})

--==============================
-- REDES SOCIAIS
--==============================
Tab1:AddSection({"Redes Sociais"})

Tab1:AddButton({
    Name = "CANAL GTX MODS",
    Callback = function()
        if setclipboard then
            setclipboard("@assure_tv_157")
            setclipboard("https://youtube.com/@gtxteam_psicopata?si=2C5z2ibRqo50LqLM")
        end
    end
})

Tab1:AddButton({
    Name = "CANAL GT_MINGUI",
    Callback = function()
        if setclipboard then
            setclipboard("assure_TV")
            setclipboard("https://youtube.com/@gtvzmodded-7")
        end
    end
})


--// PLAYER TAB
local PlayerTab = Window:MakeTab({ Title = "Player", Icon = "rbxassetid://17132521951" })
PlayerTab:AddSection({ "Movement" })




PlayerTab:AddSlider({
    Name = "WalkSpeed",
    Min = 16,
    Max = 500,
    Default = humanoid.WalkSpeed,
    Callback = function(v) humanoid.WalkSpeed = v end
})

PlayerTab:AddSlider({
    Name = "JumpPower",
    Min = 50,
    Max = 500,
    Default = humanoid.JumpPower,
    Callback = function(v) humanoid.JumpPower = v end
})

PlayerTab:AddSlider({
    Name = "Gravity",
    Min = 10,
    Max = 500,
    Default = Workspace.Gravity,
    Callback = function(v) Workspace.Gravity = v end
})

PlayerTab:AddButton({
    Name = "Reset Player Stats",
    Callback = function()
        humanoid.WalkSpeed = 16
        humanoid.JumpPower = 50
        Workspace.Gravity = 196.2
    end
})



--// SPIN
PlayerTab:AddSection({ "Spin" })
local spinning, spinSpeed = false, 50

PlayerTab:AddToggle({
    Name = "Spin On/Off",
    Default = false,
    Callback = function(v) spinning = v end
})

PlayerTab:AddSlider({
    Name = "Spin Speed",
    Min = 1,
    Max = 1000,
    Default = spinSpeed,
    Callback = function(v) spinSpeed = v end
})

RunService.RenderStepped:Connect(function(dt)
    if spinning and humanoid and humanoid.RootPart then
        humanoid.RootPart.CFrame *= CFrame.Angles(0, math.rad(spinSpeed * dt), 0)
    end
end)

--// NOCLIP
local NoclipEnabled = false

PlayerTab:AddToggle({
    Name = "Noclip",
    Default = false,
    Callback = function(state)
        NoclipEnabled = state
    end
})

RunService.Stepped:Connect(function()
    if NoclipEnabled and plr.Character then
        for _, part in ipairs(plr.Character:GetDescendants()) do
            if part:IsA("BasePart") then
                part.CanCollide = false
            end
        end
    end
end)


--// INFINITE JUMP
local InfiniteJumpEnabled = false

PlayerTab:AddToggle({
    Name = "Infinite Jump",
    Default = false,
    Callback = function(state)
        InfiniteJumpEnabled = state
    end
})

game:GetService("UserInputService").JumpRequest:Connect(function()
    if InfiniteJumpEnabled and humanoid then
        humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
    end
end)

game:GetService("UserInputService").JumpRequest:Connect(function()
    if InfiniteJumpEnabled and humanoid then
        humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
    end
end)



--////////////////////////////////////////////////////
--// SCRIPTS
PlayerTab:AddSection({ "Scripts" })

PlayerTab:AddButton({
    Name = "Emotes",
    Callback = function()
        loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-7yd7-I-Emote-Script-48024"))()
    end
})

PlayerTab:AddButton({
    Name = "Fly",
    Callback = function()
        loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Gui-Fly-v3-37111"))()
    end
})

PlayerTab:AddButton({
    Name = "Sigma Spy",
    Callback = function()
        loadstring(game:HttpGet("https://github.com/exxtremestuffs/SimpleSpySource/raw/master/SimpleSpy.lua"))()
    end
})


PlayerTab:AddButton({
    Name = "click teleport",
    Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/err0r129/KptHadesBlair/main/Bao.lua"))()
    end
})




--////////////////////////////////////////////////////
--// ANTI-SIT
PlayerTab:AddSection({ "Anti-Sit" })

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer

local antiSitEnabled = false
local antiSitConn

PlayerTab:AddToggle({
    Name = "Anti-Sit",
    Default = false,
    Callback = function(state)
        antiSitEnabled = state

        local function apply(character)
            local hum = character:FindFirstChildOfClass("Humanoid")
            if not hum then return end

            hum.Sit = false
            hum:SetStateEnabled(Enum.HumanoidStateType.Seated, false)

            if antiSitConn then
                antiSitConn:Disconnect()
            end

            antiSitConn = hum.Seated:Connect(function(sit)
                if sit then
                    hum.Sit = false
                    hum:ChangeState(Enum.HumanoidStateType.GettingUp)
                end
            end)
        end

        if state then
            if LocalPlayer.Character then
                apply(LocalPlayer.Character)
            end

            LocalPlayer.CharacterAdded:Connect(function(char)
                if antiSitEnabled then
                    apply(char)
                end
            end)
        else
            if antiSitConn then
                antiSitConn:Disconnect()
                antiSitConn = nil
            end

            if LocalPlayer.Character then
                local hum = LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
                if hum then
                    hum:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
                end
            end
        end
    end
})

--////////////////////////////////////////////////////
--// ESP COMPLETO
PlayerTab:AddSection({ "ESP" })

local ESPEnabled = false
local ESPColorMode = "RGB"
local ESPObjects = {}
local ESPConnections = {}

PlayerTab:AddDropdown({
    Name = "ESP Color",
    Default = "RGB",
    Options = {
        "RGB","Branco","Preto","Vermelho",
        "Verde","Azul","Amarelo","Rosa","Roxo"
    },
    Callback = function(v)
        ESPColorMode = v
    end
})

local function getESPColor()
    if ESPColorMode == "RGB" then
        return Color3.fromHSV((tick()%5)/5,1,1)
    elseif ESPColorMode == "Branco" then
        return Color3.fromRGB(255,255,255)
    elseif ESPColorMode == "Preto" then
        return Color3.fromRGB(0,0,0)
    elseif ESPColorMode == "Vermelho" then
        return Color3.fromRGB(255,0,0)
    elseif ESPColorMode == "Verde" then
        return Color3.fromRGB(0,255,0)
    elseif ESPColorMode == "Azul" then
        return Color3.fromRGB(0,170,255)
    elseif ESPColorMode == "Amarelo" then
        return Color3.fromRGB(255,255,0)
    elseif ESPColorMode == "Rosa" then
        return Color3.fromRGB(255,105,180)
    elseif ESPColorMode == "Roxo" then
        return Color3.fromRGB(128,0,128)
    end
    return Color3.new(1,1,1)
end

local function RemoveESP(player)
    if ESPObjects[player] then
        ESPObjects[player]:Destroy()
        ESPObjects[player] = nil
    end
end

local function CreateESP(player)
    if player == LocalPlayer then return end
    if not ESPEnabled then return end
    if not player.Character then return end

    local head = player.Character:FindFirstChild("Head")
    if not head then return end

    RemoveESP(player)

    local gui = Instance.new("BillboardGui")
    gui.Name = "ESP"
    gui.Size = UDim2.new(0,220,0,45)
    gui.StudsOffset = Vector3.new(0,3,0)
    gui.AlwaysOnTop = true
    gui.Adornee = head
    gui.Parent = head

    local txt = Instance.new("TextLabel")
    txt.Size = UDim2.new(1,0,1,0)
    txt.BackgroundTransparency = 1
    txt.TextStrokeTransparency = 0.4
    txt.Font = Enum.Font.SourceSansBold
    txt.TextSize = 14
    txt.Text = player.Name.." | "..player.AccountAge.." dias"
    txt.TextColor3 = getESPColor()
    txt.Parent = gui

    ESPObjects[player] = gui
end

PlayerTab:AddToggle({
    Name = "ESP On/Off",
    Default = false,
    Callback = function(state)
        ESPEnabled = state

        if state then
            for _,p in ipairs(Players:GetPlayers()) do
                CreateESP(p)
            end

            table.insert(ESPConnections, Players.PlayerAdded:Connect(function(p)
                p.CharacterAdded:Connect(function()
                    task.wait(0.4)
                    CreateESP(p)
                end)
            end))

            table.insert(ESPConnections, Players.PlayerRemoving:Connect(function(p)
                RemoveESP(p)
            end))

            table.insert(ESPConnections, RunService.RenderStepped:Connect(function()
                if ESPColorMode == "RGB" then
                    for _,gui in pairs(ESPObjects) do
                        local txt = gui:FindFirstChildOfClass("TextLabel")
                        if txt then
                            txt.TextColor3 = getESPColor()
                        end
                    end
                end
            end))
        else
            for _,gui in pairs(ESPObjects) do
                gui:Destroy()
            end
            ESPObjects = {}

            for _,c in pairs(ESPConnections) do
                c:Disconnect()
            end
            ESPConnections = {}
        end
    end
})



local TrollTab = Window:MakeTab({
    Title = "Troll",
    Icon = "rbxassetid://6862780932"
})

TrollTab:AddSection({ Name = "Kill Troll" })

--==============================
-- VARIÁVEIS
--==============================
local selectedPlayer
local killEnabled = false

local teleportThread
local noclipThread
local monitorThread
local jumpThread
local respawnConn

--==============================
-- SOFÁ
--==============================
local function hasCouch()
    local char = plr.Character
    local bp = plr:FindFirstChildOfClass("Backpack")
    if char and char:FindFirstChild("Couch") then return true end
    if bp and bp:FindFirstChild("Couch") then return true end
    return false
end

local function pickCouch()
    pcall(function()
        ReplicatedStorage.RE:FindFirstChild("1Too1l")
            :InvokeServer("PickingTools", "Couch")
    end)
end

local function equipCouch()
    local char = plr.Character
    local hum = char and char:FindFirstChildOfClass("Humanoid")
    if not hum then return end

    local tool =
        (char and char:FindFirstChild("Couch")) or
        (plr.Backpack and plr.Backpack:FindFirstChild("Couch"))

    if tool then
        hum:EquipTool(tool)
    end
end

--==============================
-- PLAYER LIST
--==============================
local function getPlayers()
    local t = {}
    for _, p in ipairs(Players:GetPlayers()) do
        if p ~= plr then
            table.insert(t, p.Name)
        end
    end
    return t
end

local dropdown = TrollTab:AddDropdown({
    Name = "Escolher Player",
    Options = getPlayers(),
    Callback = function(v)
        selectedPlayer = v
    end
})

TrollTab:AddButton({
    Name = "Atualizar Lista",
    Callback = function()
        dropdown:Set(getPlayers())
    end
})

--==============================
-- TOGGLE KILL DEMORADO E CHATO
--==============================
TrollTab:AddToggle({
    Name = "Kill demorado e chato 😈",
    Default = false,
    Callback = function(state)
        killEnabled = state

        -- DESLIGAR TUDO
        if not state then
            if teleportThread then task.cancel(teleportThread) teleportThread = nil end
            if noclipThread then task.cancel(noclipThread) noclipThread = nil end
            if monitorThread then task.cancel(monitorThread) monitorThread = nil end
            if jumpThread then task.cancel(jumpThread) jumpThread = nil end
            if respawnConn then respawnConn:Disconnect() respawnConn = nil end
            return
        end

        if not selectedPlayer then return end

        -- MONITORAR SOFÁ (pegar automaticamente)
        monitorThread = task.spawn(function()
            while killEnabled do
                if not hasCouch() then
                    pickCouch()
                    task.wait(0.15)
                end
                equipCouch()
                task.wait(0.2)
            end
        end)

        -- AO MORRER
        respawnConn = plr.CharacterAdded:Connect(function()
            if killEnabled then
                task.wait(0.3)
                pickCouch()
            end
        end)

        -- TELEPORT CAÓTICO (NÁRNIA MODE 🌌)
        teleportThread = task.spawn(function()
            while killEnabled do
                local target = Players:FindFirstChild(selectedPlayer)
                local hrp = plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")
                local thrp = target and target.Character and target.Character:FindFirstChild("HumanoidRootPart")

                if hrp and thrp then
                    for i = 1, 60 do
                        if not killEnabled then break end
                        local dir = Vector3.new(
                            math.random(-100,100)/100*0.001, -- distância mínima de 1mm
                            math.random(-100,100)/100*0.001,
                            math.random(-100,100)/100*0.001
                        )
                        hrp.CFrame = CFrame.lookAt(thrp.Position + dir, thrp.Position)
                    end
                end
                task.wait(0.001)
            end
        end)

        -- NOCLIP FORTE
        noclipThread = task.spawn(function()
            while killEnabled do
                local char = plr.Character
                if char then
                    for _, p in ipairs(char:GetDescendants()) do
                        if p:IsA("BasePart") then
                            p.CanCollide = false
                        end
                    end
                end
                task.wait()
            end
        end)

        -- 🔥 PULO INFINITO (PC, Mobile, Tablet)
        jumpThread = task.spawn(function()
            while killEnabled do
                local char = plr.Character
                local hum = char and char:FindFirstChildOfClass("Humanoid")
                if hum then
                    hum.Jump = true
                    -- Dispara Input para todos os dispositivos
                    pcall(function()
                        UserInputService:InputBegan({UserInputType = Enum.UserInputType.Keyboard, KeyCode = Enum.KeyCode.Space}, false)
                        UserInputService:InputBegan({UserInputType = Enum.UserInputType.Touch}, false)
                    end)
                end
                task.wait(0.15)
            end
        end)
    end
})


--==============================
-- SLIDER TELEPORTE INFINITO
--==============================
TrollTab:AddSlider({
    Name = "Velocidade Teleporte Infinito",
    Min = 1,
    Max = 100,
    Default = 5,
    Increment = 1,
    Callback = function(v)
        tpSpeed = v
    end
})

--==============================
-- TOGGLE TELEPORTE INFINITO
--==============================
TrollTab:AddToggle({
    Name = "Teleportar Infinito (On / Off)",
    Default = false,
    Callback = function(state)
        tpEnabled = state

        if tpConnection then
            tpConnection:Disconnect()
            tpConnection = nil
        end

        if not state then return end

        tpConnection = RunService.Heartbeat:Connect(function(dt)
            if not tpEnabled or not selectedPlayer then return end

            local target = Players:FindFirstChild(selectedPlayer)
            if not target or not target.Character then return end

            local thrp = target.Character:FindFirstChild("HumanoidRootPart")
            local char = plr.Character
            local hrp = char and char:FindFirstChild("HumanoidRootPart")

            if not (thrp and hrp) then return end

            -- teleporta literalmente DENTRO do jogador
            hrp.CFrame = thrp.CFrame

            task.wait(1 / math.clamp(tpSpeed, 1, 100))
        end)
    end
})

--==============================
-- BOTÃO TELEPORTE ÚNICO
--==============================
TrollTab:AddButton({
    Name = "Teleportar Uma Vez",
    Callback = function()
        if not selectedPlayer then return end

        local target = Players:FindFirstChild(selectedPlayer)
        if not target or not target.Character then return end

        local thrp = target.Character:FindFirstChild("HumanoidRootPart")
        local hrp = plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")

        if thrp and hrp then
            hrp.CFrame = thrp.CFrame
        end
    end
})

--==============================
-- VISUALIZAR JOGADOR
--==============================
TrollTab:AddToggle({
    Name = "Visualizar Jogador",
    Default = false,
    Callback = function(state)
        viewing = state

        local cam = workspace.CurrentCamera
        local target = selectedPlayer and Players:FindFirstChild(selectedPlayer)

        if state and target and target.Character then
            local hum = target.Character:FindFirstChildOfClass("Humanoid")
            if hum then
                cam.CameraSubject = hum
                cam.CameraType = Enum.CameraType.Custom
            end
        else
            local myHum = plr.Character and plr.Character:FindFirstChildOfClass("Humanoid")
            if myHum then
                cam.CameraSubject = myHum
                cam.CameraType = Enum.CameraType.Custom
            end
        end
    end
})






--// SLIDER VELOCIDADE (só velocidade)
TrollTab:AddSlider({
    Name = "velocidade de frente e trás +18",
    Min = 1,
    Max = 100,
    Default = 5,
    Increment = 1,
    Callback = function(v)
        moveSpeed = v
    end
})

--// TOGGLE PRINCIPAL
TrollTab:AddToggle({
    Name = "Teleport Troll (On / Off)",
    Default = false,
    Callback = function(state)
        enabled = state

        if connection then
            connection:Disconnect()
            connection = nil
        end

        if not state or not selectedPlayer then return end

        timeOffset = 0

        connection = RunService.Heartbeat:Connect(function(dt)
            if not enabled then return end

            local target = Players:FindFirstChild(selectedPlayer)
            if not target or not target.Character then return end

            local thrp = target.Character:FindFirstChild("HumanoidRootPart")
            local char = plr.Character
            local hrp = char and char:FindFirstChild("HumanoidRootPart")

            if not (thrp and hrp) then return end

            -- TEMPO (slider atua aqui)
            timeOffset += dt * (moveSpeed * 0.3)

            -- FRENTE ↔ TRÁS
            local baseDistance = 4.5      -- mais perto do jogador
            local oscillation = math.sin(timeOffset) * 3

            -- CIMA ↕ BAIXO (bem leve)
            local verticalOffset = math.sin(timeOffset * 2) * 0.6

            -- POSIÇÃO FINAL
            local targetPos =
                thrp.Position
                - thrp.CFrame.LookVector * (baseDistance + oscillation)
                + Vector3.new(0, verticalOffset, 0)

            -- TREMIDA VISUAL
            local shake = Vector3.new(
                math.random(-10,10) / 70,
                math.random(-10,10) / 70,
                0
            )

            -- APLICAR TELEPORTE
            hrp.CFrame = CFrame.lookAt(
                targetPos + shake,
                thrp.Position
            )
        end)
    end
})






--==============================
-- SLIDER VELOCIDADE
--==============================
TrollTab:AddSlider({
    Name = "Velocidade do gogogogo",
    Min = 1,
    Max = 100,
    Default = 10,
    Increment = 1,
    Callback = function(v)
        speed = v
    end
})

--==============================
-- TOGGLE
--==============================
TrollTab:AddToggle({
    Name = "gogogogo no player +18",
    Default = false,
    Callback = function(state)
        enabled = state

        if connection then
            connection:Disconnect()
            connection = nil
        end

        if not state or not selectedPlayer then return end

        timeValue = 0

        connection = RunService.Heartbeat:Connect(function(dt)
            if not enabled then return end

            local target = Players:FindFirstChild(selectedPlayer)
            if not target or not target.Character then return end

            local tChar = target.Character
            local tRoot = tChar:FindFirstChild("HumanoidRootPart")
            local tHead = tChar:FindFirstChild("Head")

            local char = plr.Character
            local hrp = char and char:FindFirstChild("HumanoidRootPart")

            if not (tRoot and tHead and hrp) then return end

            -- ALTURA BASEADA NA SUA CINTURA
            local myHipHeight = hrp.Size.Y * 0.5

            -- ALTURA FINAL (BOCA + UM POUCO PRA CIMA)
            local heightOffset = Vector3.new(0, tHead.Size.Y * 0.4 + myHipHeight * 0.15, 0)

            -- CONTROLE REAL DE VAI ↔ VOLTA
            timeValue += dt * speed
            local backAndForth = math.sin(timeValue) * 2.5

            -- POSIÇÃO NA FRENTE DO JOGADOR
            local finalPosition =
                tRoot.Position
                + tRoot.CFrame.LookVector * (3 + backAndForth)
                + heightOffset

            -- APLICAR
            hrp.CFrame = CFrame.lookAt(finalPosition, tHead.Position)
        end)
    end
})


--// ===============================
--// ABA SKINS - COPY AVATAR REAL
--// ===============================

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Remotes = ReplicatedStorage:WaitForChild("Remotes")
local plr = Players.LocalPlayer

-- CRIAR ABA
local SkinsTab = Window:MakeTab({
    Title = "Skins",
    Icon = "rbxassetid://15726694719"
})

SkinsTab:AddSection({ "Copy Outfit / Avatar" })

-- ===============================
-- DROPDOWN (MESMO SISTEMA DO TROLL)
-- ===============================

local selectedSkinPlayer = nil
local skinDropdown

local function getPlayersSkins()
    local t = {}
    for _, p in ipairs(Players:GetPlayers()) do
        if p ~= plr then
            table.insert(t, p.Name)
        end
    end
    return t
end

skinDropdown = SkinsTab:AddDropdown({
    Name = "Escolher Player",
    Options = {},
    Callback = function(v)
        selectedSkinPlayer = v
    end
})

local function refreshSkinDropdown()
    local players = getPlayersSkins()
    skinDropdown:Set(players)

    if selectedSkinPlayer and not Players:FindFirstChild(selectedSkinPlayer) then
        selectedSkinPlayer = nil
        skinDropdown:Set("")
    end
end

refreshSkinDropdown()

SkinsTab:AddButton({
    Name = "Atualizar Lista",
    Callback = refreshSkinDropdown
})

-- ===============================
-- BOTÃO COPY AVATAR (IGUAL AO SCRIPT ORIGINAL)
-- ===============================

SkinsTab:AddButton({
    Name = "Copiar Avatar",
    Callback = function()
        if not selectedSkinPlayer then return end

        local LP = Players.LocalPlayer
        local LChar = LP.Character
        local TPlayer = Players:FindFirstChild(selectedSkinPlayer)

        if not (LChar and TPlayer and TPlayer.Character) then return end

        local LHumanoid = LChar:FindFirstChildOfClass("Humanoid")
        local THumanoid = TPlayer.Character:FindFirstChildOfClass("Humanoid")
        if not (LHumanoid and THumanoid) then return end

        -- ==================================
        -- RESET TOTAL DO LOCALPLAYER
        -- ==================================
        local LDesc = LHumanoid:GetAppliedDescription()

        -- REMOVER ACESSÓRIOS
        for _, acc in ipairs(LDesc:GetAccessories(true)) do
            if acc.AssetId and tonumber(acc.AssetId) then
                Remotes.Wear:InvokeServer(tonumber(acc.AssetId))
                task.wait(0.2)
            end
        end

        -- REMOVER ROUPAS
        if tonumber(LDesc.Shirt) then
            Remotes.Wear:InvokeServer(tonumber(LDesc.Shirt))
            task.wait(0.2)
        end

        if tonumber(LDesc.Pants) then
            Remotes.Wear:InvokeServer(tonumber(LDesc.Pants))
            task.wait(0.2)
        end

        -- REMOVER FACE
        if tonumber(LDesc.Face) then
            Remotes.Wear:InvokeServer(tonumber(LDesc.Face))
            task.wait(0.2)
        end

        -- ==================================
        -- COPIAR DO PLAYER ALVO
        -- ==================================
        local PDesc = THumanoid:GetAppliedDescription()

        -- PARTES DO CORPO (FORMATO EXATO)
        local argsBody = {
            [1] = {
                [1] = PDesc.Torso,
                [2] = PDesc.RightArm,
                [3] = PDesc.LeftArm,
                [4] = PDesc.RightLeg,
                [5] = PDesc.LeftLeg,
                [6] = PDesc.Head
            }
        }
        Remotes.ChangeCharacterBody:InvokeServer(unpack(argsBody))
        task.wait(0.5)

        -- ROUPAS
        if tonumber(PDesc.Shirt) then
            Remotes.Wear:InvokeServer(tonumber(PDesc.Shirt))
            task.wait(0.3)
        end

        if tonumber(PDesc.Pants) then
            Remotes.Wear:InvokeServer(tonumber(PDesc.Pants))
            task.wait(0.3)
        end

        -- FACE
        if tonumber(PDesc.Face) then
            Remotes.Wear:InvokeServer(tonumber(PDesc.Face))
            task.wait(0.3)
        end

        -- ACESSÓRIOS
        for _, v in ipairs(PDesc:GetAccessories(true)) do
            if v.AssetId and tonumber(v.AssetId) then
                Remotes.Wear:InvokeServer(tonumber(v.AssetId))
                task.wait(0.3)
            end
        end

        -- COR DO CORPO
        local SkinColor = TPlayer.Character:FindFirstChild("Body Colors")
        if SkinColor then
            Remotes.ChangeBodyColor:FireServer(tostring(SkinColor.HeadColor))
            task.wait(0.3)
        end

        -- ANIMAÇÃO IDLE
        if tonumber(PDesc.IdleAnimation) then
            Remotes.Wear:InvokeServer(tonumber(PDesc.IdleAnimation))
            task.wait(0.3)
        end
    end
})


--// ===============================
--// SKINS RÁPIDAS
--// ===============================

SkinsTab:AddSection({ "Skins Rápidas" })

local WearRemote = Remotes.Wear

local function addSkinButton(name, id)
    SkinsTab:AddButton({
        Name = name,
        Callback = function()
            WearRemote:InvokeServer(id)
        end
    })
end

-- INDIVIDUAIS
addSkinButton("Sem Cabeça", 134082579)
addSkinButton("Sem Perna 1", 115656762149031)
addSkinButton("Sem Perna 2", 93177286821086)
addSkinButton("Fada 1", 226189871)
addSkinButton("Fada 2", 150381051)
addSkinButton("Fada 3", 141742418)
addSkinButton("Fada 4", 128217885)
addSkinButton("Asa de Anjo", 192557913)
addSkinButton("Abóbora", 132809431)
addSkinButton("Chapéu", 305888394)
addSkinButton("Pombo", 134936622364544)
addSkinButton("Pé Gigante 1", 140311311736304)
addSkinButton("Pé Gigante 2", 94880807456770)
addSkinButton("Unhas Grandes", 135726095366567)
addSkinButton("Mãos Grandes", 12725518393)

-- PACK BLACK DOCTOR
SkinsTab:AddButton({
    Name = "Black Doctor",
    Callback = function()
        local ids = {
            134917317332597, 76104684961073, 113280776217715,
            12134501285, 88423188570127, 94604639662776,
            134022922877138, 100316015179747, 11743311601,
            80195816516327, 2510235063
        }
        for _, id in ipairs(ids) do
            WearRemote:InvokeServer(id)
            task.wait(0.15)
        end
    end
})

-- PACK GONER
SkinsTab:AddButton({
    Name = "Goner",
    Callback = function()
        local ids = {
            11274394350, 17822749561, 17812417356,
            17812415139, 17771175724, 17822722698,
            17772174303, 17770317484, 892268340,
            892267099, 2510236649
        }
        for _, id in ipairs(ids) do
            WearRemote:InvokeServer(id)
            task.wait(0.15)
        end
    end
})



--// ABA LIMITADOS
local LimitedTab = Window:MakeTab({
    Title = "Limitados",
    Icon = "rbxassetid://16181381646"
})

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local plr = Players.LocalPlayer

-- Adicionar seção visual
LimitedTab:AddSection({ "Ferramentas Limitadas" })

-- Lista de ferramentas
local tools = {
    "EggLauncher",
    "Cannon",
    "Glider",
    "UraniumRod",
    "Water Balloon",
    "FireHose",
    "Chainsaw",
    "Present",
    "CookieWindowTray",
    "SnowflakeGlider",
    "Couch" -- novo botão adicionado
}

-- Função para criar botão que dispara evento
local function createToolButton(toolName)
    LimitedTab:AddButton({
        Name = toolName,
        Callback = function()
            local args = {
                [1] = "AcceptedToolToServer",
                [2] = toolName,
                [3] = plr
            }
            local event = ReplicatedStorage:WaitForChild("RE"):WaitForChild("1Playe1rTrigge1rEven1t")
            if event then
                event:FireServer(unpack(args))
            end
        end
    })
end

-- Criar botões individuais
for _, toolName in ipairs(tools) do
    createToolButton(toolName)
end

-- Botão "Itens ALL" que dispara todos de uma vez
LimitedTab:AddButton({
    Name = "Itens ALL",
    Callback = function()
        local event = ReplicatedStorage:WaitForChild("RE"):WaitForChild("1Playe1rTrigge1rEven1t")
        if event then
            for _, toolName in ipairs(tools) do
                local args = {
                    [1] = "AcceptedToolToServer",
                    [2] = toolName,
                    [3] = plr
                }
                event:FireServer(unpack(args))
            end
        end
    end
})

--// ===============================
--// ABA RGB (NOME + BIO)
--// ===============================

local RGBTab = Window:MakeTab({
    Name = "RGB",
    Icon = "rbxassetid://122803943043720"
})

-- Remote
local RPColorRemote = game:GetService("ReplicatedStorage")
    :WaitForChild("RE")
    :WaitForChild("1RPNam1eColo1r")

-- Controle
local RGBEnabled = false
local RGBSpeed = 0.5 -- padrão

-- Lista de cores (organizada, sem repetição desnecessária)
local RGBColors = {
    Color3.new(1, 0, 0.0167),
    Color3.new(1, 0, 0.2720),
    Color3.new(1, 0, 0.4329),
    Color3.new(1, 0, 0.5769),
    Color3.new(1, 0, 0.6901),

    Color3.new(0.97, 0, 1),
    Color3.new(0.90, 0.03, 1),
    Color3.new(0.69, 0.07, 1),
    Color3.new(0.58, 0.03, 1),
    Color3.new(0.44, 0.02, 1),
    Color3.new(0.27, 0.02, 1),

    Color3.new(0, 0.19, 1),
    Color3.new(0, 0.37, 1),
    Color3.new(0, 0.70, 1),
    Color3.new(0.04, 0.89, 1),

    Color3.new(0.13, 1, 0.88),
    Color3.new(0.11, 1, 0.67),
    Color3.new(0.07, 1, 0.47),
    Color3.new(0.12, 1, 0.33),
    Color3.new(0.06, 1, 0.18),

    Color3.new(0.30, 1, 0),
    Color3.new(0.46, 1, 0.10),
    Color3.new(0.63, 1, 0.05),
    Color3.new(0.78, 1, 0.06),
    Color3.new(0.97, 1, 0),

    Color3.new(1, 0.89, 0),
    Color3.new(1, 0.79, 0),
    Color3.new(1, 0.68, 0),
    Color3.new(1, 0.50, 0),
    Color3.new(1, 0.39, 0),
    Color3.new(1, 0.24, 0),

    Color3.new(1, 0.15, 0.08),
    Color3.new(1, 0.02, 0.04)
}

-- Loop RGB
local function StartRGB()
    task.spawn(function()
        while RGBEnabled do
            for _, color in ipairs(RGBColors) do
                if not RGBEnabled then break end

                pcall(function()
                    -- Nome
                    RPColorRemote:FireServer(
                        "PickingRPNameColor",
                        color
                    )
                    -- Bio
                    RPColorRemote:FireServer(
                        "PickingRPBioColor",
                        color
                    )
                end)

                task.wait(RGBSpeed)
            end
        end
    end)
end

-- Toggle ON / OFF
RGBTab:AddToggle({
    Name = "RGB Nome + Bio",
    Default = false,
    Callback = function(state)
        RGBEnabled = state
        if state then
            StartRGB()
        end
    end
})

-- Slider de Velocidade
RGBTab:AddSlider({
    Name = "Velocidade RGB",
    Min = 1,
    Max = 100,
    Default = 50,
    Callback = function(value)
        -- 1 = lento | 100 = rápido
        RGBSpeed = math.clamp(1 / value, 0.01, 1)
    end
})


--// RP NAME + BIO TYPE & DELETE (SEM BUG DE SPEED)

local RPTextRemote = game:GetService("ReplicatedStorage")
    :WaitForChild("RE")
    :WaitForChild("1RPNam1eTex1t")

local RPNameText = ""
local RPBioText = ""

local RPNameEnabled = false
local RPBioEnabled = false

local NameSpeed = 30
local BioSpeed = 30

local function getDelay(speed)
    speed = math.clamp(speed, 1, 60)
    return 0.02 + (60 - speed) * 0.003
end

-- ================= RP NAME =================

RGBTab:AddTextBox({
    Name = "RP Name Texto",
    Placeholder = "Digite o RP Name",
    Callback = function(v)
        RPNameText = v
    end
})

RGBTab:AddSlider({
    Name = "Velocidade RP Name",
    Min = 1,
    Max = 60,
    Default = 30,
    Callback = function(v)
        NameSpeed = v
    end
})

RGBTab:AddToggle({
    Name = "RP Name ON / OFF",
    Default = false,
    Callback = function(state)
        RPNameEnabled = state
        if not state or RPNameText == "" then return end

        task.spawn(function()
            while RPNameEnabled do
                -- ESCREVER
                for i = 1, #RPNameText do
                    if not RPNameEnabled then return end
                    RPTextRemote:FireServer(
                        "RolePlayName",
                        string.sub(RPNameText, 1, i)
                    )
                    task.wait(getDelay(NameSpeed))
                end

                task.wait(0.4)

                -- APAGAR (DE TRÁS PRA FRENTE)
                for i = #RPNameText - 1, 0, -1 do
                    if not RPNameEnabled then return end
                    RPTextRemote:FireServer(
                        "RolePlayName",
                        string.sub(RPNameText, 1, i)
                    )
                    task.wait(getDelay(NameSpeed))
                end

                task.wait(0.4)
            end
        end)
    end
})

-- ================= RP BIO =================

RGBTab:AddTextBox({
    Name = "RP Bio Texto",
    Placeholder = "Digite o RP Bio",
    Callback = function(v)
        RPBioText = v
    end
})

RGBTab:AddSlider({
    Name = "Velocidade RP Bio",
    Min = 1,
    Max = 60,
    Default = 30,
    Callback = function(v)
        BioSpeed = v
    end
})

RGBTab:AddToggle({
    Name = "RP Bio ON / OFF",
    Default = false,
    Callback = function(state)
        RPBioEnabled = state
        if not state or RPBioText == "" then return end

        task.spawn(function()
            while RPBioEnabled do
                -- ESCREVER
                for i = 1, #RPBioText do
                    if not RPBioEnabled then return end
                    RPTextRemote:FireServer(
                        "RolePlayBio",
                        string.sub(RPBioText, 1, i)
                    )
                    task.wait(getDelay(BioSpeed))
                end

                task.wait(0.4)

                -- APAGAR
                for i = #RPBioText - 1, 0, -1 do
                    if not RPBioEnabled then return end
                    RPTextRemote:FireServer(
                        "RolePlayBio",
                        string.sub(RPBioText, 1, i)
                    )
                    task.wait(getDelay(BioSpeed))
                end

                task.wait(0.4)
            end
        end)
    end
})


--// ABA CHAT
local ChatTab = Window:MakeTab({ Title = "Chat", Icon = "rbxassetid://92345592692449" })

--// SEÇÃO SPAM CHAT
ChatTab:AddSection({ Name = "Spam Chat" })

local TextSave = ""
local tcs = game:GetService("TextChatService")
local chat = tcs.ChatInputBarConfiguration and tcs.ChatInputBarConfiguration.TargetTextChannel

local function sendchat(msg)
    if not msg or msg == "" then return end
    if tcs.ChatVersion == Enum.ChatVersion.LegacyChatService then
        local success, err = pcall(function()
            game:GetService("ReplicatedStorage"):FindFirstChild("DefaultChatSystemChatEvents").SayMessageRequest:FireServer(msg, "All")
        end)
        if not success then warn(err) end
    elseif chat then
        local success, err = pcall(function()
            chat:SendAsync(msg)
        end)
        if not success then warn(err) end
    end
end

--// TEXTBOX PARA DIGITAR MENSAGEM
ChatTab:AddTextBox({
    Name = "Enter text",
    PlaceholderText = "Digite a mensagem",
    Callback = function(text)
        TextSave = text
    end
})

--// BOTÃO SEND CHAT
ChatTab:AddButton({
    Name = "Send Chat",
    Callback = function()
        sendchat(TextSave)
    end
})

--// SLIDER DE DELAY PARA SPAM
getgenv().ChaosHubSendDelay = 1
ChatTab:AddSlider({
    Name = "Spam Delay",
    Min = 0.4,
    Max = 10,
    Default = 1,
    Increment = 0.1,
    Callback = function(Value)
        getgenv().ChaosHubSendDelay = Value
    end
})

--// TOGGLE DE SPAM AUTOMÁTICO
getgenv().ChaosHubSpawnText = false
ChatTab:AddToggle({
    Name = "Spam Chat",
    Default = false,
    Callback = function(Value)
        getgenv().ChaosHubSpawnText = Value
        task.spawn(function()
            while getgenv().ChaosHubSpawnText do
                sendchat(TextSave)
                task.wait(getgenv().ChaosHubSendDelay)
            end
        end)
    end
})

--// BOTÃO SPAM HACKED
ChatTab:AddButton({
    Name = "Spam chat Hacked By Spectra",
    Callback = function()
        if tcs.ChatVersion == Enum.ChatVersion.TextChatService then 
            tcs.TextChannels.RBXGeneral:SendAsync("Server: Hacked by Spectra HUB")
        else 
            print("Nothing")
        end
    end
})

--// BOTÃO LIMPAR CHAT
ChatTab:AddButton({
    Name = "Clear Chat",
    Callback = function()
        if tcs.ChatVersion == Enum.ChatVersion.TextChatService then 
            tcs.TextChannels.RBXGeneral:SendAsync("Server: Chat Cleared")
        else 
            print("Nothing")
        end
    end
})


--==============================
-- ABA EVENTOS
--==============================
local EventosTab = Window:MakeTab({
    Title = "Eventos",
    Icon = "rbxassetid://4519515245"
})

EventosTab:AddSection({ Name = "Coletar Estrelas de Natal" })

local eventoEnabled = false
local teleportThreadEvento

-- Lista de localizações do evento (corrigida)
local localizacoes = {
    Vector3.new(174.7, 4.4, -172.7),
    Vector3.new(179.5, 9.5, -231.0),
    Vector3.new(350.9, 4.7, -409.6),
    Vector3.new(320.3, 4.7, -436.0),
    Vector3.new(263.5, 4.7, -435.8),
    Vector3.new(425.4, 4.8, -268.3),
    Vector3.new(367.4, 12.7, -251.0),
    Vector3.new(338.1, 11.3, -214.3),
    Vector3.new(333.5, 4.8, -150.9),
    Vector3.new(293.5, 4.3, -144.0),
    Vector3.new(244.3, 4.3, -172.9),
    Vector3.new(171.3, 53.3, -263.4),
    Vector3.new(442.7, 51.0, -368.5),
    Vector3.new(487.3, 69.4, -333.4),
    Vector3.new(121.17, 3.74, -117.83),
    Vector3.new(122.07, 3.02, -179.70),
    Vector3.new(125.72, 7.27, -241.51),
    Vector3.new(126.70, 6.33, -291.01),
    Vector3.new(135.30, 6.01, -336.68),
    Vector3.new(191.58, 5.90, -344.29),
    Vector3.new(258.76, 5.04, -336.52),
    Vector3.new(312.00, 7.85, -321.72),
    Vector3.new(362.28, 6.83, -334.05),
    Vector3.new(615.31, 142.10, -419.94),
    Vector3.new(351.4, 101.9, -168.1),
    Vector3.new(259.0, 11.3, -204.4),
    Vector3.new(171.1, 30.4, -278.7),
    Vector3.new(189.2, -11.1, -256.9),
    Vector3.new(349.8, 101.9, -168.9)
}

EventosTab:AddToggle({
    Name = "Evento de Natal",
    Default = false,
    Callback = function(state)
        eventoEnabled = state

        -- DESLIGAR
        if not state then
            if teleportThreadEvento then task.cancel(teleportThreadEvento) end
            return
        end

        -- Ligar loop de teleporte
        teleportThreadEvento = task.spawn(function()
            while eventoEnabled do
                local hrp = plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")
                if hrp then
                    for _, pos in ipairs(localizacoes) do
                        if not eventoEnabled then break end
                        hrp.CFrame = CFrame.new(pos)
                        task.wait(2) -- espera 2 segundos em cada posição
                    end
                end
                task.wait()
            end
        end)
    end
})

--==============================
-- BOTÕES DE TELEPORTE DIRETO
--==============================
local locaisTeleport = {
    ["Loja de Natal"] = Vector3.new(163.30, 4.31, -148.14),
    ["Monte Everest"] = Vector3.new(614.71, 138.72, -393.17),
    ["Em cima da Árvore de Natal"] = Vector3.new(356.16, 101.81, -172.04),
    ["Na frente do evento de Natal"] = Vector3.new(115.82, 4.93, -113.38),
    ["Festa de Natal"] = Vector3.new(306.78, -20.02, -337.43),
    ["Túnel de Natal"] = Vector3.new(124.52, -5.64, -163.93)
}

for nome, pos in pairs(locaisTeleport) do
    EventosTab:AddButton({
        Name = nome,
        Callback = function()
            local hrp = plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")
            if hrp then
                hrp.CFrame = CFrame.new(pos)
            end
        end
    })
end

--// CRIAR ABA PROTECTION
local ProtectionTab = Window:MakeTab({
    Title = "Protection",
    Icon = "rbxassetid://5197571732"
})

--// REFERÊNCIAS
local RunService = game:GetService("RunService")
local Players = game:GetService("Players")
local Workspace = game:GetService("Workspace")
local LocalPlayer = Players.LocalPlayer

--===============================
-- FUNÇÃO ANTI-FLING GENÉRICA
--===============================
function AntiFlingLoop(name, finder)
    return function(state)
        task.spawn(function()
            while state do
                local target = finder()
                if target then
                    for _, part in ipairs(target:GetDescendants()) do
                        if part:IsA("BasePart") then
                            part.CanCollide = true
                            part.Anchored = true
                        end
                    end
                end
                task.wait(0.5)
            end
        end)
    end
end

--===============================
-- TOGGLES INDIVIDUAIS
--===============================
ProtectionTab:AddToggle({Name = "Anti Fling Carros", Default = false, Callback = AntiFlingLoop("Vehicles", function() return Workspace:FindFirstChild("Vehicles") end)})
ProtectionTab:AddToggle({Name = "Anti Canoe Fling", Default = false, Callback = AntiFlingLoop("Canoes", function() local wc = Workspace:FindFirstChild("WorkspaceCom") return wc and wc:FindFirstChild("001_CanoeStorage") end)})
ProtectionTab:AddToggle({Name = "Anti Fling Jets", Default = false, Callback = AntiFlingLoop("Jets", function() local f = Workspace:FindFirstChild("WorkspaceCom") if f and f:FindFirstChild("001_Airport") then local s = f["001_Airport"]:FindFirstChild("AirportHanger") if s then return s:FindFirstChild("001_JetStorage") and s["001_JetStorage"]:FindFirstChild("JetAirport") end end end)})
ProtectionTab:AddToggle({Name = "Anti Fling Helicópteros", Default = false, Callback = AntiFlingLoop("Helis", function() local f = Workspace:FindFirstChild("WorkspaceCom") return f and f:FindFirstChild("001_HeliStorage") and f["001_HeliStorage"]:FindFirstChild("PoliceStationHeli") end)})
ProtectionTab:AddToggle({Name = "Anti Fling Ball", Default = false, Callback = AntiFlingLoop("Balls", function() local f = Workspace:FindFirstChild("WorkspaceCom") return f and f:FindFirstChild("001_SoccerBalls") end)})

--===============================
-- Anti Sit / Sofá / Grab
--===============================
local antiSitActive = false
ProtectionTab:AddToggle({
    Name = "Anti Sit / Grab / Sofá",
    Default = false,
    Callback = function(state)
        antiSitActive = state
        task.spawn(function()
            while antiSitActive and LocalPlayer.Character do
                local humanoid = LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
                if humanoid then
                    humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
                    if humanoid:GetState() == Enum.HumanoidStateType.Seated then
                        humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
                    end
                end
                task.wait(0.05)
            end
        end)
    end
})

--===============================
-- Anti Lag / Anti Tool
--===============================
ProtectionTab:AddToggle({
    Name = "Anti-Lag / Anti Tool",
    Default = false,
    Callback = function(state)
        if not state then return end
        task.spawn(function()
            local dedupLock = {}
            local function isTool(inst) return inst:IsA("Tool") end
            local function gather(player)
                local items = {}
                local containers = {}
                if player.Character then table.insert(containers, player.Character) end
                local backpack = player:FindFirstChildOfClass("Backpack")
                if backpack then table.insert(containers, backpack) end
                local sg = player:FindFirstChild("StarterGear")
                if sg then table.insert(containers, sg) end
                for _, container in ipairs(containers) do
                    for _, child in ipairs(container:GetChildren()) do
                        if isTool(child) then table.insert(items, child) end
                    end
                end
                return items
            end
            local function dedupe(player)
                if dedupLock[player] then return end
                dedupLock[player] = true
                local tools = gather(player)
                if #tools > 1 then
                    for i = 2, #tools do pcall(function() tools[i]:Destroy() end) end
                end
                dedupLock[player] = false
            end
            Players.PlayerAdded:Connect(function(plr) dedupe(plr) end)
            for _,plr in ipairs(Players:GetPlayers()) do dedupe(plr) end
            while state do
                for _,plr in ipairs(Players:GetPlayers()) do dedupe(plr) end
                task.wait(2)
            end
        end)
    end
})

--===============================
-- Anti Fling Portas
--===============================
ProtectionTab:AddToggle({
    Name = "Anti Fling Portas",
    Default = false,
    Callback = function(state)
        if not _G.hiddenDoors then _G.hiddenDoors = {} end
        if state then
            _G.hiddenDoors = {}
            for _, obj in ipairs(workspace:GetDescendants()) do
                if obj:IsA("BasePart") and obj.Name:lower():find("door") then
                    local doorData = {door=obj, originalTransparency=obj.Transparency, originalCanCollide=obj.CanCollide, originalCastShadow=obj.CastShadow}
                    obj.Transparency = 1
                    obj.CanCollide = false
                    obj.CastShadow = false
                    for _, child in ipairs(obj:GetChildren()) do
                        if child:IsA("BasePart") then child.Transparency = 1; child.CanCollide=false
                        elseif child:IsA("SurfaceGui") or child:IsA("BillboardGui") then child.Enabled = false end
                    end
                    table.insert(_G.hiddenDoors, doorData)
                end
            end
            print("⚡ " .. #_G.hiddenDoors .. " portas escondidas!")
        else
            for _, doorData in ipairs(_G.hiddenDoors or {}) do
                if doorData.door and doorData.door.Parent then
                    doorData.door.Transparency = doorData.originalTransparency
                    doorData.door.CanCollide = doorData.originalCanCollide
                    doorData.door.CastShadow = doorData.originalCastShadow
                    for _, child in ipairs(doorData.door:GetChildren()) do
                        if child:IsA("BasePart") then child.Transparency=0; child.CanCollide=true
                        elseif child:IsA("SurfaceGui") or child:IsA("BillboardGui") then child.Enabled = true end
                    end
                end
            end
            print("✔ " .. #(_G.hiddenDoors or {}) .. " portas restauradas!")
            _G.hiddenDoors = {}
        end
    end
})

--===============================
-- TOGGLE MASTER – PROTEÇÃO ALL
--===============================
ProtectionTab:AddToggle({
    Name = "🛡️ Proteção All",
    Default = false,
    Callback = function(state)
        for _,toggle in ipairs(ProtectionTab.Toggles) do
            if toggle.Name ~= "🛡️ Proteção All" then
                toggle:SetState(state)
            end
        end
    end
})

--===============================
-- TOGGLE ULTRA MAX / ANTI-KILL / ANTI-FALL
--===============================
local UltraEnabled = false
local Connections = {}
local lastSafeCFrame = nil
local lastCheck = tick()
local MAX_SPEED = 85
local MAX_FALL_SPEED = -120
local MAP_Y_LIMIT = -80

local function disconnectAll()
    for _,c in ipairs(Connections) do pcall(function() c:Disconnect() end) end
    table.clear(Connections)
end

local function getChar() return LocalPlayer.Character end
local function getHRP() local c=getChar() return c and c:FindFirstChild("HumanoidRootPart") end
local function getHum() local c=getChar() return c and c:FindFirstChildOfClass("Humanoid") end
local function restorePosition()
    local hrp = getHRP()
    if hrp and lastSafeCFrame then
        hrp.AssemblyLinearVelocity=Vector3.zero
        hrp.AssemblyAngularVelocity=Vector3.zero
        hrp.CFrame=lastSafeCFrame+Vector3.new(0,5,0)
    end
end

ProtectionTab:AddToggle({
    Name = "🛡️ Proteção Máxima ULTRA++",
    Default = false,
    Callback = function(state)
        UltraEnabled = state
        disconnectAll()
        if state then task.wait(0.4) end
        if not state then return end

        table.insert(Connections, RunService.Heartbeat:Connect(function()
            local hrp = getHRP()
            if hrp then lastSafeCFrame = hrp.CFrame end
        end))

        table.insert(Connections, RunService.Heartbeat:Connect(function()
            if not UltraEnabled then return end
            local char = getChar()
            local hrp = getHRP()
            local hum = getHum()
            if not (char and hrp and hum) then return end
            hum:SetStateEnabled(Enum.HumanoidStateType.Seated,false)
            if hum:GetState()==Enum.HumanoidStateType.Seated then hum:ChangeState(Enum.HumanoidStateType.GettingUp) end
            for _,p in ipairs(char:GetDescendants()) do if p:IsA("BasePart") then p.CanCollide=true; p.Anchored=false end end
            hrp.AssemblyAngularVelocity=Vector3.zero
            if hrp.AssemblyLinearVelocity.Magnitude>MAX_SPEED then restorePosition() end
            hrp.CustomPhysicalProperties=PhysicalProperties.new(0.01,0,0,0,0)
        end))

        table.insert(Connections, RunService.Heartbeat:Connect(function()
            if not UltraEnabled then return end
            local hrp=getHRP()
            if not hrp then return end
            local now=tick()
            if now-lastCheck<0.15 then return end
            lastCheck=now
            local vy=hrp.AssemblyLinearVelocity.Y
            if vy<MAX_FALL_SPEED or hrp.Position.Y<MAP_Y_LIMIT then restorePosition() end
        end))

        task.spawn(function()
            while UltraEnabled do
                for _,obj in ipairs(Workspace:GetDescendants()) do
                    if obj:IsA("BodyMover") or obj:IsA("VectorForce") or obj:IsA("AngularVelocity") or obj:IsA("LinearVelocity") then
                        pcall(function() obj:Destroy() end)
                    end
                end
                task.wait(2)
            end
        end)

        table.insert(Connections, LocalPlayer.CharacterAdded:Connect(function(char)
            task.wait(0.6)
            for _,v in ipairs(char:GetChildren()) do
                if v:IsA("Tool") then pcall(function() v:Destroy() end) end
            end
        end))
    end
})




--==================================================
--// LAG SERVER TAB
--==================================================
local Tab13 = Window:MakeTab({
    Title = "Lag Server",
    Icon = "rbxassetid://4483345998"
})

--==================================================
-- Shutdown Personalizado
--==================================================
local Section = Tab13:AddSection({ Name = "Shutdown Personalizado" })

-- Shutdown Normal
Tab13:AddButton({
    Name = "Shutdown Servidor",
    Callback = function()
        for m = 1, 495 do
            game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l")
                :InvokeServer("PickingTools", "FireHose")

            game.Players.LocalPlayer.Backpack.FireHose.ToolSound
                :FireServer("FireHose", "DestroyFireHose")
        end

        local hrp = game.Players.LocalPlayer.Character.HumanoidRootPart
        local oldcf = hrp.CFrame
        hrp.CFrame = CFrame.new(999999999.414, -475, 999999999.414)

        repeat task.wait() until not hrp.Parent
        game.Players.LocalPlayer.CharacterAdded:Wait()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = oldcf

        game:GetService("StarterGui"):SetCore("SendNotification", {
            Title = "Script de Dupe",
            Text = "Shutdown Concluído, Agora Vai Desligar",
            Duration = 5
        })

        task.wait(0.5)
        hrp.CFrame = CFrame.new(9999, -475, 9999)
    end
})

-- Shutdown Internet Error
Tab13:AddButton({
    Name = "Shutdown Servidor (Erro de Internet)",
    Callback = function()
        for m = 1, 535 do
            game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l")
                :InvokeServer("PickingTools", "FireHose")

            game.Players.LocalPlayer.Backpack.FireHose.ToolSound
                :FireServer("FireHose", "DestroyFireHose")
        end
    end
})

-- Shutdown Timeout Error
Tab13:AddButton({
    Name = "Shutdown Servidor (Erro de Conexão Expirada)",
    Callback = function()
        for m = 1, 635 do
            game:GetService("ReplicatedStorage").RE:FindFirstChild("1Too1l")
                :InvokeServer("PickingTools", "FireHose")

            game.Players.LocalPlayer.Backpack.FireHose.ToolSound
                :FireServer("FireHose", "DestroyFireHose")
        end
    end
})

--==================================================
-- Lag com Laptop
--==================================================
local Section = Tab13:AddSection({ Name = "Lag com Laptop" })
local toggles = { LagLaptop = false, LagPhone = false }

local function clickNormally(obj)
    local cd = obj:FindFirstChildWhichIsA("ClickDetector")
    if cd then fireclickdetector(cd) end
end

local function lagarJogoLaptop(laptop)
    while toggles.LagLaptop do
        if laptop then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = laptop.CFrame
            clickNormally(laptop)
        else
            warn("Laptop não encontrado.")
            break
        end
        task.wait(0.0001)
    end
end

Tab13:AddToggle({
    Name = "Lag com Laptop",
    Default = false,
    Callback = function(state)
        toggles.LagLaptop = state
        if state then
            local laptop = workspace.WorkspaceCom["001_GiveTools"]:FindFirstChild("Laptop")
            if laptop then
                task.spawn(function()
                    lagarJogoLaptop(laptop)
                end)
            else
                warn("Laptop não encontrado.")
            end
        else
            print("Lag com Laptop desativado.")
        end
    end
})

Tab13:AddParagraph({
    "Informação de Lag",
    "O efeito de lag começa após 35 segundos"
})

--==================================================
-- Lag com Telefone
--==================================================
local Section = Tab13:AddSection({ Name = "Lag com Telefone" })

local function lagarJogoPhone(phone)
    while toggles.LagPhone do
        if phone then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = phone.CFrame
            clickNormally(phone)
        else
            warn("Telefone não encontrado.")
            break
        end
        task.wait(0.01)
    end
end

Tab13:AddToggle({
    Name = "Lag com Telefone",
    Default = false,
    Callback = function(state)
        toggles.LagPhone = state
        if state then
            local phone =
                workspace.WorkspaceCom["001_CommercialStores"]
                .CommercialStorage1.Store.Tools:FindFirstChild("Iphone")

            if phone then
                task.spawn(function()
                    lagarJogoPhone(phone)
                end)
            else
                warn("Telefone não encontrado.")
            end
        else
            print("Lag com Telefone desativado.")
        end
    end
})

Tab13:AddParagraph({
    "Informação de Lag",
    "O script começa a causar lag após 35 segundos"
})

--==================================================
-- Lag com Bomba (COMPLETO)
--==================================================
local Section = Tab13:AddSection({ Name = "Lag com Bomba" })
local BombActive = false

Tab13:AddToggle({
    Name = "Lag com Bomba",
    Default = false,
    Callback = function(v)
        BombActive = v
        if not v then
            print("Lag com Bomba desativado.")
            return
        end

        local Player = game.Players.LocalPlayer
        local Char = Player.Character or Player.CharacterAdded:Wait()
        local HRP = Char:WaitForChild("HumanoidRootPart")
        local Bomb =
            workspace.WorkspaceCom["001_CriminalWeapons"].GiveTools:FindFirstChild("Bomb")

        if not Bomb then
            warn("Bomba não encontrada.")
            BombActive = false
            return
        end

        task.spawn(function()
            while BombActive do
                if Bomb:FindFirstChild("ClickDetector") then
                    HRP.CFrame = Bomb.CFrame
                    fireclickdetector(Bomb.ClickDetector)
                end
                task.wait(0.00001)
            end
        end)

        task.spawn(function()
            while BombActive do
                local VIM = game:GetService("VirtualInputManager")
                VIM:SendMouseButtonEvent(500, 500, 0, true, game, 0)
                task.wait(1.5)
                VIM:SendMouseButtonEvent(500, 500, 0, false, game, 0)

                game:GetService("ReplicatedStorage").RE["1Blo1wBomb1sServe1r"]
                    :FireServer("Bomb" .. Player.Name)

                task.wait(1.5)
            end
        end)
    end
})

Tab13:AddParagraph({
    "Informação de Lag",
    "O script começa a causar lag após 35 segundos"
})





--////////////////////////////////////////////////////
--// ADMIN TAB
local AdminTab = Window:MakeTab({
    Title = "Admin",
    Icon = "rbxassetid://7734053495"
})

AdminTab:AddSection({ "Comandos Admin" })

--==============================
-- PLAYER LIST
--==============================
local selectedAdminPlayer

local function getPlayers()
    local t = {}
    for _, p in ipairs(Players:GetPlayers()) do
        if p ~= plr then
            table.insert(t, p.Name)
        end
    end
    return t
end

local adminDropdown = AdminTab:AddDropdown({
    Name = "Escolher Player",
    Options = getPlayers(),
    Callback = function(v)
        selectedAdminPlayer = v
    end
})

AdminTab:AddButton({
    Name = "Atualizar Lista",
    Callback = function()
        adminDropdown:Set(getPlayers())
    end
})

--==============================
-- FUNÇÃO PARA ENVIAR COMANDO
--==============================
local TextChatService = game:GetService("TextChatService")
local function EnviarComando(comando, alvo)
    if not alvo then return end
    local canal =
        TextChatService.TextChannels:FindFirstChild("RBXGeneral")
        or TextChatService.TextChannels:GetChildren()[1]

    if canal then
        canal:SendAsync(";" .. comando .. " " .. alvo)
    end
end

--==============================
-- BOTÕES ADMIN
--==============================
local function criarBotao(nome, comando)
    AdminTab:AddButton({
        Name = nome,
        Callback = function()
            if not selectedAdminPlayer then
                warn("Nenhum jogador selecionado")
                return
            end
            EnviarComando(comando, selectedAdminPlayer)
        end
    })
end

criarBotao("Kill", "kill")
criarBotao("Fling", "fling")
criarBotao("Sit", "sit")
criarBotao("Frozen", "frozen")
criarBotao("UnFrozen", "unfrozen")
criarBotao("Spin", "spin")
criarBotao("UnSpin", "unspin")
criarBotao("Caixa", "caixa")
criarBotao("UnCaixa", "uncaixa")

--==============================
-- SISTEMA LOCAL
--==============================
local SpinPlayers = {}
local FrozenPlayers = {}
local CaixaPlayers = {}

local function KillLocal() local hum=plr.Character and plr.Character:FindFirstChildOfClass("Humanoid"); if hum then hum.Health=0 end end
local function FlingLocal() local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart"); if hrp then hrp.Velocity=Vector3.new(0,2000,0) end end
local function SitLocal() local hum=plr.Character and plr.Character:FindFirstChildOfClass("Humanoid"); if hum then hum.Sit=true end end
local function FrozenLocal() local hum=plr.Character and plr.Character:FindFirstChildOfClass("Humanoid"); if hum then hum.PlatformStand=true; FrozenPlayers[plr.Name]=true end end
local function UnFrozenLocal() local hum=plr.Character and plr.Character:FindFirstChildOfClass("Humanoid"); if hum then hum.PlatformStand=false; FrozenPlayers[plr.Name]=nil end end
local function SpinLocal() SpinPlayers[plr.Name]=true end
local function UnSpinLocal() SpinPlayers[plr.Name]=nil end
local function CaixaLocal()
    local char=plr.Character
    if char and not CaixaPlayers[plr.Name] then
        local hrp=char:FindFirstChild("HumanoidRootPart")
        if hrp then
            local caixa=Instance.new("Model")
            caixa.Name="CaixaAdmin"
            local size=Vector3.new(6,6,6)
            local pos=hrp.Position
            for x=-1,1 do for y=-1,1 do for z=-1,1 do
                if x==0 and y==0 and z==0 then continue end
                local p=Instance.new("Part")
                p.Size=size/3 p.Anchored=true p.CanCollide=true p.Color=Color3.new(0,0,0)
                p.Material=Enum.Material.Neon
                p.CFrame=CFrame.new(pos+Vector3.new(x*2,y*2,z*2))
                p.Parent=caixa
            end end end
            caixa.Parent=Workspace
            CaixaPlayers[plr.Name]=caixa
        end
    end
end
local function UnCaixaLocal() local c=CaixaPlayers[plr.Name]; if c then c:Destroy(); CaixaPlayers[plr.Name]=nil end end

--==============================
-- CHAT LISTENER
--==============================
local function OnMessageReceived(message)
    local text=string.lower(message.Text)
    local cmd, alvo = text:match("^;(.-)%s+(.+)$")
    if cmd and alvo and string.lower(alvo)==string.lower(plr.Name) then
        if cmd=="kill" then KillLocal()
        elseif cmd=="fling" then FlingLocal()
        elseif cmd=="sit" then SitLocal()
        elseif cmd=="frozen" then FrozenLocal()
        elseif cmd=="unfrozen" then UnFrozenLocal()
        elseif cmd=="spin" then SpinLocal()
        elseif cmd=="unspin" then UnSpinLocal()
        elseif cmd=="caixa" then CaixaLocal()
        elseif cmd=="uncaixa" then UnCaixaLocal() end
    end
end

for _, channel in pairs(TextChatService.TextChannels:GetChildren()) do
    channel.MessageReceived:Connect(OnMessageReceived)
end
TextChatService.TextChannels.ChildAdded:Connect(function(channel)
    channel.MessageReceived:Connect(OnMessageReceived)
end)

--==============================
-- SPIN LOOP + CAIXA TELEPORT
--==============================
RunService.RenderStepped:Connect(function(dt)
    for _,_ in pairs(SpinPlayers) do
        local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")
        if hrp then hrp.CFrame*=CFrame.Angles(0,math.rad(1000*dt),0) end
    end
    for _, caixa in pairs(CaixaPlayers) do
        local hrp=plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")
        if hrp and caixa then
            local inside=false
            for _, p in pairs(caixa:GetChildren()) do
                if p:IsA("BasePart") then
                    local s=p.Size/2 local pos=p.Position
                    local min=pos-s local max=pos+s
                    local pPos=hrp.Position
                    if pPos.X>min.X and pPos.X<max.X and pPos.Y>min.Y and pPos.Y<max.Y and pPos.Z>min.Z and pPos.Z<max.Z then
                        inside=true break
                    end
                end
            end
            if not inside then hrp.CFrame=CFrame.new(hrp.Position) end
        end
    end
end)
--// ServiÃ§os
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local TextChatService = game:GetService("TextChatService")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer
local Workspace = workspace


--// WHITELIST
local whitelist = {
    ["doxPkwsXLBt"] = true,
    ["ajudo_pessoas21"] = true,
    [""] = true
}

local player = game.Players.LocalPlayer

if not whitelist[player.Name] then
    player:Kick("Você não está autorizado a usar este script.")
    return
end

--// Jogadores autorizados por envio de Lcc_####
local Autorizados = {} -- chave: nome exato do player -> true

--// Estado local
local playerOriginalSpeed = {}
local jaulas = {}
local jailConnections = {}

--// FunÃ§Ã£o util: atualiza tag visual de um jogador (cria/recria)
local function createSpecialTag(player)
    if not player then return end
    local function apply()
        local char = player.Character
        if not char then return end
        local head = char:FindFirstChild("Head")
        if not head then return end

        local old = head:FindFirstChild("SpecialTag")
        if old then old:Destroy() end

        local gui = Instance.new("BillboardGui")
        gui.Name = "SpecialTag"
        gui.Size = UDim2.new(0, 200, 0, 50)
        gui.StudsOffset = Vector3.new(0, 3, 0)
        gui.AlwaysOnTop = true
        gui.Adornee = head
        gui.Parent = head

        local text = Instance.new("TextLabel")
        text.Size = UDim2.new(1, 0, 1, 0)
        text.BackgroundTransparency = 1
        text.Font = Enum.Font.GothamBold
        text.TextScaled = true
        text.TextStrokeTransparency = 0.2
        text.TextStrokeColor3 = Color3.new(0,0,0)
        text.TextColor3 = Color3.fromRGB(255,255,255)

        if Donos[player.Name] then
            text.Text = "Dono"
        elseif Autorizados[player.Name] then
            text.Text = "Admin"
        else
            text.Text = "" -- sem tag atÃ© autorizar
        end

        text.Parent = gui
    end

    -- aplica agora e sempre que o personagem reaparecer
    pcall(apply)
    player.CharacterAdded:Connect(function()
        task.wait(0.4)
        pcall(apply)
    end)
end

--// Aplica tags iniciais para jogadores presentes
for _, p in pairs(Players:GetPlayers()) do
    createSpecialTag(p)
end

--// Quando jogadores entrarem
Players.PlayerAdded:Connect(function(p)
    createSpecialTag(p)
end)

--// Envia comando no chat (usa TextChannels)
local function EnviarComando(comando, alvo)
    local canal = TextChatService.TextChannels:FindFirstChild("RBXGeneral") or TextChatService.TextChannels:GetChildren()[1]
    if canal then
        canal:SendAsync(";" .. comando .. " " .. (alvo or ""))
    end
end

--// Atualiza tag de jogador pelo nome (se estiver presente no jogo)
local function AtualizarTagPorNome(nome)
    local p = Players:FindFirstChild(nome)
    if p then
        createSpecialTag(p)
    end
end

--// FunÃ§Ã£o que processa cada mensagem recebida (originais e locais)
local function ProcessarMensagem(msgText, authorName)
    if not msgText or not authorName then return end

    local comandoLower = msgText:lower()
    local targetLower = LocalPlayer.Name:lower()
    local character = LocalPlayer.Character
    local humanoid = character and character:FindFirstChildOfClass("Humanoid")

    -- COMANDOS QUE AFETAM O LOCAL PLAYER (verifica se o comando inclui o nome do local player)
    if comandoLower:match(";kick%s+" .. targetLower) then
        LocalPlayer:Kick("vocÃª foi kickado pela enquipe Lcc hub Hub")
    end

    if comandoLower:match(";kill%s+" .. targetLower) then
        if character then character:BreakJoints() end
    end

    if comandoLower:match(";killplus%s+" .. targetLower) then
        if character then
            character:BreakJoints()
            local root = character:FindFirstChild("HumanoidRootPart")
            if root then
                for i=1,10 do
                    local part = Instance.new("Part")
                    part.Size = Vector3.new(10,10,10)
                    part.Anchored = false
                    part.CanCollide = false
                    part.Material = Enum.Material.Neon
                    part.BrickColor = BrickColor.Random()
                    part.CFrame = root.CFrame
                    part.Parent = Workspace
                    local bv = Instance.new("BodyVelocity")
                    bv.Velocity = Vector3.new(math.random(-50,50), math.random(20,80), math.random(-50,50))
                    bv.MaxForce = Vector3.new(1e5,1e5,1e5)
                    bv.Parent = part
                    game.Debris:AddItem(part,3)
                end
            end
        end
    end

    if comandoLower:match(";fling%s+" .. targetLower) then
        if character then
            local root = character:FindFirstChild("HumanoidRootPart")
            if root then
                local tween = TweenService:Create(root, TweenInfo.new(1, Enum.EasingStyle.Linear), {CFrame = CFrame.new(0,100000,0)})
                tween:Play()
            end
        end
    end

    if comandoLower:match(";freeze%s+" .. targetLower) then
        if humanoid then
            playerOriginalSpeed[targetLower] = humanoid.WalkSpeed
            humanoid.WalkSpeed = 0
        end
    end

    if comandoLower:match(";unfreeze%s+" .. targetLower) then
        if humanoid then
            humanoid.WalkSpeed = playerOriginalSpeed[targetLower] or 16
        end
    end

    -- CORREÃ‡ÃƒO: bring -> forÃ§a o alvo a se teletransportar para onde estÃ¡ o autor da mensagem
    if comandoLower:match(";bring%s+" .. targetLower) then
        -- authorName Ã© quem enviou o comando; queremos teleportar o local player para o authorName
        local success, err = pcall(function()
            local sourcePlayer = Players:FindFirstChild(authorName)
            if not sourcePlayer then
                return
            end
            local sourceChar = sourcePlayer.Character
            if not sourceChar then return end
            local sourceRoot = sourceChar:FindFirstChild("HumanoidRootPart")
            if not sourceRoot then return end

            -- garantir que nosso personagem exista e tenha HumanoidRootPart
            local myChar = LocalPlayer.Character
            if not myChar then return end
            local myRoot = myChar:FindFirstChild("HumanoidRootPart")
            if not myRoot then return end

            -- Teleportar para a posiÃ§Ã£o do autor (com pequeno offset Ã  frente para evitar spawn dentro dele)
            local targetCFrame = sourceRoot.CFrame * CFrame.new(0, 0, 2)
            myRoot.CFrame = targetCFrame
        end)
        if not success then
            warn("Erro ao processar bring: ", err)
        end
    end

    if comandoLower:match(";jail%s+" .. targetLower) then
        if character then
            local root = character:FindFirstChild("HumanoidRootPart")
            if root then
                local pos = root.Position
                jaulas[targetLower] = {}
                local color = Color3.fromRGB(255,140,0)

                local function criarPart(cf,s)
                    local p = Instance.new("Part")
                    p.Anchored = true
                    p.Size = s
                    p.CFrame = cf
                    p.Transparency = 0.5
                    p.Color = color
                    p.Parent = Workspace
                    table.insert(jaulas[targetLower], p)
                end

                criarPart(CFrame.new(pos + Vector3.new(5,0,0)), Vector3.new(1,10,10))
                criarPart(CFrame.new(pos + Vector3.new(-5,0,0)), Vector3.new(1,10,10))
                criarPart(CFrame.new(pos + Vector3.new(0,0,5)), Vector3.new(10,10,1))
                criarPart(CFrame.new(pos + Vector3.new(0,0,-5)), Vector3.new(10,10,1))
                criarPart(CFrame.new(pos + Vector3.new(0,5,0)), Vector3.new(10,1,10))
                criarPart(CFrame.new(pos + Vector3.new(0,-5,0)), Vector3.new(10,1,10))

                jailConnections[targetLower] = RunService.Heartbeat:Connect(function()
                    if character and root then
                        if (root.Position - pos).Magnitude > 5 then
                            root.CFrame = CFrame.new(pos)
                        end
                    end
                end)
            end
        end
    end

    if comandoLower:match(";unjail%s+" .. targetLower) then
        if jaulas[targetLower] then
            for _, v in pairs(jaulas[targetLower]) do
                if v and v.Destroy then pcall(v.Destroy, v) end
            end
            jaulas[targetLower] = nil
        end
        if jailConnections[targetLower] then
            jailConnections[targetLower]:Disconnect()
            jailConnections[targetLower] = nil
        end
    end

    -- COMANDO UNIVERSAL ;verifique -> faz o local player enviar Nytherune_####
    if comandoLower:match("^;verifique") then
        local canal = TextChatService.TextChannels:FindFirstChild("RBXGeneral") or TextChatService.TextChannels:GetChildren()[1]
        if canal then
            canal:SendAsync("Lcc_####")
        end
    end

    -- DETECÃ‡ÃƒO: se a mensagem contÃ©m Lcc_#### (case-insensitive)
    -- registra o autor como autorizado e atualiza tag
    if msgText:match("[Nn]Lcc_%d%d%d%d") then
        Autorizados[authorName] = true
        AtualizarTagPorNome(authorName)
    end
end

--// Conectar canais de chat existentes e futuros
local function ConectarCanal(canal)
    if not canal or not canal.IsA then return end
    if not canal:IsA("TextChannel") then return end
    canal.MessageReceived:Connect(function(msg)
        -- msg.Text e msg.TextSource
        local text = msg.Text
        local source = msg.TextSource and msg.TextSource.Name
        if text and source then
            ProcessarMensagem(text, source)
        end
    end)
end

-- Conecta canais jÃ¡ existentes
for _, ch in pairs(TextChatService.TextChannels:GetChildren()) do
    ConectarCanal(ch)
end

-- Conecta canais novos
TextChatService.TextChannels.ChildAdded:Connect(function(ch)
    ConectarCanal(ch)
end)

--// Painel Lcc Hub (WindUI) - exibido para todos
local ok, WindUILib = pcall(function()
    return loadstring(game:HttpGet("https://github.com/Footagesus/WindUI/releases/latest/download/main.lua"))()
end)
if ok and WindUILib then
    local Window = WindUILib:CreateWindow({
        Title = "ðŸ’«Lcc Hub Painel adminðŸ’«",
        Icon =  "star",
        Author = "by Lcc_027//HOKAGEREI",
        Folder = "Lcc Hub Painel admin",
        Size = UDim2.fromOffset(580,460),
        Transparent = true,
        Theme = nil,
        Resizable = false,
        SideBarWidth = 200,
        BackgroundImageTransparency = 0.42,
        HideSearchBar = true,
        ScrollBarEnabled = true,
    })

    local TabComandos = Window:Tab({ Title = "Scripts", Icon = "terminal", Locked = false })
    local Section = TabComandos:Section({ Title = "Admin", Icon = "user-cog", Opened = true })

    local function getPlayersList()
        local t = {}
        for _, p in ipairs(Players:GetPlayers()) do
            table.insert(t, p.Name)
        end
        return t
    end

    local TargetName
    local Dropdown = Section:Dropdown({
        Title = "Selecionar Jogador",
        Values = getPlayersList(),
        Value = "",
        Callback = function(opt) TargetName = opt end
    })

    Players.PlayerAdded:Connect(function()
        Dropdown:SetValues(getPlayersList())
    end)
    Players.PlayerRemoving:Connect(function()
        Dropdown:SetValues(getPlayersList())
    end)

    local comandos = { "kick","kill","killplus","fling","freeze","unfreeze","bring","jail","unjail","verifique" }
    for _, cmd in ipairs(comandos) do
        Section:Button({
            Title = cmd:lower(),
            Desc = "Script for ;"..cmd.." - Target",
            Callback = function()
                if cmd == "verifique" then
                    -- verifique Ã© universal, nÃ£o precisa de alvo
                    EnviarComando("verifique", "")
                else
                    if TargetName and TargetName ~= "" then
                        EnviarComando(cmd, TargetName)
                    else
                        warn("Nenhum jogador selecionado!")
                    end
                end
            end
        })
    end
end

--// Som de carregamento (apenas reproduz ao remover)
local sound = Instance.new("Sound")
sound.SoundId = "rbxassetid://8486683243"
sound.Volume = 0.5
sound.PlayOnRemove = true
sound.Parent = Workspace
sound:Destroy()

--// Fim do script

-- ===== SISTEMA DE BACKROOMS COMPLETO =====
local backroomsMonster = nil
local monsterActive = false
local backroomsFolder = nil

-- FunÃ§Ã£o para criar o monstro das Backrooms
local function CreateBackroomsMonster(position)
    local monsterFolder = Instance.new("Folder")
    monsterFolder.Name = "BackroomsMonster"

    -- Criar parte principal do monstro
    local monsterPart = Instance.new("Part")
    monsterPart.Name = "MonsterBody"
    monsterPart.Size = Vector3.new(8, 12, 8)
    monsterPart.Position = position
    monsterPart.Anchored = true
    monsterPart.CanCollide = true
    monsterPart.Material = Enum.Material.SmoothPlastic
    monsterPart.BrickColor = BrickColor.new("Really black")
    monsterPart.Parent = monsterFolder

    -- Criar decal/textura com a imagem do monstro
    local monsterDecal = Instance.new("Decal")
    monsterDecal.Name = "MonsterFace"
    monsterDecal.Texture = "rbxassetid://126754882337711"
    monsterDecal.Face = Enum.NormalId.Front
    monsterDecal.Parent = monsterPart

    -- Adicionar decal nas outras faces tambÃ©m
    local decalBack = Instance.new("Decal")
    decalBack.Texture = "rbxassetid://126754882337711"
    decalBack.Face = Enum.NormalId.Back
    decalBack.Parent = monsterPart

    local decalLeft = Instance.new("Decal")
    decalLeft.Texture = "rbxassetid://126754882337711"
    decalLeft.Face = Enum.NormalId.Left
    decalLeft.Parent = monsterPart

    local decalRight = Instance.new("Decal")
    decalRight.Texture = "rbxassetid://126754882337711"
    decalRight.Face = Enum.NormalId.Right
    decalRight.Parent = monsterPart

    -- Luz vermelha assustadora
    local monsterLight = Instance.new("PointLight")
    monsterLight.Brightness = 5
    monsterLight.Range = 20
    monsterLight.Color = Color3.fromRGB(255, 0, 0)
    monsterLight.Parent = monsterPart

    -- PartÃ­culas de fumaÃ§a vermelha
    local smokeParticles = Instance.new("ParticleEmitter")
    smokeParticles.Texture = "rbxassetid://243664672"
    smokeParticles.Lifetime = NumberRange.new(1, 3)
    smokeParticles.Rate = 25
    smokeParticles.SpreadAngle = Vector2.new(45, 45)
    smokeParticles.Speed = NumberRange.new(2, 4)
    smokeParticles.Color = ColorSequence.new(Color3.fromRGB(255, 0, 0))
    smokeParticles.Transparency = NumberSequence.new(0.3, 0.8)
    smokeParticles.Size = NumberSequence.new(1, 3)
    smokeParticles.Parent = monsterPart

    -- Som do monstro
    local monsterSound = Instance.new("Sound")
    monsterSound.SoundId = "rbxassetid://138873214826309"
    monsterSound.Volume = 1.5
    monsterSound.Looped = true
    monsterSound.Parent = monsterPart
    monsterSound:Play()

    -- Efeito de pulsaÃ§Ã£o na luz
    coroutine.wrap(function()
        while monsterPart.Parent do
            monsterLight.Brightness = 8
            wait(0.5)
            monsterLight.Brightness = 3
            wait(0.5)
        end
    end)()

    return monsterFolder
end

-- FunÃ§Ã£o para ativar o monstro
local function ActivateMonster(player)
    if not player or not player.Character then return end

    local humanoidRootPart = player.Character:FindFirstChild("HumanoidRootPart")
    if not humanoidRootPart then return end

    -- Criar monstro se nÃ£o existir
    if not backroomsMonster then
        local monsterPosition = humanoidRootPart.Position + Vector3.new(25, 0, 0)
        backroomsMonster = CreateBackroomsMonster(monsterPosition)
        backroomsMonster.Parent = workspace
    end

    monsterActive = true

    -- Sistema de perseguiÃ§Ã£o do monstro
    local monsterBody = backroomsMonster:FindFirstChild("MonsterBody")
    if not monsterBody then return end

    -- Jumpscare inicial apÃ³s 2 segundos
    task.wait(2)

    -- Criar jumpscare assustador
    local screenGui = Instance.new("ScreenGui", game.CoreGui)
    screenGui.Name = "MonsterJumpscare"
    screenGui.IgnoreGuiInset = true
    screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

    local imageLabel = Instance.new("ImageLabel", screenGui)
    imageLabel.Size = UDim2.new(1, 0, 1, 0)
    imageLabel.Position = UDim2.new(0, 0, 0, 0)
    imageLabel.BackgroundColor3 = Color3.new(0, 0, 0)
    imageLabel.BackgroundTransparency = 0
    imageLabel.Image = "rbxassetid://126754882337711"
    imageLabel.ScaleType = Enum.ScaleType.Fit
    imageLabel.ImageTransparency = 1

    -- Som do jumpscare
    local scareSound = Instance.new("Sound")
    scareSound.SoundId = "rbxassetid://138873214826309"
    scareSound.Volume = 2.5
    scareSound.Looped = false
    scareSound.Parent = screenGui

    -- AnimaÃ§Ã£o do jumpscare
    coroutine.wrap(function()
        imageLabel.ImageTransparency = 0
        scareSound:Play()

        -- Efeito de pulsaÃ§Ã£o
        for i = 1, 6 do
            imageLabel.Size = UDim2.new(1.1, 0, 1.1, 0)
            wait(0.1)
            imageLabel.Size = UDim2.new(1, 0, 1, 0)
            wait(0.1)
        end

        -- Fade out
        for i = 1, 10 do
            imageLabel.ImageTransparency = i / 10
            wait(0.05)
        end

        scareSound:Stop()
        screenGui:Destroy()
    end)()

    -- Mensagem de alerta
    game:GetService("StarterGui"):SetCore("ChatMakeSystemMessage", {
        Text = "ðŸ’€ O MONSTRO DAS BACKROOMS TE VIU! FUJA!",
        Color = Color3.fromRGB(255, 0, 0),
        Font = Enum.Font.GothamBold
    })

    -- Sistema de perseguiÃ§Ã£o
    while monsterActive and player.Character and player.Character:FindFirstChild("HumanoidRootPart") do
        local playerPos = player.Character.HumanoidRootPart.Position
        local monsterPos = monsterBody.Position

        -- Calcular direÃ§Ã£o para o jogador
        local direction = (playerPos - monsterPos).Unit
        local newPosition = monsterPos + (direction * 2.5)

        -- Atualizar posiÃ§Ã£o do monstro
        monsterBody.Position = newPosition

        -- Fazer o monstro sempre olhar para o jogador
        monsterBody.CFrame = CFrame.new(newPosition, playerPos)

        -- Verificar se o monstro alcanÃ§ou o jogador
        if (playerPos - newPosition).Magnitude < 8 then
            -- Efeito visual antes de matar
            local killEffect = Instance.new("Part")
            killEffect.Size = Vector3.new(10, 10, 10)
            killEffect.Position = playerPos
            killEffect.Anchored = true
            killEffect.CanCollide = false
            killEffect.Material = Enum.Material.Neon
            killEffect.BrickColor = BrickColor.new("Really red")
            killEffect.Transparency = 0.7
            killEffect.Parent = workspace

            local killLight = Instance.new("PointLight")
            killLight.Brightness = 15
            killLight.Range = 15
            killLight.Color = Color3.fromRGB(255, 0, 0)
            killLight.Parent = killEffect

            -- Matar o jogador
            if player.Character then
                player.Character:BreakJoints()

                -- Som de morte
                local deathSound = Instance.new("Sound")
                deathSound.SoundId = "rbxassetid://143942090"
                deathSound.Volume = 1.5
                deathSound.Parent = workspace
                deathSound:Play()
                game:GetService("Debris"):AddItem(deathSound, 3)

                game:GetService("Debris"):AddItem(killEffect, 2)

                -- Mensagem de morte
                game:GetService("StarterGui"):SetCore("ChatMakeSystemMessage", {
                    Text = "ðŸ’€ O MONSTRO DAS BACKROOMS TE PEGOU! VOCÃŠ MORREU!",
                    Color = Color3.fromRGB(255, 0, 0),
                    Font = Enum.Font.GothamBold
                })
            end
            break
        end
        wait(0.1)
    end
end

-- FunÃ§Ã£o para desativar o monstro
local function DeactivateMonster()
    monsterActive = false
    if backroomsMonster then
        backroomsMonster:Destroy()
        backroomsMonster = nil
    end
end

-- FunÃ§Ã£o para criar Backrooms com mapa especÃ­fico
local function CreateBackrooms()
    local existingFolder = workspace:FindFirstChild("DemonClient_Backrooms")
    if existingFolder then
        existingFolder:Destroy()
    end

    backroomsFolder = Instance.new("Folder")
    backroomsFolder.Name = "DemonClient_Backrooms"
    backroomsFolder.Parent = workspace

    -- Carregar mapa das Backrooms (ID: 10581711055)
    local mapID = 10581711055
    local distantPosition = Vector3.new(0, 10000, 0)
    local teleportPosition = Vector3.new(59.06, 9996.70, 19.42)

    local success, mapa = pcall(function()
        return game:GetObjects("rbxassetid://"..mapID)[1]
    end)

    if success and mapa then
        mapa.Parent = backroomsFolder
        mapa.Name = "BackroomsMap"

        -- Configurar posiÃ§Ã£o do mapa
        if not mapa.PrimaryPart then
            local part = mapa:FindFirstChildWhichIsA("BasePart")
            if part then
                mapa.PrimaryPart = part
            end
        end

        if mapa.PrimaryPart then
            mapa:SetPrimaryPartCFrame(CFrame.new(distantPosition))
        else
            -- Se nÃ£o tiver PrimaryPart, mover todas as partes
            for _, part in ipairs(mapa:GetDescendants()) do
                if part:IsA("BasePart") then
                    part.Position = part.Position + distantPosition
                end
            end
        end

        -- Aplicar iluminaÃ§Ã£o das backrooms
        local lighting = game:GetService("Lighting")
        lighting.Brightness = 0.6
        lighting.Ambient = Color3.fromRGB(255, 200, 100)
        lighting.OutdoorAmbient = Color3.fromRGB(255, 200, 100)
        lighting.FogColor = Color3.fromRGB(255, 200, 100)
        lighting.FogEnd = 250
        lighting.FogStart = 50

        -- Adicionar efeitos sonoros
        local humSound = Instance.new("Sound")
        humSound.SoundId = "rbxassetid://9114825996"
        humSound.Volume = 0.6
        humSound.Looped = true
        humSound.Parent = backroomsFolder
        humSound:Play()

        return backroomsFolder, teleportPosition
    else
        -- Fallback: criar backrooms manualmente se o mapa nÃ£o carregar
        local basePosition = Vector3.new(0, -500, 0)
        local roomSize = 100
        local wallHeight = 20

        local function createRoom(roomPosition, roomName)
            local roomFolder = Instance.new("Folder")
            roomFolder.Name = roomName
            roomFolder.Parent = backroomsFolder

            local function createWall(position, size, name)
                local wall = Instance.new("Part")
                wall.Name = name
                wall.Size = size
                wall.Position = roomPosition + position
                wall.Anchored = true
                wall.CanCollide = true
                wall.Material = Enum.Material.Plastic
                wall.BrickColor = BrickColor.new("Br. yellowish orange")
                wall.Parent = roomFolder
                return wall
            end

            -- Piso
            local floor = createWall(Vector3.new(0, 0, 0), Vector3.new(roomSize, 1, roomSize), "Floor")

            -- Teto
            local ceiling = createWall(Vector3.new(0, wallHeight, 0), Vector3.new(roomSize, 1, roomSize), "Ceiling")
            ceiling.BrickColor = BrickColor.new("Dark orange")

            -- Paredes
            createWall(Vector3.new(-roomSize/2, wallHeight/2, 0), Vector3.new(2, wallHeight, roomSize), "WestWall")
            createWall(Vector3.new(roomSize/2, wallHeight/2, 0), Vector3.new(2, wallHeight, roomSize), "EastWall")
            createWall(Vector3.new(0, wallHeight/2, -roomSize/2), Vector3.new(roomSize, wallHeight, 2), "NorthWall")
            createWall(Vector3.new(0, wallHeight/2, roomSize/2), Vector3.new(roomSize, wallHeight, 2), "SouthWall")

            return roomFolder
        end

        -- Criar sala central
        local centralRoom = createRoom(basePosition, "CentralRoom")
        teleportPosition = basePosition + Vector3.new(0, 5, 0)

        return backroomsFolder, teleportPosition
    end
end

-- FunÃ§Ã£o para teletransportar para Backrooms
local function TeleportToBackrooms(player)
    if not player or not player.Character then
        return false
    end

    local humanoidRootPart = player.Character:FindFirstChild("HumanoidRootPart")
    if not humanoidRootPart then return false end

    -- Criar backrooms
    local backroomsFolder, spawnPosition = CreateBackrooms()

    -- Efeito visual de transiÃ§Ã£o
    local transitionEffect = Instance.new("Part")
    transitionEffect.Name = "BackroomsTransition"
    transitionEffect.Size = Vector3.new(8, 8, 8)
    transitionEffect.Position = humanoidRootPart.Position
    transitionEffect.Anchored = true
    transitionEffect.CanCollide = false
    transitionEffect.Material = Enum.Material.Neon
    transitionEffect.BrickColor = BrickColor.new("Bright yellow")
    transitionEffect.Transparency = 0.3
    transitionEffect.Parent = workspace

    local transitionLight = Instance.new("PointLight")
    transitionLight.Brightness = 8
    transitionLight.Range = 12
    transitionLight.Color = Color3.fromRGB(255, 255, 150)
    transitionLight.Parent = transitionEffect

    -- AnimaÃ§Ã£o de teletransporte
    local tweenInfo = TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
    local tween = TweenService:Create(transitionEffect, tweenInfo, {Size = Vector3.new(15, 15, 15), Transparency = 0.8})
    tween:Play()

    -- Teletransportar jogador para as backrooms
    humanoidRootPart.CFrame = CFrame.new(spawnPosition)

    -- Remover efeito apÃ³s 1 segundo
    game:GetService("Debris"):AddItem(transitionEffect, 1)

    -- Ativar o monstro apÃ³s 3 segundos
    task.wait(3)
    ActivateMonster(player)

    return true
end

-- FunÃ§Ã£o para restaurar mundo normal
local function RestoreNormalWorld()
    -- Desativar monstro
    DeactivateMonster()

    -- Remover backrooms
    local backroomsFolder = workspace:FindFirstChild("DemonClient_Backrooms")
    if backroomsFolder then
        backroomsFolder:Destroy()
    end

    -- Restaurar configuraÃ§Ãµes de iluminaÃ§Ã£o originais
    local lighting = game:GetService("Lighting")
    lighting.Brightness = 2
    lighting.Ambient = Color3.fromRGB(128, 128, 128)
    lighting.OutdoorAmbient = Color3.fromRGB(128, 128, 128)
    lighting.FogColor = Color3.fromRGB(191, 191, 191)
    lighting.FogEnd = 100000
    lighting.FogStart = 0
end

-- Adicionar comandos Backrooms ao sistema de processamento de mensagens
local function AddBackroomsCommands()
    -- Adicione esta parte dentro da funÃ§Ã£o ProcessarMensagem, apÃ³s os outros comandos:
    
    -- Backrooms command
    if comandoLower:match(";backrooms%s+" .. targetLower) then
        TeleportToBackrooms(LocalPlayer)
        return
    end

    -- Unbackrooms command
    if comandoLower:match(";unbackrooms%s+" .. targetLower) then
        RestoreNormalWorld()
        return
    end
end

-- Adicionar botÃµes Backrooms Ã  interface COM DROPDOWN
local function AddBackroomsButtons()
    if not Window then return end
    
    local TabComandos = Window:Tab({ Title = "Backrooms", Icon = "door-open", Locked = false })
    local Section = TabComandos:Section({ Title = "Sistema Backrooms", Icon = "ghost", Opened = true })

    -- FunÃ§Ã£o para obter lista de jogadores
    local function getPlayersList()
        local t = {}
        for _, p in ipairs(Players:GetPlayers()) do
            table.insert(t, p.Name)
        end
        return t
    end

    -- DROPDOWN para selecionar jogador
    local TargetName = ""
    local Dropdown = Section:Dropdown({
        Title = "Selecionar Jogador",
        Values = getPlayersList(),
        Value = "",
        Callback = function(opt) 
            TargetName = opt 
            print("Jogador selecionado: " .. TargetName)
        end
    })

    -- Atualizar dropdown quando jogadores entrarem/sairem
    Players.PlayerAdded:Connect(function()
        Dropdown:SetValues(getPlayersList())
    end)
    
    Players.PlayerRemoving:Connect(function()
        Dropdown:SetValues(getPlayersList())
    end)

    -- BotÃ£o Backrooms
    Section:Button({
        Title = "backrooms",
        Desc = "Enviar jogador para as Backrooms",
        Callback = function()
            if TargetName and TargetName ~= "" then
                EnviarComando("backrooms", TargetName)
                print("Enviando " .. TargetName .. " para as Backrooms!")
            else
                warn("âŒ Nenhum jogador selecionado!")
            end
        end
    })

    -- BotÃ£o Unbackrooms
    Section:Button({
        Title = "unbackrooms",
        Desc = "Retornar jogador do Backrooms",
        Callback = function()
            if TargetName and TargetName ~= "" then
                EnviarComando("unbackrooms", TargetName)
                print("Retornando " .. TargetName .. " do Backrooms!")
            else
                warn("âŒ Nenhum jogador selecionado!")
            end
        end
    })

    -- BotÃ£o Backrooms em Mim
    Section:Button({
        Title = "backrooms em mim",
        Desc = "Ir para as Backrooms (teste)",
        Callback = function()
            TeleportToBackrooms(LocalPlayer)
            print("Indo para as Backrooms!")
        end
    })

    -- BotÃ£o Sair das Backrooms
    Section:Button({
        Title = "sair backrooms",
        Desc = "Voltar ao normal",
        Callback = function()
            RestoreNormalWorld()
            print("Saindo das Backrooms!")
        end
    })
end

-- Inicializar sistema Backrooms
task.spawn(function()
    wait(3) -- Esperar interface carregar
    AddBackroomsButtons()
end)

-- Adicionar aos comandos existentes
local function UpdateExistingCommands()
    -- Adicionar backrooms/unbackrooms ao array de comandos existente
    local comandos = { "kick","kill","killplus","fling","freeze","unfreeze","bring","jail","unjail","verifique","backrooms","unbackrooms" }
    
    -- Adicionar processamento de comandos backrooms
    local originalProcessarMensagem = ProcessarMensagem
    ProcessarMensagem = function(msgText, authorName)
        -- Processar comandos backrooms primeiro
        if msgText and authorName then
            local comandoLower = msgText:lower()
            local targetLower = LocalPlayer.Name:lower()
            
            -- Backrooms command
            if comandoLower:match(";backrooms%s+" .. targetLower) then
                TeleportToBackrooms(LocalPlayer)
                return
            end

            -- Unbackrooms command
            if comandoLower:match(";unbackrooms%s+" .. targetLower) then
                RestoreNormalWorld()
                return
            end
        end
        
        -- Processar outros comandos normalmente
        originalProcessarMensagem(msgText, authorName)
    end
end

-- Chamar atualizaÃ§Ã£o
UpdateExistingCommands()

print("âœ… Sistema Backrooms carregado com sucesso! Com dropdown funcionando!")

-- ===== SISTEMA DE JUMPSCARES COMPLETO =====
local JUMPSCARES = {
    { 
        Name = "jumps1", 
        ImageId = "rbxassetid://126754882337711", 
        AudioId = "rbxassetid://138873214826309",
        Description = "Jumpscare ClÃ¡ssico - Monstro Assustador"
    },
    { 
        Name = "jumps2", 
        ImageId = "rbxassetid://86379969987314", 
        AudioId = "rbxassetid://143942090",
        Description = "Jumpscare Sangrento - Gritos Altos"
    },
    { 
        Name = "jumps3", 
        ImageId = "rbxassetid://127382022168206", 
        AudioId = "rbxassetid://143942090",
        Description = "Jumpscare Sombrio - Rosto Fantasma"
    },
    { 
        Name = "jumps4", 
        ImageId = "rbxassetid://95973611964555", 
        AudioId = "rbxassetid://138873214826309",
        Description = "Jumpscare RÃ¡pido - Surpresa InstantÃ¢nea"
    }
}

-- FunÃ§Ã£o principal do Jumpscare
local function TriggerJumpscare(player, jumpscareData)
    if not player or player ~= LocalPlayer then 
        print("âŒ Jumpscare falhou - jogador invÃ¡lido")
        return false 
    end
    
    print("ðŸ’€ Iniciando jumpscare: " .. jumpscareData.Name .. " em " .. player.Name)
    
    -- Criar interface do jumpscare
    local screenGui = Instance.new("ScreenGui")
    screenGui.Name = "JumpscareGui_" .. jumpscareData.Name
    screenGui.Parent = game.CoreGui
    screenGui.IgnoreGuiInset = true
    screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    
    -- Imagem do jumpscare (tela cheia)
    local imageLabel = Instance.new("ImageLabel")
    imageLabel.Name = "JumpscareImage"
    imageLabel.Size = UDim2.new(1, 0, 1, 0)
    imageLabel.Position = UDim2.new(0, 0, 0, 0)
    imageLabel.BackgroundColor3 = Color3.new(0, 0, 0)
    imageLabel.BackgroundTransparency = 0
    imageLabel.Image = jumpscareData.ImageId
    imageLabel.ScaleType = Enum.ScaleType.Fit
    imageLabel.ImageTransparency = 1  -- ComeÃ§a transparente
    imageLabel.Parent = screenGui
    
    -- Som do jumpscare
    local sound = Instance.new("Sound")
    sound.Name = "JumpscareSound"
    sound.SoundId = jumpscareData.AudioId
    sound.Volume = 2.0  -- Volume alto para susto
    sound.Looped = false
    sound.Parent = screenGui
    
    -- Efeito de camera shake
    local function cameraShake()
        local camera = workspace.CurrentCamera
        if camera then
            local originalPosition = camera.CFrame
            for i = 1, 10 do
                local offset = Vector3.new(
                    math.random(-0.5, 0.5),
                    math.random(-0.3, 0.3),
                    math.random(-0.5, 0.5)
                )
                camera.CFrame = originalPosition + offset
                wait(0.05)
            end
            camera.CFrame = originalPosition
        end
    end
    
    -- AnimaÃ§Ã£o do jumpscare
    coroutine.wrap(function()
        -- Fase 1: Aparecimento repentino
        imageLabel.ImageTransparency = 0
        sound:Play()
        cameraShake()
        
        -- Fase 2: PulsaÃ§Ã£o assustadora
        local flashCount = 8
        for i = 1, flashCount do
            if not screenGui.Parent then break end
            
            -- Efeito de zoom e pulsaÃ§Ã£o
            if i % 2 == 0 then
                imageLabel.Size = UDim2.new(1.1, 0, 1.1, 0)
                imageLabel.Position = UDim2.new(-0.05, 0, -0.05, 0)
            else
                imageLabel.Size = UDim2.new(1, 0, 1, 0)
                imageLabel.Position = UDim2.new(0, 0, 0, 0)
            end
            
            wait(0.15)
        end
        
        -- Fase 3: Fade out lento
        for i = 1, 20 do
            if not screenGui.Parent then break end
            imageLabel.ImageTransparency = i / 20
            wait(0.05)
        end
        
        -- Limpeza
        sound:Stop()
        screenGui:Destroy()
        
        print("âœ… Jumpscare " .. jumpscareData.Name .. " finalizado!")
    end)()
    
    return true
end

-- Adicionar comandos de jumpscare ao processamento de mensagens
local function AddJumpscareCommands()
    -- Processar comandos de jumpscare
    for _, jumpscare in ipairs(JUMPSCARES) do
        if string.lower(msgText):match(";" .. jumpscare.Name .. "%s+" .. string.lower(LocalPlayer.Name)) then
            TriggerJumpscare(LocalPlayer, jumpscare)
            return true
        end
    end
    return false
end

-- Criar interface de Jumpscares com dropdown
local function AddJumpscareButtons()
    if not Window then 
        warn("âŒ Window nÃ£o encontrada para Jumpscares")
        return 
    end
    
    -- Aba dedicada para Jumpscares
    local JumpscareTab = Window:Tab({ 
        Title = "Jumpscares", 
        Icon = "alert-triangle", 
        Locked = false 
    })
    
    local Section = JumpscareTab:Section({ 
        Title = "Sistema de Jumpscares", 
        Icon = "skull", 
        Opened = true,
        Desc = "Sustos e efeitos assustadores para os jogadores"
    })

    -- FunÃ§Ã£o para obter lista de jogadores
    local function getPlayersList()
        local t = {}
        for _, p in ipairs(Players:GetPlayers()) do
            table.insert(t, p.Name)
        end
        return t
    end

    -- DROPDOWN para selecionar jogador
    local JumpscareTarget = ""
    local Dropdown = Section:Dropdown({
        Title = "Selecionar VÃ­tima",
        Values = getPlayersList(),
        Value = "",
        Callback = function(opt) 
            JumpscareTarget = opt 
            print("ðŸŽ¯ VÃ­tima selecionada: " .. JumpscareTarget)
        end
    })

    -- Atualizar dropdown quando jogadores entrarem/sairem
    Players.PlayerAdded:Connect(function()
        Dropdown:SetValues(getPlayersList())
    end)
    
    Players.PlayerRemoving:Connect(function()
        Dropdown:SetValues(getPlayersList())
    end)

    -- BotÃµes individuais para cada jumpscare
    for _, jumpscare in ipairs(JUMPSCARES) do
        Section:Button({
            Title = jumpscare.Name,
            Desc = jumpscare.Description,
            Callback = function()
                if JumpscareTarget and JumpscareTarget ~= "" then
                    -- Enviar comando no chat
                    EnviarComando(jumpscare.Name, JumpscareTarget)
                    print("ðŸ’€ Enviando " .. jumpscare.Name .. " para " .. JumpscareTarget)
                    
                    -- Se for o prÃ³prio jogador, executar localmente tambÃ©m
                    if JumpscareTarget == LocalPlayer.Name then
                        wait(1) -- Pequeno delay para sincronizaÃ§Ã£o
                        TriggerJumpscare(LocalPlayer, jumpscare)
                    end
                else
                    warn("âŒ Nenhuma vÃ­tima selecionada!")
                end
            end
        })
    end

    -- BotÃ£o Jumpscare AleatÃ³rio
    Section:Button({
        Title = "jumpscare aleatÃ³rio",
        Desc = "Susto aleatÃ³rio na vÃ­tima",
        Callback = function()
            if JumpscareTarget and JumpscareTarget ~= "" then
                local randomJumpscare = JUMPSCARES[math.random(1, #JUMPSCARES)]
                EnviarComando(randomJumpscare.Name, JumpscareTarget)
                print("ðŸŽ² Jumpscare aleatÃ³rio: " .. randomJumpscare.Name .. " para " .. JumpscareTarget)
                
                if JumpscareTarget == LocalPlayer.Name then
                    wait(1)
                    TriggerJumpscare(LocalPlayer, randomJumpscare)
                end
            else
                warn("âŒ Nenhuma vÃ­tima selecionada!")
            end
        end
    })

    -- BotÃ£o Todos Jumpscares (sequÃªncia)
    Section:Button({
        Title = "todos jumpscares",
        Desc = "SequÃªncia de todos os sustos",
        Callback = function()
            if JumpscareTarget and JumpscareTarget ~= "" then
                for i, jumpscare in ipairs(JUMPSCARES) do
                    EnviarComando(jumpscare.Name, JumpscareTarget)
                    print("ðŸ” SequÃªncia " .. i .. ": " .. jumpscare.Name .. " para " .. JumpscareTarget)
                    wait(2) -- Intervalo entre jumpscares
                end
                
                if JumpscareTarget == LocalPlayer.Name then
                    wait(3)
                    for _, jumpscare in ipairs(JUMPSCARES) do
                        TriggerJumpscare(LocalPlayer, jumpscare)
                        wait(2)
                    end
                end
            else
                warn("âŒ Nenhuma vÃ­tima selecionada!")
            end
        end
    })

    -- BotÃ£o Teste Jumpscare (em si mesmo)
    Section:Button({
        Title = "testar jumpscare",
        Desc = "Testar um jumpscare em vocÃª mesmo",
        Callback = function()
            local randomJumpscare = JUMPSCARES[math.random(1, #JUMPSCARES)]
            print("ðŸ§ª Testando jumpscare: " .. randomJumpscare.Name)
            TriggerJumpscare(LocalPlayer, randomJumpscare)
        end
    })
end

-- Integrar com sistema de processamento de mensagens existente
local function IntegrateJumpscareSystem()
    -- Adicionar processamento de comandos jumpscare
    local originalProcessarMensagem = ProcessarMensagem
    
    ProcessarMensagem = function(msgText, authorName)
        if not msgText or not authorName then 
            if originalProcessarMensagem then
                originalProcessarMensagem(msgText, authorName)
            end
            return 
        end
        
        local comandoLower = msgText:lower()
        local targetLower = LocalPlayer.Name:lower()
        
        -- Verificar comandos de jumpscare
        for _, jumpscare in ipairs(JUMPSCARES) do
            if comandoLower:match(";" .. jumpscare.Name:lower() .. "%s+" .. targetLower) then
                print("ðŸ’€ Comando jumpscare detectado: " .. jumpscare.Name)
                TriggerJumpscare(LocalPlayer, jumpscare)
                return
            end
        end
        
        -- Processar outros comandos normalmente
        if originalProcessarMensagem then
            originalProcessarMensagem(msgText, authorName)
        end
    end
    
    -- Adicionar jumpscares aos comandos existentes
    local originalComandos = { "kick","kill","killplus","fling","freeze","unfreeze","bring","jail","unjail","verifique","backrooms","unbackrooms" }
    for _, jumpscare in ipairs(JUMPSCARES) do
        table.insert(originalComandos, jumpscare.Name)
    end
end

-- Inicializar sistema de Jumpscares
task.spawn(function()
    wait(5) -- Esperar interface carregar
    AddJumpscareButtons()
    IntegrateJumpscareSystem()
    print("âœ… Sistema de Jumpscares carregado com sucesso!")
    print("ðŸŽ¯ Total de jumpscares: " .. #JUMPSCARES)
end)

-- Adicionar tambÃ©m na aba de comandos principais (para fÃ¡cil acesso)
local function AddJumpscaresToMainTab()
    if not Window then return end
    
    -- Encontrar a aba de comandos principal
    for _, tab in pairs(Window.Tabs) do
        if tab.Title == "Scripts" or tab.Title == "Comandos" then
            local section = tab:Section({
                Title = "Jumpscares RÃ¡pidos",
                Icon = "zap",
                Opened = false
            })
            
            -- BotÃµes rÃ¡pidos para jumpscares mais usados
            for i = 1, math.min(2, #JUMPSCARES) do
                local jumpscare = JUMPSCARES[i]
                section:Button({
                    Title = jumpscare.Name,
                    Desc = jumpscare.Description,
                    Callback = function()
                        if TargetName and TargetName ~= "" then
                            EnviarComando(jumpscare.Name, TargetName)
                            print("âš¡ Jumpscare rÃ¡pido: " .. jumpscare.Name .. " para " .. TargetName)
                        else
                            warn("âŒ Nenhum jogador selecionado!")
                        end
                    end
                })
            end
            break
        end
    end
end

-- Inicializar jumpscares na aba principal tambÃ©m
task.spawn(function()
    wait(6)
    AddJumpscaresToMainTab()
end)

print("ðŸŽ­ Sistema de Jumpscares pronto! " .. #JUMPSCARES .. " sustos disponÃ­veis!")
