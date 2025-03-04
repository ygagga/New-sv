local espToggle = Section:NewToggle("Enable ESP", "Toggle ESP On/Off", function(state)
    if state then
        -- Ativar o ESP
        for _, player in pairs(game.Players:GetPlayers()) do
            if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                local espBox = Instance.new("BillboardGui")
                espBox.Adornee = player.Character.HumanoidRootPart
                espBox.Size = UDim2.new(0, 100, 0, 100)
                espBox.StudsOffset = Vector3.new(0, 3, 0)
                espBox.Parent = player.Character
                espBox.Name = "ESPBox"
                
                local frame = Instance.new("Frame")
                frame.Size = UDim2.new(1, 0, 1, 0)
                frame.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
                frame.BorderSizePixel = 0
                frame.Parent = espBox
            end
        end
    else
        -- Desativar o ESP
        for _, player in pairs(game.Players:GetPlayers()) do
            if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                local espBox = player.Character:FindFirstChild("ESPBox")
                if espBox then
                    espBox:Destroy()
                end
            end
        end
    end
end)
