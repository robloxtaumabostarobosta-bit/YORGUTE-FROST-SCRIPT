-- Carregar Rayfield
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

-- Criar janela
local Window = Rayfield:CreateWindow({
   Name = "YORGUTE FROST HUB (RP)",
   LoadingTitle = "Carregando...",
   LoadingSubtitle = "por você",
   ConfigurationSaving = {
      Enabled = false
   }
})

-- Criar abas
local PlayerTab = Window:CreateTab("Player", 4483362458)
local JobsTab = Window:CreateTab("Empregos", 4483362458)
local TeleportTab = Window:CreateTab("Teleport", 4483362458)

-- PLAYER (Sprint)
local player = game.Players.LocalPlayer

PlayerTab:CreateToggle({
   Name = "Correr (Sprint)",
   CurrentValue = false,
   Callback = function(Value)
      if player.Character and player.Character:FindFirstChild("Humanoid") then
         if Value then
            player.Character.Humanoid.WalkSpeed = 26
         else
            player.Character.Humanoid.WalkSpeed = 16
         end
      end
   end,
})

-- PLAYER (Pular mais alto)
PlayerTab:CreateToggle({
   Name = "Pulo Alto",
   CurrentValue = false,
   Callback = function(Value)
      if player.Character and player.Character:FindFirstChild("Humanoid") then
         if Value then
            player.Character.Humanoid.JumpPower = 80
         else
            player.Character.Humanoid.JumpPower = 50
         end
      end
   end,
})

-- EMPREGO: LIXEIRO (exemplo simples)
JobsTab:CreateButton({
   Name = "Trabalhar de Lixeiro",
   Callback = function()
      print("Iniciando trabalho de lixeiro...")
      -- aqui você conecta com seu sistema de job
   end,
})

-- EMPREGO: ENTREGADOR
JobsTab:CreateButton({
   Name = "Trabalhar de Entregador",
   Callback = function()
      print("Iniciando trabalho de entregas...")
   end,
})

-- TELEPORTES (coloque as posições do seu mapa)
TeleportTab:CreateButton({
   Name = "Ir para Cidade",
   Callback = function()
      local char = player.Character
      if char then
         char:MoveTo(Vector3.new(0, 5, 0))
      end
   end,
})

TeleportTab:CreateButton({
   Name = "Ir para Favela",
   Callback = function()
      local char = player.Character
      if char then
         char:MoveTo(Vector3.new(100, 5, 100))
      end
   end,
})

-- NOTIFICAÇÃO
Rayfield:Notify({
   Title = "Script carregado",
   Content = "YORGUTE FROST HUB pronto!",
   Duration = 5
})
