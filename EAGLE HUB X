-- FlowAuth LRM compatibility variables
-- FlowAuth console: normal
LRM_IsUserPremium=false
LRM_LinkedDiscordID="\048"
LRM_ScriptName="\080\097\105\100\032\097\112"
LRM_TotalExecutions=0
LRM_SecondsLeft=math.huge
LRM_UserNote="\078\111\116\032\115\112\101\099\105\102\105\101\100"
LRM_ScriptVersion="\048\046\048\046\048\046\051"
LRM_ExecutionTrace="\102\097\049\095\087\053\049\090\073\057\053\103\070\054\097\057\118\085\099\050\065\095\070\103\067\066\054\071"
-- FlowAuth target internal
-- FlowAuth execution lease
do
local type,pcall,rawget,rawset,tonumber,ipairs=type,pcall,rawget,rawset,tonumber,ipairs
local function environmentOf(provider,fallback)
if type(provider)=="function" then local ok,value=pcall(function()return provider()end) if ok and type(value)=="table" then return value end end
return fallback
end
local environment=environmentOf(getgenv,nil)
if not environment then environment=environmentOf(getfenv,_G) end
local previous=type(environment)=="table" and rawget(environment,"FlowAuth") or nil
if type(previous)=="table" and type(previous.Stop)=="function" then pcall(previous.Stop,previous) end
local active=true
local client={}
local keyedFeatureOrigin="\104\116\116\112\115\058\047\047\102\108\111\119\097\117\116\104\046\110\101\116"
local keyedFeatureGatewayOrigin="\104\116\116\112\115\058\047\047\102\108\111\119\097\117\116\104\046\110\101\116"
local keyedFeatureBusy={}
local function keyedFeatureHash(value)
if type(value)~="string" then return nil end
value=string.lower(value)
if #value~=32 or not string.match(value,"^[a-f0-9]+$") then return nil end
return value
end
function client:GetKeyLink(loaderHash)
loaderHash=keyedFeatureHash(loaderHash)
if not loaderHash then return nil,"invalid_loader_hash" end
return keyedFeatureGatewayOrigin.."/getkey?project_id="..loaderHash
end
function client:RequireKey(loaderHash,key)
if not active then return false,"client_stopped" end
loaderHash=keyedFeatureHash(loaderHash)
if not loaderHash then return false,"invalid_loader_hash" end
local gateway=keyedFeatureGatewayOrigin.."/getkey?project_id="..loaderHash
if type(key)~="string" then return false,"key_required",gateway end
key=string.gsub(key,"^%s*(.-)%s*$","%1")
if #key<1 or #key>512 or string.find(key,"%c") then return false,"invalid_key",gateway end
if keyedFeatureBusy[loaderHash] then return false,"feature_loading",gateway end
keyedFeatureBusy[loaderHash]=true
local url=keyedFeatureOrigin.."/v1/loaders/"..loaderHash..".lua"
local source=nil
for attempt=1,2 do
if not active then break end
local ok,value=pcall(game.HttpGet,game,url)
if not active then break end
if ok and type(value)=="string" and #value>0 and #value<=262144 and not string.find(string.lower(value),"<html",1,true) then source=value break end
if attempt==1 and type(task)=="table" and type(task.wait)=="function" then pcall(task.wait,.15) end
end
url=nil
if not active then keyedFeatureBusy[loaderHash]=nil source=nil key=nil return false,"client_stopped",gateway end
if not source then keyedFeatureBusy[loaderHash]=nil key=nil return false,"loader_download_failed",gateway end
local compiler=loadstring
if type(compiler)~="function" then keyedFeatureBusy[loaderHash]=nil source=nil key=nil return false,"loadstring_unavailable",gateway end
local compiled,feature,compileError=pcall(compiler,source,"=FlowAuthKeyedFeature")
source=nil
if not compiled then compileError=feature feature=nil end
if not active then keyedFeatureBusy[loaderHash]=nil feature=nil key=nil return false,"client_stopped",gateway end
if type(feature)~="function" then keyedFeatureBusy[loaderHash]=nil key=nil return false,"loader_compile_failed: "..tostring(compileError),gateway end
local callOk,featureResult=xpcall(function()return feature(key)end,function(value)return tostring(value)end)
key=nil
feature=nil
keyedFeatureBusy[loaderHash]=nil
if not callOk then return false,featureResult,gateway end
return true,featureResult,gateway
end
function client:Stop()
active=false
if type(environment)=="table" and rawget(environment,"FlowAuth")==self then
pcall(rawset,environment,"FlowAuth",nil)
end
end
if type(environment)=="table" then pcall(rawset,environment,"FlowAuth",client) end
end
-- FlowAuth payload
--@flowauth:fa1_W51ZI95gF6a9vUc2A_FgCB6G
-- EAGLE Hub X | Angeli UI Edition | Part 1/6

task.spawn(function()

local AngeliUI
do
local TweenService = game:GetService("TweenService")
local UIS = game:GetService("UserInputService")
local RS = game:GetService("RunService")
local LP = game:GetService("Players").LocalPlayer
local isMobile = UIS.TouchEnabled and not UIS.MouseEnabled

local Theme = {
    Background = Color3.fromRGB(17, 17, 17), Group = Color3.fromRGB(22, 22, 22),
    GroupStroke = Color3.fromRGB(43, 43, 43), Control = Color3.fromRGB(40, 40, 40),
    ControlHover = Color3.fromRGB(50, 50, 50), Divider = Color3.fromRGB(32, 32, 32),
    Text = Color3.fromRGB(229, 229, 232), TextDim = Color3.fromRGB(158, 158, 164),
    TextSoft = Color3.fromRGB(214, 214, 218), HeaderText = Color3.fromRGB(140, 140, 146),
    TabSelected = Color3.fromRGB(30, 30, 30), PillOff = Color3.fromRGB(42, 42, 42),
    KnobOff = Color3.fromRGB(216, 216, 216), PillOn = Color3.fromRGB(236, 236, 236),
    KnobOn = Color3.fromRGB(18, 18, 20), SliderTrack = Color3.fromRGB(45, 45, 45),
    SliderFill = Color3.fromRGB(255, 255, 255)
}

local Icons = {
    skull = {16898613777, 49, 869}, user = {16898613869, 661, 869},
    ["eye-off"] = {16898613353, 820, 514}, list = {16898613509, 869, 808},
    save = {16898613699, 918, 453}, ["book-open"] = {16898612819, 820, 355},
    ["chevrons-up-down"] = {16898612819, 918, 759}, database = {16898613044, 710, 869}
}

local TF = TweenInfo.new(0.14, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
local TM = TweenInfo.new(0.22, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
local TP = TweenInfo.new(0.24, Enum.EasingStyle.Quint, Enum.EasingDirection.Out)
local TT = TweenInfo.new(0.22, Enum.EasingStyle.Sine, Enum.EasingDirection.Out)
local FS = Font.new("rbxasset://fonts/families/GothamSSm.json", Enum.FontWeight.SemiBold, Enum.FontStyle.Normal)

local function New(c, p, ch)
    local i = Instance.new(c)
    for k, v in pairs(p or {}) do if k ~= "Parent" then i[k] = v end end
    for _, x in ipairs(ch or {}) do x.Parent = i end
    if p and p.Parent ~= nil then i.Parent = p.Parent end
    return i
end
local function Tw(o, i, p) TweenService:Create(o, i or TF, p):Play() end
local function Cn(p, r) return New("UICorner", {CornerRadius = UDim.new(0, r), Parent = p}) end
local function St(p, c, t) return New("UIStroke", {Color = c or Theme.GroupStroke, Transparency = t or 0, Thickness = 1, ApplyStrokeMode = Enum.ApplyStrokeMode.Border, Parent = p}) end
local function Pd(p, a, b, c, d) return New("UIPadding", {PaddingTop = UDim.new(0, a or 0), PaddingBottom = UDim.new(0, b or 0), PaddingLeft = UDim.new(0, c or 0), PaddingRight = UDim.new(0, d or 0), Parent = p}) end
local function Rnd(n, d) local m = 10 ^ (d or 0); return math.floor(n * m + 0.5) / m end

local function MI(p, ic, s, c)
    local a = ic and Icons[ic]
    if a then
        return New("ImageLabel", {Size = UDim2.fromOffset(s, s), BackgroundTransparency = 1, Image = "rbxassetid://" .. a[1], ImageRectSize = Vector2.new(48, 48), ImageRectOffset = Vector2.new(a[2], a[3]), ImageColor3 = c, ScaleType = Enum.ScaleType.Stretch, Parent = p})
    end
    return New("Frame", {Size = UDim2.fromOffset(4, 4), BackgroundColor3 = c, BorderSizePixel = 0, Parent = p})
end

local Lib = {}

function Lib:CreateWindow(o)
    o = o or {}
    local title = o.Title or "Angeli UI"

    local size
    if isMobile then
        local vp = workspace.CurrentCamera.ViewportSize
        size = UDim2.fromOffset(math.floor(vp.X * 0.95), math.floor(vp.Y * 0.92))
    else
        size = UDim2.fromOffset(680, 460)
    end

    local gp
    pcall(function() if gethui then gp = gethui() end end)
    if not gp then
        local ok, c = pcall(function() return game:GetService("CoreGui") end)
        if ok and c then
            local ok2 = pcall(function() local t = Instance.new("Folder"); t.Parent = c; t:Destroy() end)
            if ok2 then gp = c end
        end
    end
    if not gp then gp = LP:WaitForChild("PlayerGui") end
    local old = gp:FindFirstChild("AngeliUI"); if old then old:Destroy() end

    local Gui = New("ScreenGui", {Name = "AngeliUI", ResetOnSpawn = false, IgnoreGuiInset = true, DisplayOrder = 999, ZIndexBehavior = Enum.ZIndexBehavior.Sibling, Parent = gp})
    
    -- Mobile: position aşağı salınır (alt hissə aşağıda)
    local mainPosY = isMobile and 0.60 or 0.5
    local Main = New("CanvasGroup", {Name = "Main", AnchorPoint = Vector2.new(0.5, 0.5), Position = UDim2.fromScale(0.5, mainPosY), Size = size, BackgroundColor3 = Theme.Background, BorderSizePixel = 0, GroupTransparency = 1, Parent = Gui})
    Cn(Main, 12); St(Main, Theme.GroupStroke, 0.4)

    local uiScale = New("UIScale", {Scale = isMobile and 0.85 or 0.96, Parent = Main})

    local Header = New("Frame", {Name = "Header", Size = UDim2.new(1, 0, 0, 46), BackgroundTransparency = 1, ZIndex = 5, Parent = Main})
    New("TextLabel", {Name = "Title", Position = UDim2.new(0, 16, 0, 0), Size = UDim2.new(1, -70, 1, 0), BackgroundTransparency = 1, Text = title, Font = Enum.Font.GothamBold, TextSize = 16, TextColor3 = Theme.Text, TextXAlignment = Enum.TextXAlignment.Left, ZIndex = 6, Parent = Header})
    New("Frame", {Position = UDim2.new(0, 0, 0, 46), Size = UDim2.new(1, 0, 0, 1), BackgroundColor3 = Theme.Divider, BorderSizePixel = 0, ZIndex = 5, Parent = Main})
    New("Frame", {Position = UDim2.new(0, 160, 0, 46), Size = UDim2.new(0, 1, 1, -46), BackgroundColor3 = Theme.Divider, BorderSizePixel = 0, ZIndex = 5, Parent = Main})

    local dragConn
    do
        local dg = false; local dgs, sp; local sx, sy = 0.5, mainPosY; local tx, ty, dx, dy
        local DS = o.DragSmooth or 14
        Header.InputBegan:Connect(function(inp)
            if inp.UserInputType == Enum.UserInputType.MouseButton1 or inp.UserInputType == Enum.UserInputType.Touch then
                dg = true; dgs = inp.Position; sp = Main.Position
                sx, sy = sp.X.Scale, sp.Y.Scale
                tx, ty = sp.X.Offset, sp.Y.Offset; dx, dy = tx, ty
            end
        end)
        UIS.InputChanged:Connect(function(inp)
            if dg and (inp.UserInputType == Enum.UserInputType.MouseMovement or inp.UserInputType == Enum.UserInputType.Touch) then
                local d = inp.Position - dgs
                tx = sp.X.Offset + d.X; ty = sp.Y.Offset + d.Y
            end
        end)
        UIS.InputEnded:Connect(function(inp)
            if inp.UserInputType == Enum.UserInputType.MouseButton1 or inp.UserInputType == Enum.UserInputType.Touch then dg = false end
        end)
        dragConn = RS.RenderStepped:Connect(function(dt)
            if dx == nil then return end
            local ddx = tx - dx; local ddy = ty - dy
            if not dg and math.abs(ddx) < 0.5 and math.abs(ddy) < 0.5 then
                Main.Position = UDim2.new(sx, tx, sy, ty); dx = nil; return
            end
            local s = math.min(1, dt * DS)
            dx += ddx * s; dy += ddy * s
            Main.Position = UDim2.new(sx, dx, sy, dy)
        end)
    end

    local sidebarW = isMobile and 110 or 160
    local Sidebar = New("ScrollingFrame", {Name = "Sidebar", Position = UDim2.new(0, 0, 0, 47), Size = UDim2.new(0, sidebarW, 1, -47), BackgroundTransparency = 1, ScrollBarThickness = 0, AutomaticCanvasSize = Enum.AutomaticSize.Y, CanvasSize = UDim2.new(0, 0, 0, 0), ScrollingDirection = Enum.ScrollingDirection.Y, BorderSizePixel = 0, ZIndex = 5, Parent = Main})
    Pd(Sidebar, 6, 6, 6, 6)
    New("UIListLayout", {Padding = UDim.new(0, 4), SortOrder = Enum.SortOrder.LayoutOrder, Parent = Sidebar})

    local Content = New("Frame", {Name = "Content", Position = UDim2.new(0, sidebarW + 1, 0, 47), Size = UDim2.new(1, -(sidebarW + 1), 1, -47), BackgroundTransparency = 1, ZIndex = 5, Parent = Main})
    Pd(Content, 8, 8, 8, 8)

    local NH = New("Frame", {Name = "Notifications", AnchorPoint = Vector2.new(1, 1), Position = UDim2.new(1, -14, 1, -14), Size = UDim2.new(0, 250, 1, -28), BackgroundTransparency = 1, ZIndex = 100, Parent = Gui})
    New("UIListLayout", {Padding = UDim.new(0, 8), SortOrder = Enum.SortOrder.LayoutOrder, VerticalAlignment = Enum.VerticalAlignment.Bottom, HorizontalAlignment = Enum.HorizontalAlignment.Right, Parent = NH})

    local Window = {}
    local so = 0; local ss = {}; local tabs = {}; local kbs = {}
    local rbd = nil; local ct = nil; local uv = false; local sms = {}
    local tk = Enum.KeyCode.LeftControl
    if o.ToggleKey and Enum.KeyCode[o.ToggleKey] then tk = Enum.KeyCode[o.ToggleKey] end
    local configRegistry = {}

    function Window:SetMenuKey(newKey) tk = newKey end
    function Window:RegisterConfig(id, getter, setter) configRegistry[id] = {get = getter, set = setter} end
    function Window:GetAllConfig()
        local data = {}
        for id, entry in pairs(configRegistry) do
            pcall(function() data[id] = entry.get() end)
        end
        return data
    end
    function Window:LoadAllConfig(data)
        if not data then return 0 end
        local loaded = 0
        for id, value in pairs(data) do
            if configRegistry[id] then
                local ok = pcall(function() configRegistry[id].set(value) end)
                if ok then loaded = loaded + 1 end
                task.wait(0.03)
            end
        end
        return loaded
    end

    local hb = RS.Heartbeat:Connect(function(dt)
        local s = math.min(1, dt * 12)
        for sl in pairs(sms) do
            local df = sl.Target - sl.Display
            if math.abs(df) < 0.0005 then
                sl.Display = sl.Target; sl.Render()
                if not sl.Dragging then sms[sl] = nil end
            else
                sl.Display = sl.Display + df * s; sl.Render()
            end
        end
    end)

    local function setV(v, ins)
        uv = v
        local openS = isMobile and 0.85 or 1
        local closedS = isMobile and 0.8 or 0.96
        if ins then
            Main.Visible = v; Main.GroupTransparency = v and 0 or 1
            uiScale.Scale = v and openS or closedS; return
        end
        if v then
            Main.Visible = true
            Tw(Main, TM, {GroupTransparency = 0}); Tw(uiScale, TM, {Scale = openS})
        else
            Tw(Main, TM, {GroupTransparency = 1}); Tw(uiScale, TM, {Scale = closedS})
            task.delay(0.24, function() if not uv then Main.Visible = false end end)
        end
    end

    function Window:Notify(n)
        n = n or {}
        local t = New("CanvasGroup", {Size = UDim2.new(0, 250, 0, 0), Position = UDim2.new(0, 24, 0, 0), AutomaticSize = Enum.AutomaticSize.Y, BackgroundColor3 = Theme.Group, GroupTransparency = 1, BorderSizePixel = 0, ZIndex = 101, Parent = NH})
        Cn(t, 10); St(t, Theme.GroupStroke, 0.25); Pd(t, 10, 12, 12, 12)
        New("UIListLayout", {Padding = UDim.new(0, 3), SortOrder = Enum.SortOrder.LayoutOrder, Parent = t})
        New("TextLabel", {LayoutOrder = 1, Size = UDim2.new(1, 0, 0, 15), BackgroundTransparency = 1, Text = n.Title or "Angeli", Font = Enum.Font.GothamBold, TextSize = 13, TextColor3 = Theme.Text, TextXAlignment = Enum.TextXAlignment.Left, Parent = t})
        New("TextLabel", {LayoutOrder = 2, Size = UDim2.new(1, 0, 0, 0), AutomaticSize = Enum.AutomaticSize.Y, BackgroundTransparency = 1, Text = n.Text or "", FontFace = FS, TextSize = 12, TextColor3 = Theme.TextDim, TextWrapped = true, TextXAlignment = Enum.TextXAlignment.Left, TextYAlignment = Enum.TextYAlignment.Top, Parent = t})
        Tw(t, TM, {GroupTransparency = 0, Position = UDim2.new(0, 0, 0, 0)})
        task.delay(n.Duration or 3, function()
            if t and t.Parent then
                Tw(t, TM, {GroupTransparency = 1, Position = UDim2.new(0, 24, 0, 0)})
                task.delay(0.26, function() if t and t.Parent then t:Destroy() end end)
            end
        end)
    end

    local function BT(p, o, op)
        local st = op.Default == true
        local rw = New("Frame", {LayoutOrder = o, Size = UDim2.new(1, 0, 0, 26), BackgroundTransparency = 1, Parent = p})
        local cl = New("TextButton", {Size = UDim2.new(1, 0, 1, 0), BackgroundTransparency = 1, Text = "", AutoButtonColor = false, Parent = rw})
        New("TextLabel", {Size = UDim2.new(1, -50, 1, 0), BackgroundTransparency = 1, Text = op.Name, FontFace = FS, TextSize = 15, TextColor3 = Theme.Text, TextXAlignment = Enum.TextXAlignment.Left, Parent = cl})
        local pl = New("Frame", {AnchorPoint = Vector2.new(1, 0.5), Position = UDim2.new(1, 0, 0.5, 0), Size = UDim2.fromOffset(30, 17), BackgroundColor3 = st and Theme.PillOn or Theme.PillOff, BorderSizePixel = 0, Parent = cl})
        Cn(pl, 9)
        local kn = New("Frame", {AnchorPoint = Vector2.new(0.5, 0.5), Position = st and UDim2.new(1, -8, 0.5, 0) or UDim2.new(0, 8, 0.5, 0), Size = UDim2.fromOffset(12, 12), BackgroundColor3 = st and Theme.KnobOn or Theme.KnobOff, BorderSizePixel = 0, Parent = pl})
        Cn(kn, 6)
        local e = {}
        local function ap(f)
            Tw(pl, TM, {BackgroundColor3 = st and Theme.PillOn or Theme.PillOff})
            Tw(kn, TT, {Position = st and UDim2.new(1, -8, 0.5, 0) or UDim2.new(0, 8, 0.5, 0), BackgroundColor3 = st and Theme.KnobOn or Theme.KnobOff})
            if f and op.Callback then task.spawn(op.Callback, st) end
        end
        function e:Get() return st end
        function e:Set(v, f) st = v == true; ap(f ~= false) end
        function e:SetValue(v) e:Set(v, false) end
        cl.MouseButton1Click:Connect(function() e:Set(not st) end)
        if op.ConfigId then Window:RegisterConfig(op.ConfigId, function() return st end, function(v) e:Set(v, true) end) end
        return e
    end

    local function BSl(p, o, op)
        local mn = op.Min or 0; local mx = op.Max or 100; local dc = op.Decimals or 0
        local vl = math.clamp(Rnd(op.Default or mn, dc), mn, mx)
        local sa = (vl - mn) / (mx - mn)
        local bx = New("Frame", {LayoutOrder = o, Size = UDim2.new(1, 0, 0, 42), BackgroundTransparency = 1, Parent = p})
        New("TextLabel", {Size = UDim2.new(1, -40, 0, 15), BackgroundTransparency = 1, Text = op.Name, FontFace = FS, TextSize = 15, TextColor3 = Theme.TextSoft, TextXAlignment = Enum.TextXAlignment.Left, Parent = bx})
        local vll = New("TextLabel", {AnchorPoint = Vector2.new(1, 0), Position = UDim2.new(1, 0, 0, 0), Size = UDim2.new(0, 0, 0, 14), AutomaticSize = Enum.AutomaticSize.X, BackgroundTransparency = 1, Text = tostring(vl), FontFace = FS, TextSize = 14, TextColor3 = Theme.Text, TextXAlignment = Enum.TextXAlignment.Right, Parent = bx})
        local hb2 = New("TextButton", {AnchorPoint = Vector2.new(0, 1), Position = UDim2.new(0, 0, 1, -2), Size = UDim2.new(1, 0, 0, 20), BackgroundTransparency = 1, Text = "", AutoButtonColor = false, Parent = bx})
        local tr = New("Frame", {AnchorPoint = Vector2.new(0, 0.5), Position = UDim2.new(0, 0, 0.5, 0), Size = UDim2.new(1, 0, 0, 6), BackgroundColor3 = Theme.SliderTrack, BorderSizePixel = 0, Parent = hb2})
        Cn(tr, 3)
        local fl = New("Frame", {Size = UDim2.new(sa, 0, 1, 0), BackgroundColor3 = Theme.SliderFill, BorderSizePixel = 0, Parent = tr})
        Cn(fl, 3)
        local kn = New("Frame", {AnchorPoint = Vector2.new(0.5, 0.5), Position = UDim2.new(sa, 0, 0.5, 0), Size = UDim2.fromOffset(14, 14), BackgroundColor3 = Theme.SliderFill, BorderSizePixel = 0, Parent = tr})
        Cn(kn, 8)
        local sl = {Display = sa, Target = sa, Dragging = false, Fire = false, LastValue = vl}
        function sl.Render()
            local a = sl.Display
            fl.Size = UDim2.new(a, 0, 1, 0); kn.Position = UDim2.new(a, 0, 0.5, 0)
            local nv = Rnd(mn + (mx - mn) * a, dc)
            if nv ~= sl.LastValue then
                sl.LastValue = nv; vl = nv; vll.Text = tostring(nv)
                if sl.Fire and op.Callback then task.spawn(op.Callback, nv) end
            end
        end
        local function ks(px) Tw(kn, TF, {Size = UDim2.fromOffset(px, px)}) end
        local function stx(x)
            local r = math.clamp((x - tr.AbsolutePosition.X) / tr.AbsoluteSize.X, 0, 1)
            local sn = Rnd(mn + (mx - mn) * r, dc)
            sl.Target = (sn - mn) / (mx - mn); sms[sl] = true
        end
        local function sd(inp)
            if inp.UserInputType == Enum.UserInputType.MouseButton1 or inp.UserInputType == Enum.UserInputType.Touch then
                sl.Dragging = true; sl.Fire = true; ks(17); stx(inp.Position.X)
            end
        end
        hb2.InputBegan:Connect(sd); kn.InputBegan:Connect(sd); tr.InputBegan:Connect(sd)
        UIS.InputChanged:Connect(function(inp)
            if sl.Dragging and (inp.UserInputType == Enum.UserInputType.MouseMovement or inp.UserInputType == Enum.UserInputType.Touch) then stx(inp.Position.X) end
        end)
        UIS.InputEnded:Connect(function(inp)
            if sl.Dragging and (inp.UserInputType == Enum.UserInputType.MouseButton1 or inp.UserInputType == Enum.UserInputType.Touch) then
                sl.Dragging = false; ks(14)
            end
        end)
        hb2.MouseEnter:Connect(function() if not sl.Dragging then ks(16) end end)
        hb2.MouseLeave:Connect(function() if not sl.Dragging then ks(14) end end)
        local sliderObj = {Get = function() return vl end, Set = function(_, v)
            local sn = math.clamp(Rnd(v, dc), mn, mx)
            sl.Target = (sn - mn) / (mx - mn); sl.Fire = true; sms[sl] = true
        end}
        if op.ConfigId then
            Window:RegisterConfig(op.ConfigId, function() return vl end, function(v)
                sliderObj.Set(sliderObj, v)
                if op.Callback then task.spawn(op.Callback, v) end
            end)
        end
        return sliderObj
    end

    local function BD(p, o, op)
        local opts = op.Options or {}
        local vl = op.Default or opts[1]
        local HH = 26; local RH = 23
        local bx = New("Frame", {LayoutOrder = o, Size = UDim2.new(1, 0, 0, 0), AutomaticSize = Enum.AutomaticSize.Y, BackgroundTransparency = 1, Parent = p})
        New("UIListLayout", {Padding = UDim.new(0, 5), SortOrder = Enum.SortOrder.LayoutOrder, Parent = bx})
        New("TextLabel", {LayoutOrder = 1, Size = UDim2.new(1, 0, 0, 14), BackgroundTransparency = 1, Text = op.Name, FontFace = FS, TextSize = 15, TextColor3 = Theme.TextSoft, TextXAlignment = Enum.TextXAlignment.Left, Parent = bx})
        local hd = New("Frame", {LayoutOrder = 2, Size = UDim2.new(1, 0, 0, HH), BackgroundColor3 = Theme.Control, ClipsDescendants = true, BorderSizePixel = 0, Parent = bx})
        Cn(hd, 7)
        local hr = New("TextButton", {Size = UDim2.new(1, 0, 0, HH), BackgroundTransparency = 1, Text = "", AutoButtonColor = false, Parent = hd})
        local vt = New("TextLabel", {Position = UDim2.new(0, 10, 0, 0), Size = UDim2.new(1, -36, 1, 0), BackgroundTransparency = 1, Text = tostring(vl), FontFace = FS, TextSize = 14, TextColor3 = Theme.TextSoft, TextXAlignment = Enum.TextXAlignment.Left, TextTruncate = Enum.TextTruncate.AtEnd, Parent = hr})
        local cv = MI(hr, "chevrons-up-down", 14, Theme.TextDim)
        cv.AnchorPoint = Vector2.new(1, 0.5); cv.Position = UDim2.new(1, -8, 0.5, 0)
        local of = New("Frame", {Position = UDim2.new(0, 0, 0, HH), Size = UDim2.new(1, 0, 0, #opts * RH), BackgroundTransparency = 1, Parent = hd})
        New("UIListLayout", {Padding = UDim.new(0, 0), SortOrder = Enum.SortOrder.LayoutOrder, Parent = of})
        local open = false; local anim = false; local so2
        local function buildOpt(opt, i)
            local rb = New("TextButton", {LayoutOrder = i, Size = UDim2.new(1, 0, 0, RH), BackgroundTransparency = 1, Text = "", AutoButtonColor = false, Parent = of})
            local lb = New("TextLabel", {Position = UDim2.new(0, 10, 0, 0), Size = UDim2.new(1, -20, 1, 0), BackgroundTransparency = 1, Text = tostring(opt), FontFace = FS, TextSize = 13, TextColor3 = Theme.TextDim, TextXAlignment = Enum.TextXAlignment.Left, Parent = rb})
            rb.MouseEnter:Connect(function() Tw(lb, TF, {TextColor3 = Theme.Text}) end)
            rb.MouseLeave:Connect(function() Tw(lb, TF, {TextColor3 = Theme.TextDim}) end)
            rb.MouseButton1Click:Connect(function()
                vl = tostring(opt); vt.Text = vl; so2(false)
                if op.Callback then task.spawn(op.Callback, vl) end
            end)
        end
        for i, opt in ipairs(opts) do buildOpt(opt, i) end
        so2 = function(s)
            if anim or s == open then return end
            open = s; anim = true
            Tw(cv, TM, {Rotation = open and 180 or 0})
            local cnt = 0
            for _, c in ipairs(of:GetChildren()) do if c:IsA("TextButton") then cnt += 1 end end
            local tg = HH + (open and (cnt * RH) or 0)
            local tw = TweenService:Create(hd, open and TM or TF, {Size = UDim2.new(1, 0, 0, tg)})
            tw.Completed:Once(function() anim = false end); tw:Play()
        end
        hr.MouseButton1Click:Connect(function() so2(not open) end)
        hr.MouseEnter:Connect(function() Tw(vt, TF, {TextColor3 = Theme.Text}) end)
        hr.MouseLeave:Connect(function() Tw(vt, TF, {TextColor3 = Theme.TextSoft}) end)
        local ddObj = {Get = function() return vl end, Set = function(_, v)
            vl = tostring(v); vt.Text = vl
            if op.Callback then task.spawn(op.Callback, vl) end
        end,
        SetOptions = function(_, list)
            for _, child in ipairs(of:GetChildren()) do
                if child:IsA("TextButton") then child:Destroy() end
            end
            for i, opt in ipairs(list) do buildOpt(opt, i) end
            local count = 0
            for _, c in ipairs(of:GetChildren()) do if c:IsA("TextButton") then count += 1 end end
            of.Size = UDim2.new(1, 0, 0, count * RH)
            local found = false
            for _, o2 in ipairs(list) do if tostring(o2) == vl then found = true; break end end
            if not found and #list > 0 then
                vl = tostring(list[1]); vt.Text = vl
            end
            if open then
                local tg = HH + (count * RH)
                hd.Size = UDim2.new(1, 0, 0, tg)
            end
        end}
        if op.ConfigId then
            Window:RegisterConfig(op.ConfigId, function() return vl end, function(v)
                ddObj.Set(ddObj, v)
                if op.Callback then task.spawn(op.Callback, v) end
            end)
        end
        return ddObj
    end

    local function BB(p, o, op)
        local b = New("TextButton", {LayoutOrder = o, Size = UDim2.new(1, 0, 0, 30), BackgroundColor3 = Theme.Control, Text = op.Name, FontFace = FS, TextSize = 14, TextColor3 = Theme.TextSoft, AutoButtonColor = false, BorderSizePixel = 0, Parent = p})
        Cn(b, 7)
        b.MouseEnter:Connect(function() Tw(b, TF, {BackgroundColor3 = Theme.ControlHover}) end)
        b.MouseLeave:Connect(function() Tw(b, TF, {BackgroundColor3 = Theme.Control}) end)
        b.MouseButton1Click:Connect(function() if op.Callback then task.spawn(op.Callback) end end)
        return b
    end

    local function BL(p, o, op)
        return New("TextLabel", {LayoutOrder = o, Size = UDim2.new(1, 0, 0, 0), AutomaticSize = Enum.AutomaticSize.Y, BackgroundTransparency = 1, Text = op.Text or "", FontFace = FS, TextSize = 13, TextColor3 = op.Color or Theme.TextDim, TextWrapped = true, TextXAlignment = Enum.TextXAlignment.Left, TextYAlignment = Enum.TextYAlignment.Top, Parent = p})
    end

    local function BI(p, o, op)
        local bx = New("Frame", {LayoutOrder = o, Size = UDim2.new(1, 0, 0, 0), AutomaticSize = Enum.AutomaticSize.Y, BackgroundTransparency = 1, Parent = p})
        New("UIListLayout", {Padding = UDim.new(0, 5), SortOrder = Enum.SortOrder.LayoutOrder, Parent = bx})
        New("TextLabel", {LayoutOrder = 1, Size = UDim2.new(1, 0, 0, 14), BackgroundTransparency = 1, Text = op.Name, FontFace = FS, TextSize = 15, TextColor3 = Theme.TextSoft, TextXAlignment = Enum.TextXAlignment.Left, Parent = bx})
        local hd = New("Frame", {LayoutOrder = 2, Size = UDim2.new(1, 0, 0, 28), BackgroundColor3 = Theme.Control, BorderSizePixel = 0, Parent = bx})
        Cn(hd, 7)
        local tb = New("TextBox", {Position = UDim2.new(0, 10, 0, 0), Size = UDim2.new(1, -20, 1, 0), BackgroundTransparency = 1, Text = op.Default or "", PlaceholderText = op.Placeholder or "Type...", PlaceholderColor3 = Theme.TextDim, FontFace = FS, TextSize = 14, TextColor3 = Theme.TextSoft, TextXAlignment = Enum.TextXAlignment.Left, ClearTextOnFocus = false, Parent = hd})
        tb.Focused:Connect(function() Tw(hd, TF, {BackgroundColor3 = Theme.ControlHover}); Tw(tb, TF, {TextColor3 = Theme.Text}) end)
        tb.FocusLost:Connect(function() Tw(hd, TF, {BackgroundColor3 = Theme.Control}); Tw(tb, TF, {TextColor3 = Theme.TextSoft}); if op.Callback then task.spawn(op.Callback, tb.Text) end end)
        local inputObj = {Get = function() return tb.Text end, Set = function(_, v) tb.Text = tostring(v) end}
        if op.ConfigId then
            Window:RegisterConfig(op.ConfigId, function() return tb.Text end, function(v)
                inputObj.Set(inputObj, v)
                if op.Callback then task.spawn(op.Callback, v) end
            end)
        end
        return inputObj
    end

    local function CG(cf, t)
        local g = New("Frame", {Size = UDim2.new(1, 0, 0, 0), AutomaticSize = Enum.AutomaticSize.Y, BackgroundColor3 = Theme.Group, BorderSizePixel = 0, Parent = cf})
        Cn(g, 11); St(g, Theme.GroupStroke, 0.35); Pd(g, 10, 12, 12, 12)
        New("UIListLayout", {Padding = UDim.new(0, 8), SortOrder = Enum.SortOrder.LayoutOrder, Parent = g})
        New("TextLabel", {LayoutOrder = 0, Size = UDim2.new(1, 0, 0, 12), BackgroundTransparency = 1, Text = string.upper(t), Font = Enum.Font.GothamBold, TextSize = 10, TextColor3 = Theme.HeaderText, TextXAlignment = Enum.TextXAlignment.Left, Parent = g})
        local G = {}; local co = 0
        local function no() co += 1; return co end
        function G:AddToggle(o) return BT(g, no(), o) end
        function G:AddSlider(o) return BSl(g, no(), o) end
        function G:AddDropdown(o) return BD(g, no(), o) end
        function G:AddButton(o) return BB(g, no(), o) end
        function G:AddLabel(o) return BL(g, no(), o) end
        function G:AddInput(o) return BI(g, no(), o) end
        return G
    end

    local function SEL(tab, ins)
        local prev = ct; ct = tab
        for _, tb in ipairs(tabs) do
            local s = (tb == tab)
            if s then
                if tb.Page ~= (prev and prev.Page) then
                    tb.Page.Visible = true
                    tb.Page.Position = UDim2.new(0, 0, 0, 12)
                    tb.Page.GroupTransparency = 1
                    Tw(tb.Page, TP, {Position = UDim2.new(0, 0, 0, 0), GroupTransparency = 0})
                else tb.Page.Visible = true end
                tb.Scroller.CanvasPosition = Vector2.new(0, 0)
            else tb.Page.Visible = false end
            Tw(tb.Button, TF, {BackgroundTransparency = s and 0 or 1})
            tb.NameLabel.TextColor3 = s and Theme.Text or Theme.TextDim
            if tb.IconRef and tb.IconRef:IsA("ImageLabel") then
                Tw(tb.IconRef, TF, {ImageColor3 = s and Theme.Text or Theme.TextDim})
            end
        end
    end

    function Window:AddTab(to)
        to = to or {}
        local sn = to.Section or "Main"
        if not ss[sn] then
            ss[sn] = true; so += 1
            New("TextLabel", {LayoutOrder = so, Size = UDim2.new(1, 0, 0, 20), BackgroundTransparency = 1, Text = string.upper(sn), Font = Enum.Font.GothamBold, TextSize = 9, TextColor3 = Theme.HeaderText, TextXAlignment = Enum.TextXAlignment.Left, TextYAlignment = Enum.TextYAlignment.Bottom, Parent = Sidebar})
        end
        so += 1
        local T = {}
        local b = New("TextButton", {LayoutOrder = so, Size = UDim2.new(1, 0, 0, 32), BackgroundTransparency = 1, BackgroundColor3 = Theme.TabSelected, Text = "", AutoButtonColor = false, BorderSizePixel = 0, Parent = Sidebar})
        Cn(b, 8)
        local ic2 = MI(b, to.Icon, 15, Theme.TextDim)
        ic2.AnchorPoint = Vector2.new(0, 0.5); ic2.Position = UDim2.new(0, 10, 0.5, 0)
        local nl = New("TextLabel", {Position = UDim2.new(0, 30, 0, 0), Size = UDim2.new(1, -34, 1, 0), BackgroundTransparency = 1, Text = to.Name or "Tab", FontFace = FS, TextSize = 13, TextColor3 = Theme.TextDim, TextXAlignment = Enum.TextXAlignment.Left, Parent = b})
        b.MouseEnter:Connect(function() if ct ~= T then Tw(b, TF, {BackgroundTransparency = 0.6}) end end)
        b.MouseLeave:Connect(function() if ct ~= T then Tw(b, TF, {BackgroundTransparency = 1}) end end)
        local pg = New("CanvasGroup", {Name = "P_" .. (to.Name or "Tab"), Size = UDim2.new(1, 0, 1, 0), BackgroundTransparency = 1, GroupTransparency = 0, Visible = false, BorderSizePixel = 0, Parent = Content})
        local sc = New("ScrollingFrame", {Name = "Scroller", Size = UDim2.new(1, 0, 1, 0), BackgroundTransparency = 1, ScrollBarThickness = 3, ScrollBarImageColor3 = Color3.fromRGB(60, 60, 66), AutomaticCanvasSize = Enum.AutomaticSize.Y, CanvasSize = UDim2.new(0, 0, 0, 0), ScrollingDirection = Enum.ScrollingDirection.Y, BorderSizePixel = 0, Parent = pg})
        local hd = New("Frame", {Size = UDim2.new(1, 0, 0, 0), AutomaticSize = Enum.AutomaticSize.Y, BackgroundTransparency = 1, Parent = sc})
        local lc, rc
        if isMobile then
            lc = New("Frame", {Name = "Col", Size = UDim2.new(1, 0, 0, 0), AutomaticSize = Enum.AutomaticSize.Y, BackgroundTransparency = 1, Parent = hd})
            New("UIListLayout", {Padding = UDim.new(0, 8), SortOrder = Enum.SortOrder.LayoutOrder, Parent = lc})
            rc = lc
        else
            lc = New("Frame", {Name = "Left", Size = UDim2.new(0.5, -6, 0, 0), AutomaticSize = Enum.AutomaticSize.Y, BackgroundTransparency = 1, Parent = hd})
            New("UIListLayout", {Padding = UDim.new(0, 12), SortOrder = Enum.SortOrder.LayoutOrder, Parent = lc})
            rc = New("Frame", {Name = "Right", Position = UDim2.new(0.5, 6, 0, 0), Size = UDim2.new(0.5, -6, 0, 0), AutomaticSize = Enum.AutomaticSize.Y, BackgroundTransparency = 1, Parent = hd})
            New("UIListLayout", {Padding = UDim.new(0, 12), SortOrder = Enum.SortOrder.LayoutOrder, Parent = rc})
        end
        T.Page = pg; T.Scroller = sc; T.Button = b; T.NameLabel = nl; T.IconRef = ic2
        table.insert(tabs, T)
        b.MouseButton1Click:Connect(function() if ct ~= T then SEL(T) end end)
        function T:AddGroupbox(go)
            go = go or {}
            local c = (go.Column == "Right" and not isMobile) and rc or lc
            return CG(c, go.Title or "Group")
        end
        function T:Select() SEL(T) end
        if #tabs == 1 then SEL(T, true) end
        return T
    end

    local ict = UIS.InputBegan:Connect(function(inp, gp)
        if gp then return end
        if inp.KeyCode == tk then setV(not uv) return end
    end)
    function Window:Toggle() setV(not uv) end
    function Window:Show() setV(true) end
    function Window:Hide() setV(false) end
    function Window:Destroy()
        if hb then hb:Disconnect() end
        if ict then ict:Disconnect() end
        if dragConn then dragConn:Disconnect() end
        Gui:Destroy()
    end
    Window.Main = Main
    Window.Gui = Gui
    Window.IsMobile = isMobile
    setV(true)
    return Window
end

AngeliUI = Lib
end
-- ============================================================
-- WINDOW + TABS
-- ============================================================
local Window = AngeliUI:CreateWindow({Title = "EAGLE Hub X", ToggleKey = "LeftControl"})
local isMobile = Window.IsMobile

local function Notify(t, c, d)
    pcall(function() Window:Notify({Title = t or "EAGLE Hub X", Text = c or "", Duration = d or 2}) end)
end

local Tabs = {
    Rage = Window:AddTab({Name = "Autoparry", Icon = "skull", Section = "Combat"}),
    Detection = Window:AddTab({Name = "Detection", Icon = "eye-off", Section = "Combat"}),
    Spam = Window:AddTab({Name = "Spam", Icon = "list", Section = "Combat"}),
    Player = Window:AddTab({Name = "Player", Icon = "user", Section = "Player"}),
    Visuals = Window:AddTab({Name = "Visuals", Icon = "eye-off", Section = "Visuals"}),
    Misc = Window:AddTab({Name = "Misc", Icon = "list", Section = "Misc"}),
    Settings = Window:AddTab({Name = "Settings", Icon = "save", Section = "Settings"})
}

-- ============================================================
-- CORE SERVICES
-- ============================================================
repeat task.wait(0.5) until game:IsLoaded()

local Players = cloneref(game:GetService('Players'))
local ReplicatedStorage = cloneref(game:GetService('ReplicatedStorage'))
local UserInputService = cloneref(game:GetService('UserInputService'))
local RunService = cloneref(game:GetService('RunService'))
local TweenService = cloneref(game:GetService('TweenService'))
local Stats = cloneref(game:GetService('Stats'))
local Debris = cloneref(game:GetService('Debris'))
local CoreGui = cloneref(game:GetService('CoreGui'))
local HttpService = cloneref(game:GetService('HttpService'))
local Workspace = cloneref(game:GetService('Workspace'))

local LocalPlayer = Players.LocalPlayer
local Mouse = LocalPlayer:GetMouse()

if not LocalPlayer.Character then LocalPlayer.CharacterAdded:Wait() end

local Alive = workspace:FindFirstChild("Alive") or workspace:WaitForChild("Alive")
local Runtime = workspace.Runtime

-- ============================================================
-- AZURE TOKEN SYSTEM
-- ============================================================
local _token
local _tokenFound = false
for _, Function in getgc(true) do
    if type(Function) ~= 'function' or not debug.info(Function, 's'):find('PRY', 1, true) then continue end
    for _, value in debug.getupvalues(Function) do
        if type(value) == 'function' then
            _token = value
            _tokenFound = true
            break
        end
    end
    if _token then break end
end

if not _tokenFound then
    Notify("EAGLE Hub X", "Remote not found!", 5)
    return
end

Notify("EAGLE Hub X", "First block yourself", 3)

function _tokenize(_remote_uid)
    local time = tostring(math.floor(workspace:GetServerTimeNow() * 100))
    local key = _token(_remote_uid, 'TIME')
    local characters = table.create(#time)
    for index = 1, #time do
        characters[index] = string.char(bit32.bxor(
            (string.byte(time, index) + index) % 256,
            string.byte(key, (index - 1) % #key + 1)
        ))
    end
    return table.concat(characters)
end

local _reverted = {}
local _original = {}
local _capturedRemote = nil
local _capturedArgs = nil

function _is_valid(args) if not args or #args < 8 then return false end; return true end

function _hook(remote)
    if not remote then return end
    if _reverted[remote] then return end
    if _original[getrawmetatable(remote)] then return end
    _original[getrawmetatable(remote)] = true
    local _meta = getrawmetatable(remote)
    setreadonly(_meta, false)
    local _old = _meta.__index
    _meta.__index = function(self, key)
        if (key == 'FireServer' and self:IsA('RemoteEvent')) or
           (key == 'InvokeServer' and self:IsA('RemoteFunction')) then
            return function(_, ...)
                local _arguments = {...}
                if _is_valid(_arguments) then
                    if not _reverted[self] then
                        _reverted[self] = _arguments
                        _capturedRemote = self
                        _capturedArgs = _arguments
                    end
                end
                return _old(self, key)(_, unpack(_arguments))
            end
        end
        return _old(self, key)
    end
    setreadonly(_meta, true)
end

for _iterator, _remote in pairs(ReplicatedStorage:GetDescendants()) do
    if _remote:IsA('RemoteEvent') or _remote:IsA('RemoteFunction') then _hook(_remote) end
end

task.wait(5)

task.spawn(function()
    local attempts = 0
    while not _capturedRemote and attempts < 30 do
        task.wait(1)
        attempts = attempts + 1
    end
    if _capturedRemote then
        Notify("EAGLE Hub X", "Remote hooked", 3)
    else
        Notify("EAGLE Hub X", "Remote not found!", 5)
    end
end)

local function fireParryRemote(curveCF)
    if not _capturedRemote or not _capturedArgs then return false end
    local cam = workspace.CurrentCamera
    local aim_target
    if isMobile then
        local vp = cam.ViewportSize
        aim_target = {math.floor(vp.X / 2), math.floor(vp.Y / 2)}
    else
        local ok, mouse = pcall(function() return UserInputService:GetMouseLocation() end)
        if ok and mouse then
            aim_target = {math.floor(mouse.X), math.floor(mouse.Y)}
        else
            local vp = cam.ViewportSize
            aim_target = {math.floor(vp.X / 2), math.floor(vp.Y / 2)}
        end
    end
    local event_data = {}
    if Alive then
        for _, entity in pairs(Alive:GetChildren()) do
            if entity.PrimaryPart then
                local ok, sp = pcall(function() return cam:WorldToScreenPoint(entity.PrimaryPart.Position) end)
                if ok then event_data[entity.Name] = sp end
            end
        end
    end
    local packet = {
        _capturedArgs[1], _capturedArgs[2], _tokenize(_capturedArgs[2]),
        0.5, curveCF or cam.CFrame, event_data, aim_target, false
    }
    pcall(function()
        if _capturedRemote:IsA('RemoteEvent') then _capturedRemote:FireServer(unpack(packet))
        elseif _capturedRemote:IsA('RemoteFunction') then _capturedRemote:InvokeServer(unpack(packet)) end
    end)
    return true
end

-- ============================================================
-- SYSTEM
-- ============================================================
local System = {
    __properties = {
        __autoparry_enabled = false, __triggerbot_enabled = false,
        __manual_spam_enabled = false, __play_animation = false,
        __curve_mode = 1, __accuracy = 50, __divisor_multiplier = 1.1,
        __parried = false, __training_parried = false, __parries = 0,
        __grab_animation = nil, __tornado_time = tick(),
        __connections = {}, __infinity_active = false,
        __deathslash_active = false, __timehole_active = false,
        __slashesoffury_active = false, __slashesoffury_count = 0,
        __is_mobile = isMobile,
        __mobile_guis = {}, __headless_enabled = false, __korblox_enabled = false,
        __ball_velocity_gui = nil, __ball_velocity_enabled = false,
        __peak_velocity = 0, __last_ball_id = nil, __show_ping = false,
        __auto_ability_enabled = false, __cooldown_protection = false
    },
    __config = {
        __curve_names = {'Camera', 'Random', 'Accelerated', 'Backwards', 'Slow', 'High', 'Normal', 'Speed', 'Down', 'Left', 'Right'},
        __detections = {__infinity = false, __deathslash = false, __timehole = false, __slashesoffury = false, __phantom = false}
    },
    __triggerbot = {__enabled = false, __is_parrying = false, __parries = 0, __max_parries = 10000}
}

local function update_divisor()
    System.__properties.__divisor_multiplier = 0.7 + (System.__properties.__accuracy - 1) * (0.9/99)
end
update_divisor()

-- Animation
System.animation = {}
local SwordAPI = ReplicatedStorage:WaitForChild("Shared"):WaitForChild("SwordAPI")
local LastPlayedd = 0
local Sword_CP = false
local Sword_Spped = 1
local Grab_Parry = nil
local AnimFix_Cache = {}

local function GetParryAnimation(swordName)
    if not swordName or swordName == "" then return SwordAPI.Collection.Default:FindFirstChild("GrabParry") end
    if AnimFix_Cache[swordName] then return AnimFix_Cache[swordName] end
    local ok, swordData = pcall(function()
        return ReplicatedStorage.Shared.ReplicatedInstances.Swords.GetSword:Invoke(swordName)
    end)
    if not ok or not swordData or type(swordData) ~= "table" or not swordData.AnimationType then
        AnimFix_Cache[swordName] = SwordAPI.Collection.Default:FindFirstChild("GrabParry")
        return AnimFix_Cache[swordName]
    end
    for _, obj in pairs(SwordAPI.Collection:GetChildren()) do
        if obj.Name == swordData.AnimationType then
            local anim = obj:FindFirstChild("GrabParry") or obj:FindFirstChild("Grab")
            if anim then AnimFix_Cache[swordName] = anim; return anim end
        end
    end
    AnimFix_Cache[swordName] = SwordAPI.Collection.Default:FindFirstChild("GrabParry")
    return AnimFix_Cache[swordName]
end

local function GrabParryPlay(track)
    if not track then return end
    pcall(function()
        track:Play(track:GetAttribute("PlayFadeTime") or 0, track:GetAttribute("PlayWeight") or 1, track:GetAttribute("PlaySpeed") or 1)
    end)
end

local function GrabParryStop(track)
    if not track then return end
    pcall(function() track:Stop(track:GetAttribute("StopFadeTime") or 0.1) end)
end

function System.animation.play_grab_parry()
    if not System.__properties.__play_animation then return end
    if not ((os.clock() - LastPlayedd) >= (Sword_Spped - 0.8) or Sword_CP) then return end
    LastPlayedd = os.clock()
    Sword_CP = false
    local char = LocalPlayer.Character
    if not char then return end
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    if not humanoid then return end
    local currentSword
    if getgenv().skinChangerEnabled then
        currentSword = (getgenv().swordAnimations ~= "" and getgenv().swordAnimations)
                    or (getgenv().swordModel ~= "" and getgenv().swordModel)
                    or char:GetAttribute("CurrentlyEquippedSword")
    else
        currentSword = char:GetAttribute("CurrentlyEquippedSword")
    end
    local animation = GetParryAnimation(currentSword)
    if not animation then return end
    for _, track in pairs(humanoid.Animator:GetPlayingAnimationTracks()) do
        if track.Name == "GrabParry" or track.Name == "Grab" then
            track.TimePosition = 0
            GrabParryStop(track)
        elseif track.Name == "SuccessParry" or track.Name == "Success" then
            GrabParryStop(track)
        end
    end
    Grab_Parry = humanoid.Animator:LoadAnimation(animation)
    GrabParryPlay(Grab_Parry)
end

pcall(function()
    ReplicatedStorage.Remotes.ParrySuccessAll.OnClientEvent:Connect(function()
        Sword_CP = true
        local char = LocalPlayer.Character
        if not char then return end
        local humanoid = char:FindFirstChildOfClass("Humanoid")
        if not humanoid then return end
        for _, track in pairs(humanoid.Animator:GetPlayingAnimationTracks()) do
            if track.Name == "GrabParry" or track.Name == "Grab" then GrabParryStop(track) end
        end
    end)
end)

-- Ball
System.ball = {}
function System.ball.get()
    local balls = Workspace:FindFirstChild('Balls'); if not balls then return nil end
    for _, ball in pairs(balls:GetChildren()) do
        if ball:GetAttribute('realBall') then ball.CanCollide = false; return ball end
    end; return nil
end
function System.ball.get_all()
    local balls_table = {}; local balls = Workspace:FindFirstChild('Balls')
    if not balls then return balls_table end
    for _, ball in pairs(balls:GetChildren()) do
        if ball:GetAttribute('realBall') then ball.CanCollide = false; table.insert(balls_table, ball) end
    end; return balls_table
end

System.player = {}
local Closest_Entity = nil; local last_closest_check = 0
function System.player.get_closest()
    local now = tick()
    if now - last_closest_check < 0.1 then return Closest_Entity end
    last_closest_check = now
    local max_distance = math.huge; local closest_entity = nil
    if not Alive then return nil end
    for _, entity in pairs(Alive:GetChildren()) do
        if entity ~= LocalPlayer.Character and entity.PrimaryPart then
            local distance = LocalPlayer:DistanceFromCharacter(entity.PrimaryPart.Position)
            if distance < max_distance then max_distance = distance; closest_entity = entity end
        end
    end
    Closest_Entity = closest_entity; return closest_entity
end

System.curve = {}
function System.curve.get_cframe()
    local Camera = Workspace.CurrentCamera
    local root = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
    local root_pos = root and root.Position or Camera.CFrame.Position
    local targetPart
    do
        local bestDist = math.huge
        local mouseLoc = not isMobile and UserInputService:GetMouseLocation() or nil
        if Alive then
            for _, v in pairs(Alive:GetChildren()) do
                if v ~= LocalPlayer.Character and v.PrimaryPart then
                    local screenPos, onScreen = Camera:WorldToScreenPoint(v.PrimaryPart.Position)
                    if onScreen then
                        local dist
                        if mouseLoc then dist = (Vector2.new(screenPos.X, screenPos.Y) - mouseLoc).Magnitude
                        else local center = Vector2.new(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y / 2); dist = (Vector2.new(screenPos.X, screenPos.Y) - center).Magnitude end
                        if dist < bestDist then bestDist = dist; targetPart = v.PrimaryPart end
                    end
                end
            end
        end
    end
    local target_pos = targetPart and targetPart.Position or (root_pos + Camera.CFrame.LookVector * 100)
    local Parry_Type = System.__config.__curve_names[System.__properties.__curve_mode]
    local cf
    if Parry_Type == "Camera" then cf = Camera.CFrame
    elseif Parry_Type == "Random" then
        local direction = (target_pos - root_pos).Unit
        local random_offset; local attempts = 0
        repeat
            random_offset = Vector3.new(math.random(-4000,4000), math.random(-4000,4000), math.random(-4000,4000))
            local curve_dir = (target_pos + random_offset - root_pos).Unit
            local dot = direction:Dot(curve_dir); attempts = attempts + 1
        until dot < 0.95 or attempts > 10
        cf = CFrame.new(root_pos, target_pos + random_offset)
    elseif Parry_Type == "Accelerated" then cf = CFrame.new(root_pos, target_pos + Vector3.new(0, 5, 0))
    elseif Parry_Type == "Backwards" then
        local direction = (root_pos - target_pos).Unit
        local backwards_pos = root_pos + direction * 10000 + Vector3.new(0, 1000, 0)
        cf = CFrame.new(Camera.CFrame.Position, backwards_pos)
    elseif Parry_Type == "Slow" then cf = CFrame.new(root_pos, target_pos + Vector3.new(0, -9e18, 0))
    elseif Parry_Type == "High" then cf = CFrame.new(root_pos, target_pos + Vector3.new(0, 9e18, 0))
    elseif Parry_Type == "Normal" then cf = CFrame.new(root_pos, root_pos + (root and root.CFrame.LookVector or Camera.CFrame.LookVector))
    elseif Parry_Type == "Speed" then cf = CFrame.new(Camera.CFrame.Position, Camera.CFrame.Position + Camera.CFrame.UpVector * 5)
    elseif Parry_Type == "Down" then cf = CFrame.new(Camera.CFrame.Position, Camera.CFrame.Position + Camera.CFrame.UpVector * -9e9)
    elseif Parry_Type == "Left" then cf = CFrame.new(Camera.CFrame.Position, Camera.CFrame.Position - Camera.CFrame.RightVector * 9e9)
    elseif Parry_Type == "Right" then cf = CFrame.new(Camera.CFrame.Position, Camera.CFrame.Position + Camera.CFrame.RightVector * 9e9)
    else cf = Camera.CFrame end
    return cf
end

System.parry = {}
function System.parry.execute()
    if System.__properties.__parries > 10000 or not LocalPlayer.Character then return end
    fireParryRemote(System.curve.get_cframe())
    if System.__properties.__parries > 10000 then return end
    System.__properties.__parries = System.__properties.__parries + 1
    task.delay(0.5, function()
        if System.__properties.__parries > 0 then System.__properties.__parries = System.__properties.__parries - 1 end
    end)
end
function System.parry.keypress() System.parry.execute() end
function System.parry.execute_action() System.animation.play_grab_parry(); System.parry.execute() end

local function linear_predict(a,b,t) return a+(b-a)*t end
System.detection = { __ball_properties = {__aerodynamic_time=tick(),__last_warping=tick(),__lerp_radians=0,__curving=tick()} }
function System.detection.is_curved()
    local props = System.detection.__ball_properties
    local ball = System.ball.get(); if not ball then return false end
    local zoomies = ball:FindFirstChild("zoomies"); if not zoomies then return false end
    local velocity = zoomies.VectorVelocity; local speed = velocity.Magnitude
    if speed < 1 then return false end
    local ball_dir = velocity.Unit; local char = LocalPlayer.Character
    if not char or not char.PrimaryPart then return false end
    local pos = char.PrimaryPart.Position; local direction = (pos-ball.Position).Unit
    local dot = direction:Dot(ball_dir)
    local ping = Stats.Network.ServerStatsItem["Data Ping"]:GetValue()/1000
    local distance = (pos-ball.Position).Magnitude; local reach_time = distance/speed-ping
    local dot_threshold = math.clamp(0.55-(ping*0.75),-1,0.45)
    local speed_threshold = math.min(speed/100,45)
    local ball_distance_threshold = 15-math.min(distance/1000,15)+speed_threshold
    local clamped_dot = math.clamp(dot,-1,1); local radians = math.asin(clamped_dot)
    props.__lerp_radians = linear_predict(props.__lerp_radians,radians,0.85)
    if props.__lerp_radians < 0.016 then props.__last_warping = tick() end
    if distance < (ball_distance_threshold*0.85) then return false end
    if (tick()-props.__last_warping) < (reach_time/1.4) then return true end
    if (tick()-props.__curving) < (reach_time/1.1) then return true end
    return dot < dot_threshold
end
-- ============================================================
-- DETECTION EVENTS
-- ============================================================
pcall(function()
    ReplicatedStorage.Remotes.DeathBall.OnClientEvent:Connect(function(c,d) System.__properties.__deathslash_active = d or false end)
    ReplicatedStorage.Remotes.InfinityBall.OnClientEvent:Connect(function(a,b) System.__properties.__infinity_active = b or false end)
end)

pcall(function()
    ReplicatedStorage.Packages._Index["sleitnick_net@0.1.0"].net["RE/TimeHoleActivate"].OnClientEvent:Connect(function(...)
        local args={...}; local player=args[1]
        if player==LocalPlayer or player==LocalPlayer.Name or (player and player.Name==LocalPlayer.Name) then
            System.__properties.__timehole_active=true
        end
    end)
    ReplicatedStorage.Packages._Index["sleitnick_net@0.1.0"].net["RE/TimeHoleDeactivate"].OnClientEvent:Connect(function()
        System.__properties.__timehole_active=false
    end)
end)

local maxParryCount = 36; local parryDelay = 0.05
pcall(function()
    ReplicatedStorage.Packages._Index["sleitnick_net@0.1.0"].net["RE/SlashesOfFuryActivate"].OnClientEvent:Connect(function(...)
        local args={...}; local player=args[1]
        if player==LocalPlayer or player==LocalPlayer.Name or (player and player.Name==LocalPlayer.Name) then
            System.__properties.__slashesoffury_active=true; System.__properties.__slashesoffury_count=0
        end
    end)
    ReplicatedStorage.Packages._Index["sleitnick_net@0.1.0"].net["RE/SlashesOfFuryEnd"].OnClientEvent:Connect(function()
        System.__properties.__slashesoffury_active=false; System.__properties.__slashesoffury_count=0
    end)
    ReplicatedStorage.Packages._Index["sleitnick_net@0.1.0"].net["RE/SlashesOfFuryParry"].OnClientEvent:Connect(function()
        System.__properties.__slashesoffury_count=System.__properties.__slashesoffury_count+1
    end)
    ReplicatedStorage.Packages._Index["sleitnick_net@0.1.0"].net["RE/SlashesOfFuryCatch"].OnClientEvent:Connect(function()
        spawn(function()
            while System.__properties.__slashesoffury_active and System.__properties.__slashesoffury_count < maxParryCount do
                if System.__config.__detections.__slashesoffury then System.parry.execute(); task.wait(parryDelay)
                else break end
            end
        end)
    end)
end)

Runtime.ChildAdded:Connect(function(Object)
    if System.__config.__detections.__phantom then
        if Object.Name=="maxTransmission" or Object.Name=="transmissionpart" then
            local Weld=Object:FindFirstChildWhichIsA("WeldConstraint")
            if Weld then
                local Character=LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
                if Character and Weld.Part1==Character.HumanoidRootPart then
                    local CurrentBall=System.ball.get(); Weld:Destroy()
                    if CurrentBall then
                        local FocusConnection
                        FocusConnection=RunService.RenderStepped:Connect(function()
                            local Highlighted=CurrentBall:GetAttribute("highlighted")
                            if Highlighted==true then
                                ReplicatedStorage.Remotes.AbilityButtonPress:Fire()
                                System.__properties.__parried=true
                                task.delay(1,function() System.__properties.__parried=false end)
                            elseif Highlighted==false then FocusConnection:Disconnect() end
                        end)
                        task.delay(3,function() if FocusConnection and FocusConnection.Connected then FocusConnection:Disconnect() end end)
                    end
                end
            end
        end
    end
end)

ReplicatedStorage.Remotes.ParrySuccessAll.OnClientEvent:Connect(function(_,root)
    if root.Parent and root.Parent ~= LocalPlayer.Character then
        if not Alive or root.Parent.Parent ~= Alive then return end
    end
    local closest=System.player.get_closest(); local ball=System.ball.get()
    if not ball or not closest then return end
    local target_distance=(LocalPlayer.Character.PrimaryPart.Position-closest.PrimaryPart.Position).Magnitude
    local distance=(LocalPlayer.Character.PrimaryPart.Position-ball.Position).Magnitude
    local direction=(LocalPlayer.Character.PrimaryPart.Position-ball.Position).Unit
    local dot=direction:Dot(ball.AssemblyLinearVelocity.Unit)
    local curve_detected=System.detection.is_curved()
    if target_distance < 15 and distance < 15 and dot > -0.25 then
        if curve_detected then System.parry.execute_action() end
    end
    if System.__properties.__grab_animation then System.__properties.__grab_animation:Stop() end
end)

ReplicatedStorage.Remotes.ParrySuccess.OnClientEvent:Connect(function()
    if not Alive or LocalPlayer.Character.Parent ~= Alive then return end
    if System.__properties.__grab_animation then System.__properties.__grab_animation:Stop() end
end)

-- ============================================================
-- TRIGGERBOT
-- ============================================================
System.triggerbot = {}
local TRIGGERBOT_COOLDOWN = 0.03
local TRIGGERBOT_PARSE_TIME = 0.02

function System.triggerbot.trigger(ball)
    if System.__triggerbot.__is_parrying or System.__triggerbot.__parries > System.__triggerbot.__max_parries then return end
    if LocalPlayer.Character and LocalPlayer.Character.PrimaryPart and LocalPlayer.Character.PrimaryPart:FindFirstChild('SingularityCape') then return end
    System.__triggerbot.__is_parrying = true
    System.__triggerbot.__parries = System.__triggerbot.__parries + 1
    System.parry.execute()
    if System.__properties.__play_animation then System.animation.play_grab_parry() end
    task.delay(TRIGGERBOT_COOLDOWN, function()
        if System.__triggerbot.__parries > 0 then System.__triggerbot.__parries = System.__triggerbot.__parries - 1 end
    end)
    task.spawn(function()
        local start_time = tick()
        repeat RunService.Heartbeat:Wait()
        until (tick()-start_time >= TRIGGERBOT_PARSE_TIME or not System.__triggerbot.__is_parrying)
        System.__triggerbot.__is_parrying = false
    end)
end

function System.triggerbot.loop()
    if not System.__triggerbot.__enabled then return end
    if LocalPlayer.Character and LocalPlayer.Character.PrimaryPart and LocalPlayer.Character.PrimaryPart:FindFirstChild('SingularityCape') then return end
    local balls = Workspace:FindFirstChild('Balls'); if not balls then return end
    for _, ball in pairs(balls:GetChildren()) do
        if ball:IsA('BasePart') and ball:GetAttribute('target') == LocalPlayer.Name then
            System.triggerbot.trigger(ball)
            break
        end
    end
end

function System.triggerbot.enable(enabled)
    System.__triggerbot.__enabled = enabled
    if enabled then
        if not System.__properties.__connections.__triggerbot then
            System.__properties.__connections.__triggerbot = RunService.PreSimulation:Connect(System.triggerbot.loop)
        end
    else
        if System.__properties.__connections.__triggerbot then
            System.__properties.__connections.__triggerbot:Disconnect()
            System.__properties.__connections.__triggerbot = nil
        end
        System.__triggerbot.__is_parrying = false
        System.__triggerbot.__parries = 0
    end
end

-- ============================================================
-- MANUAL SPAM (HEARTBEAT - ULTRA FAST)
-- ============================================================
System.manual_spam = {}
local macroAnimFix = false
local spam_accumulator = 0
local SPAM_RATE = 0.01

function System.manual_spam.start()
    System.__properties.__manual_spam_enabled = true
end

function System.manual_spam.stop()
    System.__properties.__manual_spam_enabled = false
end

RunService.Heartbeat:Connect(function(dt)
    if not System.__properties.__manual_spam_enabled then
        spam_accumulator = 0
        return
    end
    spam_accumulator = spam_accumulator + dt
    local maxFires = 5
    local fired = 0
    while spam_accumulator >= SPAM_RATE and fired < maxFires do
        spam_accumulator = spam_accumulator - SPAM_RATE
        fired = fired + 1
        if getgenv().ManualSpamMode == "Keypress" then
            pcall(function() System.parry.keypress() end)
        else
            pcall(function() System.parry.execute() end)
            if getgenv().ManualSpamAnimationFix and macroAnimFix then
                pcall(function() System.animation.play_grab_parry() end)
            end
        end
    end
    if spam_accumulator > SPAM_RATE * 10 then spam_accumulator = 0 end
end)

-- ============================================================
-- AUTO PARRY
-- ============================================================
System.autoparry = {}
function System.autoparry.start()
    if System.__properties.__connections.__autoparry then
        System.__properties.__connections.__autoparry:Disconnect()
    end
    System.__properties.__connections.__autoparry = RunService.PreSimulation:Connect(function()
        if not System.__properties.__autoparry_enabled or not LocalPlayer.Character or not LocalPlayer.Character.PrimaryPart then return end
        local balls = System.ball.get_all(); local one_ball = System.ball.get()
        local training_ball = nil
        if Workspace:FindFirstChild("TrainingBalls") then
            for _, Instance in pairs(Workspace.TrainingBalls:GetChildren()) do
                if Instance:GetAttribute("realBall") then training_ball = Instance; break end
            end
        end
        for _, ball in pairs(balls) do
            if System.__triggerbot.__enabled then return end
            if not ball then continue end
            local zoomies = ball:FindFirstChild('zoomies'); if not zoomies then continue end
            ball:GetAttributeChangedSignal('target'):Once(function() System.__properties.__parried = false end)
            if System.__properties.__parried then continue end
            local ball_target = ball:GetAttribute('target')
            local velocity = zoomies.VectorVelocity
            local distance = (LocalPlayer.Character.PrimaryPart.Position - ball.Position).Magnitude
            local ping = Stats.Network.ServerStatsItem['Data Ping']:GetValue() / 10
            local ping_threshold = math.clamp(ping / 10, 5, 17)
            local speed = velocity.Magnitude
            local capped_speed_diff = math.min(math.max(speed - 9.5, 0), 650)
            local speed_divisor = (2.4 + capped_speed_diff * 0.002) * System.__properties.__divisor_multiplier
            local parry_accuracy = ping_threshold + math.max(speed / speed_divisor, 9.5)
            local curved = System.detection.is_curved()
            if ball:FindFirstChild('AeroDynamicSlashVFX') then
                ball.AeroDynamicSlashVFX:Destroy(); System.__properties.__tornado_time = tick()
            end
            if Runtime:FindFirstChild('Tornado') then
                if (tick()-System.__properties.__tornado_time) < (Runtime.Tornado:GetAttribute('TornadoTime') or 1)+0.314159 then continue end
            end
            if one_ball and one_ball:GetAttribute('target')==LocalPlayer.Name and curved then continue end
            if ball:FindFirstChild('ComboCounter') then continue end
            if LocalPlayer.Character.PrimaryPart:FindFirstChild('SingularityCape') then continue end
            if System.__config.__detections.__infinity and System.__properties.__infinity_active then continue end
            if System.__config.__detections.__deathslash and System.__properties.__deathslash_active then continue end
            if System.__config.__detections.__timehole and System.__properties.__timehole_active then continue end
            if System.__config.__detections.__slashesoffury and System.__properties.__slashesoffury_active then continue end

            if ball_target == LocalPlayer.Name and distance <= parry_accuracy then
                if System.__properties.__auto_ability_enabled then
                    local AbilityCD = LocalPlayer.PlayerGui.Hotbar.Ability.UIGradient
                    if AbilityCD and AbilityCD.Offset.Y == 0.5 then
                        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Abilities") then
                            local abilities = LocalPlayer.Character.Abilities
                            if (abilities:FindFirstChild("Raging Deflection") and abilities["Raging Deflection"].Enabled) or
                               (abilities:FindFirstChild("Rapture") and abilities["Rapture"].Enabled) or
                               (abilities:FindFirstChild("Calming Deflection") and abilities["Calming Deflection"].Enabled) or
                               (abilities:FindFirstChild("Aerodynamic Slash") and abilities["Aerodynamic Slash"].Enabled) or
                               (abilities:FindFirstChild("Fracture") and abilities["Fracture"].Enabled) or
                               (abilities:FindFirstChild("Death Slash") and abilities["Death Slash"].Enabled) then
                                System.__properties.__parried = true
                                ReplicatedStorage.Remotes.AbilityButtonPress:Fire()
                                task.wait(2.432)
                                local ds = ReplicatedStorage:FindFirstChild("Remotes") and ReplicatedStorage.Remotes:FindFirstChild("DeathSlashShootActivation")
                                if ds then pcall(function() ds:FireServer(true) end) end
                                continue
                            end
                        end
                    end
                end
            end

            if ball_target == LocalPlayer.Name and distance <= parry_accuracy then
                if System.__properties.__cooldown_protection then
                    local AbilityCD = LocalPlayer.PlayerGui.Hotbar.Ability.UIGradient
                    if AbilityCD and AbilityCD.Offset.Y == 0.5 then
                        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Abilities") then
                            local abilities = LocalPlayer.Character.Abilities
                            if (abilities:FindFirstChild("Raging Deflection") and abilities["Raging Deflection"].Enabled) or
                               (abilities:FindFirstChild("Rapture") and abilities["Rapture"].Enabled) or
                               (abilities:FindFirstChild("Calming Deflection") and abilities["Calming Deflection"].Enabled) then
                                System.__properties.__parried = true
                                ReplicatedStorage.Remotes.AbilityButtonPress:Fire()
                                continue
                            end
                        end
                    end
                end
            end

            if ball_target==LocalPlayer.Name and distance <= parry_accuracy then
                if getgenv().AutoParryMode=="Keypress" then System.parry.keypress()
                else System.parry.execute_action() end
                System.__properties.__parried=true
            end
            local last_parrys=tick()
            repeat RunService.Stepped:Wait()
            until (tick()-last_parrys) >= 1 or not System.__properties.__parried
            System.__properties.__parried=false
        end
        if training_ball then
            local zoomies=training_ball:FindFirstChild('zoomies')
            if zoomies then
                training_ball:GetAttributeChangedSignal('target'):Once(function() System.__properties.__training_parried=false end)
                if not System.__properties.__training_parried then
                    local ball_target=training_ball:GetAttribute('target')
                    local velocity=zoomies.VectorVelocity
                    local distance=LocalPlayer:DistanceFromCharacter(training_ball.Position)
                    local speed=velocity.Magnitude
                    local ping=Stats.Network.ServerStatsItem['Data Ping']:GetValue()/10
                    local ping_threshold=math.clamp(ping/10,5,17)
                    local capped_speed_diff=math.min(math.max(speed-9.5,0),650)
                    local speed_divisor=(2.4+capped_speed_diff*0.002)*System.__properties.__divisor_multiplier
                    local parry_accuracy=ping_threshold+math.max(speed/speed_divisor,9.5)
                    if ball_target==LocalPlayer.Name and distance <= parry_accuracy then
                        if getgenv().AutoParryMode=="Keypress" then System.parry.keypress()
                        else System.parry.execute_action() end
                        System.__properties.__training_parried=true
                        local last_parrys=tick()
                        repeat RunService.Stepped:Wait()
                        until (tick()-last_parrys) >= 1 or not System.__properties.__training_parried
                        System.__properties.__training_parried=false
                    end
                end
            end
        end
    end)
end

function System.autoparry.stop()
    if System.__properties.__connections.__autoparry then
        System.__properties.__connections.__autoparry:Disconnect()
        System.__properties.__connections.__autoparry = nil
    end
end
-- ============================================================
-- HEADLESS & KORBLOX
-- ============================================================
local Byte_Library = {}
function Byte_Library.Korblox(char)
    if not char then return end
    local leg = char:FindFirstChild("Right Leg"); if not leg then return end
    if not leg:FindFirstChild("KorbloxMesh") then
        for _, v in leg:GetChildren() do if v:IsA("SpecialMesh") then v:Destroy() end end
        local m = Instance.new("SpecialMesh"); m.Name = "KorbloxMesh"
        m.MeshId = "rbxassetid://902942096"; m.TextureId = "rbxassetid://902843398"
        m.Offset = Vector3.new(0, 0.7, 0); m.Parent = leg
    end
end
function Byte_Library.Restore_Leg(char)
    if not char then return end
    local leg = char:FindFirstChild("Right Leg"); if not leg then return end
    for _, v in leg:GetChildren() do if v:IsA("SpecialMesh") then v:Destroy() end end
end
function Byte_Library.Headless(char)
    if not char then return end
    local head = char:FindFirstChild("Head"); if not head then return end
    head.Transparency = 1
    for _, child in head:GetChildren() do
        if child:IsA("Decal") or child.Name == "face" then child.Transparency = 1
        elseif child:IsA("SpecialMesh") or child:IsA("DataModelMesh") then
            if not child:GetAttribute("OriginalScale") then
                child:SetAttribute("OriginalScale", child.Scale); child.Scale = Vector3.new(0, 0, 0)
            end
        end
    end
end
function Byte_Library.Restore_Head(char)
    if not char then return end
    local head = char:FindFirstChild("Head"); if not head then return end
    head.Transparency = 0
    for _, child in head:GetChildren() do
        if child:IsA("Decal") or child.Name == "face" then child.Transparency = 0
        elseif child:IsA("SpecialMesh") or child:IsA("DataModelMesh") then
            local orig = child:GetAttribute("OriginalScale")
            if orig then child.Scale = orig; child:SetAttribute("OriginalScale", nil) end
        end
    end
end
local function ApplyHeadlessKorblox()
    local char = LocalPlayer.Character; if not char then return end
    if System.__properties.__headless_enabled then Byte_Library.Headless(char) end
    if System.__properties.__korblox_enabled then Byte_Library.Korblox(char) end
end
LocalPlayer.CharacterAdded:Connect(function(char) task.wait(0.5); ApplyHeadlessKorblox() end)

-- ============================================================
-- MOBILE UI
-- ============================================================
local mobile_ui_button = nil
local function create_mobile_ui_button()
    if mobile_ui_button and mobile_ui_button.gui then
        pcall(function() mobile_ui_button.gui:Destroy() end)
    end
    local gui = Instance.new('ScreenGui')
    gui.Name = 'EagleHubMobileUIButton'; gui.ResetOnSpawn = false
    gui.IgnoreGuiInset = true; gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    gui.DisplayOrder = 9999; gui.Parent = CoreGui
    local button = Instance.new('TextButton')
    button.Name = 'UIButton'; button.Size = UDim2.new(0, 65, 0, 65)
    button.Position = UDim2.new(0.90, 0, 0.15, 0)
    button.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    button.BackgroundTransparency = 0.3; button.AnchorPoint = Vector2.new(0.5, 0.5)
    button.Draggable = true; button.AutoButtonColor = true
    button.ZIndex = 10000; button.Text = ""; button.Parent = gui
    local corner = Instance.new('UICorner'); corner.CornerRadius = UDim.new(1, 0); corner.Parent = button
    local stroke = Instance.new('UIStroke'); stroke.Color = Color3.fromRGB(255, 255, 255)
    stroke.Thickness = 2; stroke.Transparency = 0.3; stroke.Parent = button
    local text = Instance.new('TextLabel')
    text.Size = UDim2.new(1, 0, 1, 0); text.BackgroundTransparency = 1
    text.Text = "UI"; text.Font = Enum.Font.GothamBold; text.TextSize = 22
    text.TextColor3 = Color3.fromRGB(255, 255, 255); text.ZIndex = 10001; text.Parent = button
    button.MouseButton1Click:Connect(function()
        pcall(function() Window:Toggle() end)
    end)
    mobile_ui_button = { gui = gui, button = button }
    return mobile_ui_button
end

local function create_mobile_button(name, position_y, color, x_pos)
    local gui = Instance.new('ScreenGui')
    gui.Name = 'EagleHub_' .. name .. '_Mobile'; gui.ResetOnSpawn = false
    gui.IgnoreGuiInset = true; gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    gui.DisplayOrder = 9998; gui.Parent = CoreGui
    local button = Instance.new('TextButton')
    button.Size = UDim2.new(0, 130, 0, 55)
    button.Position = UDim2.new(x_pos or 0.15, 0, position_y, 0)
    button.BackgroundTransparency = 1; button.AnchorPoint = Vector2.new(0.5, 0)
    button.Draggable = true; button.AutoButtonColor = false; button.ZIndex = 2
    local bg = Instance.new('Frame'); bg.Size = UDim2.new(1, 0, 1, 0)
    bg.BackgroundColor3 = Color3.fromRGB(40, 40, 40); bg.Parent = button
    Instance.new('UICorner', bg).CornerRadius = UDim.new(0, 10)
    local stroke = Instance.new('UIStroke', bg); stroke.Color = color
    stroke.Thickness = 2; stroke.Transparency = 0.3
    local text = Instance.new('TextLabel')
    text.Size = UDim2.new(1, 0, 1, 0); text.BackgroundTransparency = 1; text.Text = name
    text.Font = Enum.Font.GothamBold; text.TextSize = 17
    text.TextColor3 = Color3.fromRGB(255, 255, 255); text.ZIndex = 3; text.Parent = button
    button.Parent = gui
    return {gui = gui, button = button, text = text, bg = bg}
end

local function destroy_mobile_gui(gui_data) if gui_data and gui_data.gui then gui_data.gui:Destroy() end end

-- ============================================================
-- SKIN CHANGER
-- ============================================================
local SKIN_SAVE_FILE = "EagleHubX/skin.json"

local function loadSkinSave()
    local data = {}
    pcall(function()
        if isfile and isfile(SKIN_SAVE_FILE) then
            local decoded = HttpService:JSONDecode(readfile(SKIN_SAVE_FILE))
            if type(decoded) == "table" then data = decoded end
        end
    end)
    return data
end

local function saveSkinData()
    pcall(function()
        if isfolder and makefolder and not isfolder("EagleHubX") then makefolder("EagleHubX") end
        if writefile then
            writefile(SKIN_SAVE_FILE, HttpService:JSONEncode({swordModel = getgenv().swordModel or ""}))
        end
    end)
end

getgenv().saveLastEquippedSword = saveSkinData
local savedSkin = loadSkinSave()
getgenv().skinChanger = false
getgenv().skinChangerEnabled = false
getgenv().swordModel = savedSkin.swordModel or ""
getgenv().swordAnimations = savedSkin.swordModel or ""
getgenv().swordFX = savedSkin.swordModel or ""
getgenv().slashName = "SlashEffect"

task.spawn(function()
    local rs = game:GetService("ReplicatedStorage")
    local swordInstancesInstance = rs:WaitForChild("Shared", 9e9):WaitForChild("ReplicatedInstances", 9e9):WaitForChild("Swords", 9e9)
    local swordInstances = require(swordInstancesInstance)
    local swordsController
    task.spawn(function()
        while task.wait(0.25) and not swordsController do
            local ok, conns = pcall(getconnections, rs.Remotes.FireSwordInfo.OnClientEvent)
            if ok and conns then
                for _, v in ipairs(conns) do
                    if v.Function and islclosure and islclosure(v.Function) then
                        local ok2, up = pcall(getupvalues, v.Function)
                        if ok2 and #up == 1 and type(up[1]) == "table" then swordsController = up[1]; break end
                    end
                end
            end
        end
    end)
    local function getSlashName(swordName)
        local ok, sln = pcall(function() return swordInstances:GetSword(swordName) end)
        return (ok and sln and sln.SlashName) or "SlashEffect"
    end
    local function refreshSlashName()
        local fxName = getgenv().swordFX ~= "" and getgenv().swordFX or getgenv().swordModel
        if fxName ~= "" then getgenv().slashName = getSlashName(fxName)
        else getgenv().slashName = "SlashEffect" end
    end
    refreshSlashName()
    local function setSword()
        if not getgenv().skinChanger then return end
        if not LocalPlayer.Character then return end
        pcall(function()
            local f = rawget(swordInstances, "EquipSwordTo")
            if type(f) == "function" then
                local ups = getupvalues(f)
                for i = 1, #ups do if type(ups[i]) == "boolean" then setupvalue(f, i, false); break end end
            end
        end)
        pcall(function() swordInstances:EquipSwordTo(LocalPlayer.Character, getgenv().swordModel) end)
        task.spawn(function()
            local attempts = 0
            while not swordsController and attempts < 20 do task.wait(0.5); attempts = attempts + 1 end
            if not swordsController then return end
            pcall(function()
                if swordsController.SetSword then
                    swordsController:SetSword(getgenv().swordAnimations ~= "" and getgenv().swordAnimations or getgenv().swordModel)
                end
            end)
            pcall(function()
                local targetSword = getgenv().swordFX ~= "" and getgenv().swordFX or getgenv().swordModel
                if rs.Remotes:FindFirstChild("FireSwordInfo") then rs.Remotes.FireSwordInfo:FireServer(targetSword) end
                if swordsController.currentSword ~= nil then pcall(function() swordsController.currentSword = targetSword end) end
                if swordsController.SwordFX ~= nil then pcall(function() swordsController.SwordFX = targetSword end) end
            end)
        end)
    end
    local hookedFuncs = {}
    task.spawn(function()
        local remotesToHook = {"ParrySuccessAll", "ParryAttempt", "ParrySuccess", "PlaySound", "PlayVisuals"}
        while task.wait(1) do
            for _, remoteName in ipairs(remotesToHook) do
                local remote = rs.Remotes:FindFirstChild(remoteName)
                if remote and remote:IsA("RemoteEvent") then
                    local ok, conns = pcall(getconnections, remote.OnClientEvent)
                    if ok and type(conns) == "table" then
                        for _, v in ipairs(conns) do
                            local func = v.Function
                            if func and not hookedFuncs[func] then
                                hookedFuncs[func] = true
                                v:Disable()
                                local targetFunc = func
                                local ourFunc
                                ourFunc = function(...)
                                    local args = { ... }
                                    local isLocal = false
                                    for _, arg in ipairs(args) do
                                        if tostring(arg) == LocalPlayer.Name or (typeof(arg) == "Instance" and (arg == LocalPlayer.Character or arg == LocalPlayer)) then
                                            isLocal = true; break
                                        end
                                    end
                                    if isLocal and getgenv().skinChanger then
                                        local fxSword = getgenv().swordFX ~= "" and getgenv().swordFX or getgenv().swordModel
                                        refreshSlashName()
                                        local swordFound = false; local slashFound = false
                                        for i, arg in ipairs(args) do
                                            if type(arg) == "string" then
                                                if fxSword ~= "" and not slashFound and (arg:match("Slash") or arg == "Default" or arg:match("Effect")) then
                                                    args[i] = getgenv().slashName; slashFound = true
                                                elseif fxSword ~= "" and not swordFound then
                                                    local isSword = false
                                                    pcall(function()
                                                        if rs.Shared.ReplicatedInstances.Swords:FindFirstChild(arg) then isSword = true end
                                                    end)
                                                    if isSword or arg == LocalPlayer:GetAttribute("CurrentlyEquippedSword") then
                                                        args[i] = fxSword; swordFound = true
                                                    end
                                                end
                                            end
                                        end
                                        if fxSword ~= "" and not slashFound and type(args[1]) == "string" then args[1] = getgenv().slashName end
                                        if fxSword ~= "" and not swordFound and type(args[3]) == "string" then args[3] = fxSword end
                                    end
                                    if setthreadidentity then pcall(setthreadidentity, 2) end
                                    pcall(targetFunc, unpack(args))
                                end
                                hookedFuncs[ourFunc] = true
                                remote.OnClientEvent:Connect(ourFunc)
                            end
                        end
                    end
                end
            end
        end
    end)
    getgenv().updateSword = function()
        refreshSlashName()
        if getgenv().skinChanger and getgenv().swordModel ~= "" then saveSkinData() end
        setSword()
    end
    task.spawn(function()
        while task.wait(1) do
            if getgenv().skinChanger and getgenv().swordModel ~= "" then
                local char = LocalPlayer.Character
                if char then
                    if LocalPlayer:GetAttribute("CurrentlyEquippedSword") ~= getgenv().swordModel then setSword() end
                    if not char:FindFirstChild(getgenv().swordModel) then setSword() end
                    for _, v in pairs(char:GetChildren()) do
                        if v:IsA("Model") and v.Name ~= getgenv().swordModel then v:Destroy() end
                        task.wait()
                    end
                end
            end
        end
    end)
    LocalPlayer.CharacterAdded:Connect(function()
        if getgenv().skinChanger then
            getgenv().skinChanger = false
            if getgenv().setSkinChangerToggleUI then getgenv().setSkinChangerToggleUI(false) end
            task.wait(2)
            getgenv().skinChanger = true
            if getgenv().setSkinChangerToggleUI then getgenv().setSkinChangerToggleUI(true) end
            task.wait(0.5)
            pcall(function() getgenv().updateSword() end)
        end
    end)
end)

-- ============================================================
-- AVATAR CHANGER
-- ============================================================
local __players = cloneref(game:GetService('Players'))
local __localplayer = __players.LocalPlayer

local function saveOriginalAppearance()
    if _G.OriginalAppearance then return end
    local char = __localplayer.Character; if not char then return end
    _G.OriginalAppearance = {Face = nil, Shirt = nil, Pants = nil, BodyColors = nil, HeadMesh = nil, Accessories = {}, CharacterMeshes = {}}
    local head = char:FindFirstChild("Head")
    if head then
        local face = head:FindFirstChildOfClass("Decal"); if face then _G.OriginalAppearance.Face = face.Texture end
        local headMesh = head:FindFirstChildOfClass("SpecialMesh"); if headMesh then _G.OriginalAppearance.HeadMesh = headMesh:Clone() end
    end
    local shirt = char:FindFirstChildOfClass("Shirt"); if shirt then _G.OriginalAppearance.Shirt = shirt.ShirtTemplate end
    local pants = char:FindFirstChildOfClass("Pants"); if pants then _G.OriginalAppearance.Pants = pants.PantsTemplate end
    local bc = char:FindFirstChildOfClass("BodyColors")
    if bc then
        _G.OriginalAppearance.BodyColors = {HeadColor3 = bc.HeadColor3, LeftArmColor3 = bc.LeftArmColor3, RightArmColor3 = bc.RightArmColor3, LeftLegColor3 = bc.LeftLegColor3, RightLegColor3 = bc.RightLegColor3, TorsoColor3 = bc.TorsoColor3}
    end
    for _, obj in ipairs(char:GetChildren()) do
        if obj:IsA("Accessory") or obj:IsA("Accoutrement") then table.insert(_G.OriginalAppearance.Accessories, obj:Clone())
        elseif obj:IsA("CharacterMesh") then table.insert(_G.OriginalAppearance.CharacterMeshes, obj:Clone()) end
    end
end

local function restoreOriginalAppearance()
    local char = __localplayer.Character; if not char or not _G.OriginalAppearance then return end
    pcall(function()
        for _, obj in ipairs(char:GetChildren()) do
            if obj:IsA("Accessory") or obj:IsA("Accoutrement") or obj:IsA("Shirt") or obj:IsA("Pants") or obj:IsA("BodyColors") or obj:IsA("CharacterMesh") or obj:IsA("ShirtGraphic") then obj:Destroy() end
        end
        local head = char:FindFirstChild("Head")
        if head then
            local face = head:FindFirstChildOfClass("Decal"); if face then face:Destroy() end
            if _G.OriginalAppearance.Face then
                local newFace = Instance.new("Decal"); newFace.Name = "face"; newFace.Texture = _G.OriginalAppearance.Face; newFace.Parent = head
            end
            local headMesh = head:FindFirstChildOfClass("SpecialMesh"); if headMesh then headMesh:Destroy() end
            if _G.OriginalAppearance.HeadMesh then _G.OriginalAppearance.HeadMesh:Clone().Parent = head end
        end
        if _G.OriginalAppearance.Shirt then
            local shirt = Instance.new("Shirt"); shirt.Name = "Shirt"; shirt.ShirtTemplate = _G.OriginalAppearance.Shirt; shirt.Parent = char
        end
        if _G.OriginalAppearance.Pants then
            local pants = Instance.new("Pants"); pants.Name = "Pants"; pants.PantsTemplate = _G.OriginalAppearance.Pants; pants.Parent = char
        end
        if _G.OriginalAppearance.BodyColors then
            local bc = Instance.new("BodyColors")
            for k, v in pairs(_G.OriginalAppearance.BodyColors) do bc[k] = v end
            bc.Parent = char
        end
        for _, mesh in ipairs(_G.OriginalAppearance.CharacterMeshes) do mesh:Clone().Parent = char end
        for _, acc in ipairs(_G.OriginalAppearance.Accessories) do acc:Clone().Parent = char end
    end)
end

local function attachAccessoryManually(char, acc)
    local handle = acc:FindFirstChild("Handle")
    if not handle or not handle:IsA("BasePart") then return end
    local accAttachment = handle:FindFirstChildOfClass("Attachment")
    local charAttachment
    if accAttachment then
        for _, part in ipairs(char:GetChildren()) do
            if part:IsA("BasePart") then
                charAttachment = part:FindFirstChild(accAttachment.Name)
                if charAttachment then break end
            end
        end
    end
    if charAttachment then
        acc.Parent = char; handle.CanCollide = false; handle.Anchored = false
        local part = charAttachment.Parent
        if charAttachment:IsA("Attachment") and accAttachment then
            handle.CFrame = part.CFrame * charAttachment.CFrame * accAttachment.CFrame:Inverse()
        else handle.CFrame = part.CFrame * CFrame.new(0, 0, 0) end
        local weld = Instance.new("Weld"); weld.Name = "AccessoryWeld"; weld.Part0 = handle; weld.Part1 = part
        weld.C0 = accAttachment and accAttachment.CFrame or CFrame.new(0, 0.6, 0)
        weld.C1 = charAttachment:IsA("Attachment") and charAttachment.CFrame or CFrame.new()
        weld.Parent = handle
    else
        local part = char:FindFirstChild("Head")
        if part then
            acc.Parent = char; handle.CanCollide = false; handle.Anchored = false
            handle.CFrame = part.CFrame * CFrame.new(0, 0.6, 0)
            local weld = Instance.new("Weld"); weld.Name = "AccessoryWeld"; weld.Part0 = handle; weld.Part1 = part
            weld.C0 = CFrame.new(0, 0.6, 0); weld.C1 = CFrame.new(); weld.Parent = handle
        else acc.Parent = char end
    end
end

local function applyAvatarLocally(userId)
    local char = __localplayer.Character; if not char then return end
    local success, model = pcall(function() return __players:CreateHumanoidModelFromUserId(userId) end)
    if not success or not model then return end
    pcall(function()
        for _, obj in ipairs(char:GetChildren()) do
            if obj:IsA("Accessory") or obj:IsA("Accoutrement") or obj:IsA("Shirt") or obj:IsA("Pants") or obj:IsA("BodyColors") or obj:IsA("CharacterMesh") or obj:IsA("ShirtGraphic") then obj:Destroy() end
        end
        local head = char:FindFirstChild("Head")
        local modelHead = model:FindFirstChild("Head")
        if head and modelHead then
            local face = head:FindFirstChildOfClass("Decal"); if face then face:Destroy() end
            local modelFace = modelHead:FindFirstChildOfClass("Decal"); if modelFace then modelFace:Clone().Parent = head end
            local headMesh = head:FindFirstChildOfClass("SpecialMesh")
            local modelMesh = modelHead:FindFirstChildOfClass("SpecialMesh")
            if modelMesh then if headMesh then headMesh:Destroy() end; modelMesh:Clone().Parent = head
            elseif headMesh then headMesh:Destroy() end
            head.Size = modelHead.Size; head.Color = modelHead.Color
        end
        for _, obj in ipairs(model:GetChildren()) do
            if obj:IsA("Shirt") or obj:IsA("Pants") or obj:IsA("BodyColors") or obj:IsA("ShirtGraphic") or obj:IsA("CharacterMesh") then obj:Clone().Parent = char
            elseif obj:IsA("Accessory") or obj:IsA("Accoutrement") then pcall(function() attachAccessoryManually(char, obj:Clone()) end) end
        end
        model:Destroy()
    end)
end

local __avatar_changer_target = ""
local __avatar_changer_enabled = false

local function __resolveTargetId(value)
    if value == nil or value == "" then return nil end
    local id = tonumber(value); if id then return id end
    local ok, resolved = pcall(function() return __players:GetUserIdFromNameAsync(value) end)
    if ok and resolved then return resolved end
    return nil
end

-- ============================================================
-- ABILITY ESP
-- ============================================================
local abilityEspBillboards = {}
local abilityEspConnections = {}
local abilityEspPlayerAddedConnection = nil

local function create_ability_esp_for_player(player)
    task.spawn(function()
        local character = player.Character
        while not character or not character.Parent do task.wait(0.5); character = player.Character end
        local head = character:WaitForChild('Head', 10)
        if not head or not getgenv().AbilityESP then return end
        local existing = head:FindFirstChild('AbilityESPGui'); if existing then existing:Destroy() end
        local billboard = Instance.new('BillboardGui')
        billboard.Name = 'AbilityESPGui'; billboard.Adornee = head
        billboard.Size = UDim2.new(0, 220, 0, 60)
        billboard.StudsOffset = Vector3.new(0, 3.5, 0); billboard.AlwaysOnTop = true
        billboard.Parent = head
        local label = Instance.new('TextLabel')
        label.Size = UDim2.new(1, 0, 1, 0); label.BackgroundTransparency = 1
        label.TextColor3 = Color3.fromRGB(255, 255, 255); label.TextSize = 14
        label.TextStrokeTransparency = 0; label.Font = Enum.Font.Roboto
        label.RichText = true; label.TextXAlignment = Enum.TextXAlignment.Center
        label.TextYAlignment = Enum.TextYAlignment.Center; label.Parent = billboard
        label.Visible = false
        abilityEspBillboards[player] = label
        local humanoid = character:FindFirstChild('Humanoid')
        if humanoid then humanoid.DisplayDistanceType = Enum.HumanoidDisplayDistanceType.None end
        local heartbeatConnection
        heartbeatConnection = RunService.Heartbeat:Connect(function()
            if not (character and character.Parent) then
                if heartbeatConnection then heartbeatConnection:Disconnect() end
                pcall(function() billboard:Destroy() end)
                abilityEspBillboards[player] = nil; return
            end
            if getgenv().AbilityESP then
                label.Visible = true
                local ability = player:GetAttribute('EquippedAbility')
                if ability then label.Text = '<b>' .. player.DisplayName .. ' [' .. ability .. ']' .. '</b>'
                else label.Text = '<b>' .. player.DisplayName .. '</b>' end
            else label.Visible = false end
        end)
        abilityEspConnections[player] = heartbeatConnection
    end)
end

local function add_ability_esp_player(player)
    if player == LocalPlayer then return end
    if abilityEspConnections[player] then
        pcall(function() abilityEspConnections[player]:Disconnect() end)
        abilityEspConnections[player] = nil
    end
    player.CharacterAdded:Connect(function() create_ability_esp_for_player(player) end)
    if player.Character then task.spawn(function() create_ability_esp_for_player(player) end) end
end

function start_ability_esp()
    if abilityEspPlayerAddedConnection and next(abilityEspConnections) then return end
    getgenv().AbilityESP = true
    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer then add_ability_esp_player(player) end
    end
    if not abilityEspPlayerAddedConnection then
        abilityEspPlayerAddedConnection = Players.PlayerAdded:Connect(function(player)
            if getgenv().AbilityESP then add_ability_esp_player(player) end
        end)
    end
end

function stop_ability_esp()
    if not getgenv().AbilityESP then return end
    getgenv().AbilityESP = false
    if abilityEspPlayerAddedConnection then
        pcall(function() abilityEspPlayerAddedConnection:Disconnect() end)
        abilityEspPlayerAddedConnection = nil
    end
    for _, connection in pairs(abilityEspConnections) do pcall(function() connection:Disconnect() end) end
    abilityEspConnections = {}
    for _, label in pairs(abilityEspBillboards) do
        pcall(function() if label and label.Parent then label.Parent:Destroy() end end)
    end
    abilityEspBillboards = {}
end

-- ============================================================
-- BALL VELOCITY GUI
-- ============================================================
function System.create_ball_velocity_gui()
    if System.__properties.__ball_velocity_gui then System.__properties.__ball_velocity_gui.gui:Destroy() end
    local gui = Instance.new("ScreenGui"); gui.Name = "BallVelocityGUI"; gui.ResetOnSpawn = false
    gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling; gui.DisplayOrder = 999
    local frame = Instance.new("Frame"); frame.Size = UDim2.new(0, 200, 0, 75)
    frame.Position = UDim2.new(0, 10, 0.80, 0); frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    frame.BackgroundTransparency = 0.4; frame.BorderSizePixel = 0; frame.Active = true; frame.Draggable = true
    Instance.new("UICorner", frame).CornerRadius = UDim.new(0, 8)
    local stroke = Instance.new("UIStroke", frame); stroke.Color = Color3.fromRGB(255,255,255); stroke.Thickness = 2
    local title = Instance.new("TextLabel", frame); title.Size = UDim2.new(1,0,0,18); title.Position = UDim2.new(0,0,0,5)
    title.BackgroundTransparency = 1; title.Text = "Ball Status"; title.TextColor3 = Color3.fromRGB(255,255,255)
    title.Font = Enum.Font.GothamBold; title.TextSize = 13
    local cl = Instance.new("TextLabel", frame); cl.Size = UDim2.new(1,-10,0,22); cl.Position = UDim2.new(0,5,0,24)
    cl.BackgroundTransparency = 1; cl.Text = "Current: 0"; cl.TextColor3 = Color3.fromRGB(255,255,255)
    cl.Font = Enum.Font.GothamBold; cl.TextSize = 15; cl.TextXAlignment = Enum.TextXAlignment.Left
    local pl = Instance.new("TextLabel", frame); pl.Size = UDim2.new(1,-10,0,22); pl.Position = UDim2.new(0,5,0,46)
    pl.BackgroundTransparency = 1; pl.Text = "Peak: 0"; pl.TextColor3 = Color3.fromRGB(255,255,255)
    pl.Font = Enum.Font.GothamBold; pl.TextSize = 15; pl.TextXAlignment = Enum.TextXAlignment.Left
    frame.Parent = gui; gui.Parent = CoreGui
    System.__properties.__ball_velocity_gui = {gui=gui, frame=frame, currentSpeedLabel=cl, peakSpeedLabel=pl}
end

function System.update_ball_velocity()
    if not System.__properties.__ball_velocity_enabled or not System.__properties.__ball_velocity_gui then return end
    local ball = System.ball.get()
    if not ball then System.__properties.__ball_velocity_gui.currentSpeedLabel.Text = "Current: 0"; return end
    local ballId = ball:GetFullName()
    if ballId ~= System.__properties.__last_ball_id then System.__properties.__peak_velocity = 0; System.__properties.__last_ball_id = ballId end
    local zoomies = ball:FindFirstChild('zoomies')
    if not zoomies then System.__properties.__ball_velocity_gui.currentSpeedLabel.Text = "Current: 0"; return end
    local speed = zoomies.VectorVelocity.Magnitude
    if speed > System.__properties.__peak_velocity then System.__properties.__peak_velocity = speed end
    local color = Color3.fromRGB(255, 255, 0)
    if speed > 2000 then color = Color3.fromRGB(255, 0, 0)
    elseif speed > 1500 then color = Color3.fromRGB(255, 165, 0)
    elseif speed > 1000 then color = Color3.fromRGB(255, 215, 0) end
    local peakColor = Color3.fromRGB(255, 255, 0)
    if System.__properties.__peak_velocity > 2000 then peakColor = Color3.fromRGB(255, 0, 0)
    elseif System.__properties.__peak_velocity > 1500 then peakColor = Color3.fromRGB(255, 165, 0)
    elseif System.__properties.__peak_velocity > 1000 then peakColor = Color3.fromRGB(255, 215, 0) end
    System.__properties.__ball_velocity_gui.currentSpeedLabel.RichText = true
    System.__properties.__ball_velocity_gui.currentSpeedLabel.Text = string.format("Current: <font color='#%02x%02x%02x'>%.1f</font>", math.floor(color.R*255), math.floor(color.G*255), math.floor(color.B*255), speed)
    System.__properties.__ball_velocity_gui.peakSpeedLabel.RichText = true
    System.__properties.__ball_velocity_gui.peakSpeedLabel.Text = string.format("Peak: <font color='#%02x%02x%02x'>%.1f</font>", math.floor(peakColor.R*255), math.floor(peakColor.G*255), math.floor(peakColor.B*255), System.__properties.__peak_velocity)
end

-- ============================================================
-- PING GUI
-- ============================================================
local PingGui = Instance.new("ScreenGui", CoreGui)
PingGui.Name = "EagleRealPing"; PingGui.ResetOnSpawn = false
PingGui.IgnoreGuiInset = true; PingGui.DisplayOrder = 999; PingGui.Enabled = false
local PingFrame = Instance.new("Frame", PingGui)
PingFrame.Size = UDim2.new(0, 110, 0, 35); PingFrame.Position = UDim2.new(0, 15, 0.88, 0)
PingFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 10); PingFrame.BackgroundTransparency = 0.3
PingFrame.BorderSizePixel = 0; PingFrame.Active = true; PingFrame.Draggable = true
Instance.new("UICorner", PingFrame).CornerRadius = UDim.new(0, 8)
Instance.new("UIStroke", PingFrame).Color = Color3.fromRGB(60, 60, 60)
local PingLabel = Instance.new("TextLabel", PingFrame)
PingLabel.Size = UDim2.new(1, 0, 1, 0); PingLabel.Text = "Ping: 0ms"
PingLabel.TextColor3 = Color3.fromRGB(255, 255, 255); PingLabel.BackgroundTransparency = 1
PingLabel.Font = Enum.Font.GothamBold; PingLabel.TextSize = 14
PingLabel.TextXAlignment = Enum.TextXAlignment.Center

task.spawn(function()
    while task.wait(0.5) do
        if System.__properties.__show_ping then
            local ping = Stats.Network.ServerStatsItem['Data Ping']:GetValue()
            local color = Color3.fromRGB(0, 255, 0)
            if ping > 150 then color = Color3.fromRGB(255, 165, 0)
            elseif ping > 300 then color = Color3.fromRGB(255, 0, 0) end
            PingLabel.Text = string.format("Ping: <font color='#%02x%02x%02x'>%dms</font>", math.floor(color.R*255), math.floor(color.G*255), math.floor(color.B*255), ping)
            PingLabel.RichText = true
        end
    end
end)
-- ============================================================
-- UI TABS CONTENT
-- ============================================================

-- AUTOPARRY TAB
local AS = Tabs.Rage:AddGroupbox({Title = "Auto Parry", Column = "Left"})
AS:AddToggle({Name = "Auto Parry", Default = false, ConfigId = "autoparry", Callback = function(v)
    System.__properties.__autoparry_enabled = v
    System.__properties.__play_animation = v
    if v then System.autoparry.start() else System.autoparry.stop() end
    Notify("Auto Parry", v and "ON" or "OFF", 2)
end})
AS:AddDropdown({Name = "Parry Mode", Options = {"Remote", "Keypress"}, Default = "Remote", ConfigId = "parrymode", Callback = function(v) getgenv().AutoParryMode = v end})
AS:AddDropdown({Name = "Curve Mode", Options = System.__config.__curve_names, Default = "Camera", ConfigId = "curvemode", Callback = function(v)
    for i, n in ipairs(System.__config.__curve_names) do if n == v then System.__properties.__curve_mode = i; break end end
end})
AS:AddSlider({Name = "Accuracy", Default = 50, Min = 1, Max = 100, ConfigId = "accuracy", Callback = function(v) System.__properties.__accuracy = v; update_divisor() end})
AS:AddToggle({Name = "Random Curve", Default = false, ConfigId = "randomcurve", Callback = function(s)
    if s then
        if not System.__properties.__connections.__rc then
            System.__properties.__connections.__rc = RunService.PreSimulation:Connect(function()
                System.__properties.__curve_mode = math.random(1, #System.__config.__curve_names)
            end)
        end
    else
        if System.__properties.__connections.__rc then
            System.__properties.__connections.__rc:Disconnect()
            System.__properties.__connections.__rc = nil
        end
    end
end})
AS:AddToggle({Name = "Auto Ability", Default = false, ConfigId = "autoability", Callback = function(v)
    System.__properties.__auto_ability_enabled = v
    Notify("Auto Ability", v and "ON" or "OFF", 2)
end})
AS:AddToggle({Name = "Cooldown Protection", Default = false, ConfigId = "cooldown", Callback = function(v)
    System.__properties.__cooldown_protection = v
    Notify("Cooldown Protection", v and "ON" or "OFF", 2)
end})

-- TRIGGERBOT
local TBS = Tabs.Rage:AddGroupbox({Title = "Triggerbot", Column = "Right"})
TBS:AddToggle({Name = "Triggerbot", Default = false, ConfigId = "triggerbot", Callback = function(v)
    System.__properties.__triggerbot_enabled = v
    System.triggerbot.enable(v)
    Notify("Triggerbot", v and "ON" or "OFF", 2)
    if isMobile then
        if v then
            if not System.__properties.__mobile_guis.triggerbot then
                local tb = create_mobile_button('Trigger', 0.20, Color3.fromRGB(255, 100, 0), 0.15)
                System.__properties.__mobile_guis.triggerbot = tb
                tb.button.MouseButton1Click:Connect(function()
                    System.__properties.__triggerbot_enabled = not System.__properties.__triggerbot_enabled
                    System.triggerbot.enable(System.__properties.__triggerbot_enabled)
                    if System.__properties.__triggerbot_enabled then
                        tb.text.Text = "ON"
                        tb.text.TextColor3 = Color3.fromRGB(0, 255, 100)
                    else
                        tb.text.Text = "Trigger"
                        tb.text.TextColor3 = Color3.fromRGB(255, 255, 255)
                    end
                    Notify("Triggerbot", System.__properties.__triggerbot_enabled and "ON" or "OFF", 2)
                end)
            end
        else
            destroy_mobile_gui(System.__properties.__mobile_guis.triggerbot)
            System.__properties.__mobile_guis.triggerbot = nil
        end
    end
end})

-- DETECTION TAB
local DS1 = Tabs.Detection:AddGroupbox({Title = "Infinity", Column = "Left"})
DS1:AddToggle({Name = "Infinity Detection", Default = false, ConfigId = "det_infinity", Callback = function(v) System.__config.__detections.__infinity = v end})
local DS2 = Tabs.Detection:AddGroupbox({Title = "Death Slash", Column = "Left"})
DS2:AddToggle({Name = "Death Slash Detection", Default = false, ConfigId = "det_deathslash", Callback = function(v) System.__config.__detections.__deathslash = v end})
local DS3 = Tabs.Detection:AddGroupbox({Title = "Time Hole", Column = "Right"})
DS3:AddToggle({Name = "Time Hole Detection", Default = false, ConfigId = "det_timehole", Callback = function(v) System.__config.__detections.__timehole = v end})
local DS4 = Tabs.Detection:AddGroupbox({Title = "Slashes Of Fury", Column = "Right"})
DS4:AddToggle({Name = "Slashes Detection", Default = false, ConfigId = "det_slashes", Callback = function(v) System.__config.__detections.__slashesoffury = v end})
DS4:AddSlider({Name = "Parry Delay", Default = 0.05, Min = 0.05, Max = 0.25, Decimals = 2, ConfigId = "slashes_delay", Callback = function(v) parryDelay = v end})
DS4:AddSlider({Name = "Max Parry Count", Default = 36, Min = 1, Max = 100, ConfigId = "slashes_max", Callback = function(v) maxParryCount = v end})
local DS5 = Tabs.Detection:AddGroupbox({Title = "Anti-Phantom [BETA]", Column = "Right"})
DS5:AddToggle({Name = "Anti-Phantom [BETA]", Default = false, ConfigId = "det_phantom", Callback = function(v) System.__config.__detections.__phantom = v end})

-- SPAM TAB
local SP = Tabs.Spam:AddGroupbox({Title = "Manual Spam", Column = "Left"})
SP:AddToggle({Name = "Manual Spam", Default = false, ConfigId = "manualspam", Callback = function(v)
    System.__properties.__manual_spam_enabled = v
    Notify("Manual Spam", v and "ON" or "OFF", 2)
    if isMobile then
        if v then
            if not System.__properties.__mobile_guis.manual_spam then
                local sm = create_mobile_button('Spam', 0.35, Color3.fromRGB(255, 255, 255), 0.15)
                System.__properties.__mobile_guis.manual_spam = sm
                sm.button.MouseButton1Click:Connect(function()
                    System.__properties.__manual_spam_enabled = not System.__properties.__manual_spam_enabled
                    if System.__properties.__manual_spam_enabled then
                        sm.text.Text = "ON"
                        sm.text.TextColor3 = Color3.fromRGB(0, 255, 100)
                    else
                        sm.text.Text = "Spam"
                        sm.text.TextColor3 = Color3.fromRGB(255, 255, 255)
                    end
                    Notify("Manual Spam", System.__properties.__manual_spam_enabled and "ON" or "OFF", 2)
                end)
            end
        else
            destroy_mobile_gui(System.__properties.__mobile_guis.manual_spam)
            System.__properties.__mobile_guis.manual_spam = nil
        end
    end
end})
SP:AddDropdown({Name = "Mode", Options = {"Remote", "Keypress"}, Default = "Remote", ConfigId = "spam_mode", Callback = function(v) getgenv().ManualSpamMode = v end})
SP:AddToggle({Name = "Animation Fix", Default = false, ConfigId = "spam_animfix", Callback = function(v)
    getgenv().ManualSpamAnimationFix = v
    macroAnimFix = v
end})

-- PLAYER TAB
local AVC = Tabs.Player:AddGroupbox({Title = "Avatar Changer", Column = "Left"})
AVC:AddInput({Name = "Target Username", Placeholder = "Username or User ID", Default = "", ConfigId = "avatar_target", Callback = function(t)
    __avatar_changer_target = t
end})
AVC:AddToggle({Name = "Enable Avatar Changer", Default = false, ConfigId = "avatar_enabled", Callback = function(v)
    __avatar_changer_enabled = v
    if v then
        local userId = __resolveTargetId(__avatar_changer_target)
        if userId then
            saveOriginalAppearance(); applyAvatarLocally(userId)
            Notify("Avatar Changer", "Appearance changed!", 3)
        else Notify("Avatar Changer", "Invalid username or ID!", 3) end
    else
        restoreOriginalAppearance()
        Notify("Avatar Changer", "Appearance restored!", 2)
    end
end})

local HK = Tabs.Player:AddGroupbox({Title = "Headless & Korblox", Column = "Right"})
HK:AddToggle({Name = "Headless", Default = false, ConfigId = "headless", Callback = function(v)
    System.__properties.__headless_enabled = v
    local c = LocalPlayer.Character
    if c then if v then Byte_Library.Headless(c) else Byte_Library.Restore_Head(c) end end
end})
HK:AddToggle({Name = "Korblox", Default = false, ConfigId = "korblox", Callback = function(v)
    System.__properties.__korblox_enabled = v
    local c = LocalPlayer.Character
    if c then if v then Byte_Library.Korblox(c) else Byte_Library.Restore_Leg(c) end end
end})

-- VISUALS TAB
local VS = Tabs.Visuals:AddGroupbox({Title = "Ball Stats", Column = "Left"})
VS:AddToggle({Name = "Show Ball Velocity", Default = false, ConfigId = "ball_velocity", Callback = function(v)
    System.__properties.__ball_velocity_enabled = v
    if v then
        System.create_ball_velocity_gui()
        if not System.__properties.__connections.__ball_velocity then
            System.__properties.__connections.__ball_velocity = RunService.RenderStepped:Connect(function() System.update_ball_velocity() end)
        end
    else
        if System.__properties.__ball_velocity_gui then System.__properties.__ball_velocity_gui.gui:Destroy(); System.__properties.__ball_velocity_gui = nil end
        if System.__properties.__connections.__ball_velocity then System.__properties.__connections.__ball_velocity:Disconnect(); System.__properties.__connections.__ball_velocity = nil end
    end
end})
VS:AddToggle({Name = "Show Real Ping", Default = false, ConfigId = "show_ping", Callback = function(v)
    System.__properties.__show_ping = v
    PingGui.Enabled = v
end})

local AE = Tabs.Visuals:AddGroupbox({Title = "Ability ESP", Column = "Right"})
AE:AddToggle({Name = "Ability ESP", Default = false, ConfigId = "ability_esp", Callback = function(s)
    if s then start_ability_esp(); Notify("Ability ESP", "ON", 2)
    else stop_ability_esp(); Notify("Ability ESP", "OFF", 2) end
end})

-- MISC TAB
local SC = Tabs.Misc:AddGroupbox({Title = "Skin Changer", Column = "Left"})
local skinChangerToggle
skinChangerToggle = SC:AddToggle({Name = "Skin Changer", Default = false, ConfigId = "skin_enabled", Callback = function(v)
    getgenv().skinChanger = v
    getgenv().skinChangerEnabled = v
    if v and getgenv().swordModel ~= "" then
        if getgenv().updateSword then pcall(getgenv().updateSword) end
        Notify("Skin Changer", "Enabled", 2)
    else Notify("Skin Changer", "Disabled", 2) end
end})
getgenv().setSkinChangerToggleUI = function(v)
    if skinChangerToggle then
        skinChangerToggle:SetValue(v)
        getgenv().skinChanger = v
        getgenv().skinChangerEnabled = v
    end
end
SC:AddInput({Name = "Sword Name", Placeholder = "e.g. DualPrince", Default = "", ConfigId = "skin_name", Callback = function(t)
    getgenv().swordModel = t
    getgenv().swordAnimations = t
    getgenv().swordFX = t
    if getgenv().skinChangerEnabled and t ~= "" then
        if getgenv().updateSword then pcall(getgenv().updateSword) end
    end
    if getgenv().saveLastEquippedSword then pcall(getgenv().saveLastEquippedSword) end
end})

-- ============================================================
-- UNLOCK ALL — DÜZƏLDİLMİŞ VERSİYA
-- ============================================================
local UA = Tabs.Misc:AddGroupbox({Title = "Unlock All", Column = "Right"})
UA:AddButton({Name = "Load Unlock All", Callback = function()
    Notify("Unlock All", "Loading script...", 3)
    local success, err = pcall(function()
        loadstring(game:HttpGet("https://flowauth.net/v1/loaders/5d423493a8f0aa8432cda8455a5f8906.lua"))()
    end)
    if success then Notify("Unlock All", "Script loaded!", 3)
    else Notify("Unlock All", "Error: " .. tostring(err), 5) end
end})
UA:AddButton({Name = "Remove Unlock UI", Callback = function()
    Notify("Unlock All", "Removing UI...", 2)
    task.spawn(function()
        task.wait(0.2)
        local destroyed_count = 0

        local keywords = {"unlock", "unlocksuite", "flowauth", "flow", "authui", "hubui", "keyui", "keysystem", "key", "loader"}

        local function shouldDestroy(gui)
            if not gui or not gui.Name then return false end
            local name = tostring(gui.Name):lower()
            for _, kw in ipairs(keywords) do
                if name:find(kw, 1, true) then return true end
            end
            return false
        end

        local function tryDestroy(gui)
            if not gui then return end
            pcall(function()
                gui:Destroy()
                destroyed_count = destroyed_count + 1
            end)
        end

        -- 1. PlayerGui
        local playerGui = LocalPlayer:FindFirstChildOfClass("PlayerGui")
        if playerGui then
            for _, gui in ipairs(playerGui:GetChildren()) do
                if gui:IsA("ScreenGui") and shouldDestroy(gui) then tryDestroy(gui) end
            end
        end

        -- 2. CoreGui
        pcall(function()
            for _, gui in ipairs(CoreGui:GetChildren()) do
                if gui:IsA("ScreenGui") and shouldDestroy(gui) then tryDestroy(gui) end
            end
        end)

        -- 3. gethui()
        pcall(function()
            if gethui then
                local hui = gethui()
                if hui then
                    for _, gui in ipairs(hui:GetChildren()) do
                        if gui:IsA("ScreenGui") and shouldDestroy(gui) then tryDestroy(gui) end
                    end
                end
            end
        end)

        -- 4. getgenv referansları
        pcall(function()
            for _, key in ipairs({"UnlockGui", "UnlockSuiteGui", "_usStandaloneUnlockGui", "unlockGui", "flowAuthGui", "FlowAuthUI", "FlowAuthUI_Standalone", "UnlockAllUI"}) do
                if getgenv()[key] and typeof(getgenv()[key]) == "Instance" then
                    tryDestroy(getgenv()[key])
                    getgenv()[key] = nil
                end
            end
        end)

        -- 5. Fallback — ScreenGui + Parent yoxla
        pcall(function()
            for _, gui in ipairs(game:GetDescendants()) do
                if gui:IsA("ScreenGui") and gui.Parent then
                    local p = gui.Parent
                    if p == playerGui or p == CoreGui then
                        local name = tostring(gui.Name):lower()
                        if name:find("unlock", 1, true) or name:find("suite", 1, true) or name:find("flow", 1, true) or name:find("auth", 1, true) then
                            tryDestroy(gui)
                        end
                    end
                end
            end
        end)

        if destroyed_count > 0 then
            Notify("Unlock All", "Removed (" .. destroyed_count .. " UI)", 2)
        else
            Notify("Unlock All", "No UI found! Try again.", 3)
        end
    end)
end})

local NR = Tabs.Misc:AddGroupbox({Title = "No Render", Column = "Right"})
local Connections_Manager = {}
NR:AddToggle({Name = "No Render", Default = false, ConfigId = "no_render", Callback = function(state)
    local effectScripts = LocalPlayer.PlayerScripts:FindFirstChild("EffectScripts")
    if effectScripts then
        local clientFX = effectScripts:FindFirstChild("ClientFX")
        if clientFX then clientFX.Disabled = state end
    end
    if state then
        Connections_Manager['No Render'] = Workspace.Runtime.ChildAdded:Connect(function(Value) Debris:AddItem(Value, 0) end)
    else
        if Connections_Manager['No Render'] then
            Connections_Manager['No Render']:Disconnect()
            Connections_Manager['No Render'] = nil
        end
    end
end})

local AutoJump = false
local ajLastOnGround = false
local AJ = Tabs.Misc:AddGroupbox({Title = "Auto Jump", Column = "Right"})
AJ:AddToggle({Name = "Auto Jump", Default = false, ConfigId = "auto_jump", Callback = function(v)
    AutoJump = v
    if not v then ajLastOnGround = false end
    Notify("Auto Jump", v and "ON" or "OFF", 2)
end})

RunService.Heartbeat:Connect(function()
    if AutoJump then
        local char = LocalPlayer.Character
        local hum = char and char:FindFirstChildOfClass("Humanoid")
        if hum then
            local onGround = hum.FloorMaterial ~= Enum.Material.Air
            if onGround and not ajLastOnGround then hum:ChangeState(Enum.HumanoidStateType.Jumping) end
            ajLastOnGround = onGround
        end
    else ajLastOnGround = false end
end)
-- ============================================================
-- CUSTOM BACKGROUND SYSTEM
-- ============================================================
local BG_SAVE_FILE = "EagleHubX/backgrounds.json"
local savedBackgrounds = {}

local function loadBackgrounds()
    pcall(function()
        if isfile and isfile(BG_SAVE_FILE) then
            local decoded = HttpService:JSONDecode(readfile(BG_SAVE_FILE))
            if type(decoded) == "table" then savedBackgrounds = decoded end
        end
    end)
end

local function saveBackgrounds()
    pcall(function()
        if isfolder and makefolder and not isfolder("EagleHubX") then makefolder("EagleHubX") end
        if writefile then writefile(BG_SAVE_FILE, HttpService:JSONEncode(savedBackgrounds)) end
    end)
end

local function applyBackground(assetId)
    if not assetId or assetId == "" then return end
    local mf = Window.Main
    if not mf then return end
    local old = mf:FindFirstChild("CustomBG"); if old then old:Destroy() end
    local old2 = mf:FindFirstChild("BGOverlay"); if old2 then old2:Destroy() end
    local bi = Instance.new("ImageLabel")
    bi.Name = "CustomBG"; bi.Size = UDim2.new(1, 0, 1, 0); bi.BackgroundTransparency = 1
    bi.Image = "rbxassetid://" .. tostring(assetId); bi.ScaleType = Enum.ScaleType.Crop
    bi.ImageTransparency = 0.3; bi.ZIndex = 0; bi.Parent = mf
    Instance.new("UICorner", bi).CornerRadius = UDim.new(0, 12)
    local ov = Instance.new("Frame")
    ov.Name = "BGOverlay"; ov.Size = UDim2.new(1, 0, 1, 0); ov.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    ov.BackgroundTransparency = 0.5; ov.BorderSizePixel = 0; ov.ZIndex = 1; ov.Parent = mf
    Instance.new("UICorner", ov).CornerRadius = UDim.new(0, 12)
end

loadBackgrounds()

local BG = Tabs.Settings:AddGroupbox({Title = "Custom Background", Column = "Left"})
local bgName = ""
local bgId = ""
BG:AddInput({Name = "Theme Name", Placeholder = "e.g. Anime BG", Default = "", Callback = function(t) bgName = t end})
BG:AddInput({Name = "Asset ID", Placeholder = "e.g. 1234567890", Default = "", Callback = function(t) bgId = t end})

local SavedBGHolder = Tabs.Settings:AddGroupbox({Title = "Saved Themes", Column = "Right"})

local function getThemeNames()
    local names = {}
    for name, _ in pairs(savedBackgrounds) do table.insert(names, name) end
    table.sort(names)
    if #names == 0 then table.insert(names, "(no themes)") end
    return names
end

local currentDropdown = SavedBGHolder:AddDropdown({
    Name = "Select Theme",
    Options = getThemeNames(),
    Default = getThemeNames()[1],
    Callback = function(v) end
})

local function refreshThemesList()
    local names = getThemeNames()
    if currentDropdown and currentDropdown.SetOptions then
        currentDropdown:SetOptions(names)
    end
end

BG:AddButton({Name = "Save & Apply", Callback = function()
    if bgName == "" or bgId == "" then Notify("Custom BG", "Name & ID required!", 3); return end
    local id = tonumber(bgId)
    if not id then Notify("Custom BG", "ID must be number!", 3); return end
    savedBackgrounds[bgName] = bgId
    saveBackgrounds()
    applyBackground(bgId)
    refreshThemesList()
    if currentDropdown and currentDropdown.Set then currentDropdown.Set(currentDropdown, bgName) end
    Notify("Custom BG", "Saved: " .. bgName, 3)
end})

BG:AddButton({Name = "Reset Background", Callback = function()
    local mf = Window.Main
    if mf then
        local b = mf:FindFirstChild("CustomBG"); if b then b:Destroy() end
        local o = mf:FindFirstChild("BGOverlay"); if o then o:Destroy() end
        Notify("Custom BG", "Background reset!", 2)
    end
end})

SavedBGHolder:AddButton({Name = "Apply Selected", Callback = function()
    local selected = currentDropdown:Get()
    if selected and selected ~= "(no themes)" and savedBackgrounds[selected] then
        applyBackground(savedBackgrounds[selected])
        Notify("Custom BG", "Applied: " .. selected, 2)
    else Notify("Custom BG", "No theme selected!", 3) end
end})

SavedBGHolder:AddButton({Name = "Delete Selected", Callback = function()
    local selected = currentDropdown:Get()
    if selected and selected ~= "(no themes)" and savedBackgrounds[selected] then
        savedBackgrounds[selected] = nil
        saveBackgrounds()
        refreshThemesList()
        Notify("Custom BG", "Deleted: " .. selected, 2)
    else Notify("Custom BG", "No theme selected!", 3) end
end})

-- ============================================================
-- KEYBIND PICKER
-- ============================================================
local keybindState = {
    menu = Enum.KeyCode.LeftControl,
    spam = Enum.KeyCode.E,
    trig = Enum.KeyCode.R,
    jump = Enum.KeyCode.J,
}
local listening = nil
local menuBtn, spamBtn, trigBtn, jumpBtn

local KB = Tabs.Settings:AddGroupbox({Title = "Keybinds", Column = "Right"})

menuBtn = KB:AddButton({Name = "Menu Key: LeftCtrl", Callback = function()
    if listening then return end
    listening = "menu"
    if menuBtn then menuBtn.Text = "Press any key..." end
    Notify("Keybind", "Press any key for Menu (Esc to cancel)", 4)
end})

spamBtn = KB:AddButton({Name = "Manual Spam Key: E", Callback = function()
    if listening then return end
    listening = "spam"
    if spamBtn then spamBtn.Text = "Press any key..." end
    Notify("Keybind", "Press any key for Spam (Esc to cancel)", 4)
end})

trigBtn = KB:AddButton({Name = "Trigger Key: R", Callback = function()
    if listening then return end
    listening = "trig"
    if trigBtn then trigBtn.Text = "Press any key..." end
    Notify("Keybind", "Press any key for Trigger (Esc to cancel)", 4)
end})

jumpBtn = KB:AddButton({Name = "Auto Jump Key: J", Callback = function()
    if listening then return end
    listening = "jump"
    if jumpBtn then jumpBtn.Text = "Press any key..." end
    Notify("Keybind", "Press any key for Jump (Esc to cancel)", 4)
end})

UserInputService.InputBegan:Connect(function(inp, gp)
    if gp then return end

    if listening then
        if inp.UserInputType == Enum.UserInputType.Keyboard then
            local kc = inp.KeyCode
            if kc == Enum.KeyCode.Escape then
                if listening == "menu" and menuBtn then menuBtn.Text = "Menu Key: " .. keybindState.menu.Name
                elseif listening == "spam" and spamBtn then spamBtn.Text = "Manual Spam Key: " .. keybindState.spam.Name
                elseif listening == "trig" and trigBtn then trigBtn.Text = "Trigger Key: " .. keybindState.trig.Name
                elseif listening == "jump" and jumpBtn then jumpBtn.Text = "Auto Jump Key: " .. keybindState.jump.Name end
                listening = nil
                Notify("Keybind", "Cancelled", 2)
                return
            end
            if listening == "menu" then
                keybindState.menu = kc
                if menuBtn then menuBtn.Text = "Menu Key: " .. kc.Name end
                if Window.SetMenuKey then Window:SetMenuKey(kc) end
                Notify("Keybind", "Menu: " .. kc.Name, 2)
            elseif listening == "spam" then
                keybindState.spam = kc
                if spamBtn then spamBtn.Text = "Manual Spam Key: " .. kc.Name end
                Notify("Keybind", "Spam: " .. kc.Name, 2)
            elseif listening == "trig" then
                keybindState.trig = kc
                if trigBtn then trigBtn.Text = "Trigger Key: " .. kc.Name end
                Notify("Keybind", "Trigger: " .. kc.Name, 2)
            elseif listening == "jump" then
                keybindState.jump = kc
                if jumpBtn then jumpBtn.Text = "Auto Jump Key: " .. kc.Name end
                Notify("Keybind", "Jump: " .. kc.Name, 2)
            end
            listening = nil
            return
        end
    end

    local kc = inp.KeyCode
    local cmap = {[Enum.KeyCode.One]=1,[Enum.KeyCode.Two]=2,[Enum.KeyCode.Three]=3,[Enum.KeyCode.Four]=4,[Enum.KeyCode.Five]=5,[Enum.KeyCode.Six]=6,[Enum.KeyCode.Seven]=7,[Enum.KeyCode.Eight]=8,[Enum.KeyCode.Nine]=9}
    if cmap[kc] then
        System.__properties.__curve_mode = cmap[kc]
        Notify("Curve Mode", System.__config.__curve_names[cmap[kc]], 1)
    end
    if kc == keybindState.spam then
        System.__properties.__manual_spam_enabled = not System.__properties.__manual_spam_enabled
        Notify("Manual Spam", System.__properties.__manual_spam_enabled and "ON" or "OFF", 1)
    end
    if kc == keybindState.trig then
        local n = not System.__properties.__triggerbot_enabled
        System.__properties.__triggerbot_enabled = n
        System.triggerbot.enable(n)
        Notify("Triggerbot", n and "ON" or "OFF", 1)
    end
    if kc == keybindState.jump then
        AutoJump = not AutoJump
        if not AutoJump then ajLastOnGround = false end
        Notify("Auto Jump", AutoJump and "ON" or "OFF", 1)
    end
end)

-- ============================================================
-- MANUAL CONFIG MANAGER
-- ============================================================
local CONFIG_FOLDER = "EagleHubX/Configs"

local function ensureConfigFolder()
    pcall(function()
        if isfolder and makefolder then
            if not isfolder("EagleHubX") then makefolder("EagleHubX") end
            if not isfolder(CONFIG_FOLDER) then makefolder(CONFIG_FOLDER) end
        end
    end)
end

local function getSavedConfigs()
    local list = {}
    pcall(function()
        if listfiles and isfolder and isfolder(CONFIG_FOLDER) then
            for _, file in ipairs(listfiles(CONFIG_FOLDER)) do
                local name = file:match("([^/\\]+)%.json$")
                if name then table.insert(list, name) end
            end
        end
    end)
    table.sort(list)
    if #list == 0 then table.insert(list, "(no configs)") end
    return list
end

ensureConfigFolder()

local CFG = Tabs.Settings:AddGroupbox({Title = "Config Manager", Column = "Left"})
local configName = ""
CFG:AddInput({Name = "Config Name", Placeholder = "e.g. MyConfig", Default = "", Callback = function(t) configName = t end})

local configDropdown

local function refreshConfigList()
    local list = getSavedConfigs()
    if configDropdown and configDropdown.SetOptions then
        configDropdown:SetOptions(list)
    end
end

configDropdown = CFG:AddDropdown({
    Name = "Saved Configs",
    Options = getSavedConfigs(),
    Default = getSavedConfigs()[1],
    Callback = function(v) end
})

CFG:AddButton({Name = "Save Config", Callback = function()
    if configName == "" then Notify("Config", "Enter config name!", 3); return end
    ensureConfigFolder()
    pcall(function()
        local data = Window:GetAllConfig()
        local count = 0
        for _ in pairs(data) do count = count + 1 end
        local path = CONFIG_FOLDER .. "/" .. configName .. ".json"
        writefile(path, HttpService:JSONEncode(data))
        refreshConfigList()
        Notify("Config", "Saved: " .. configName .. " (" .. count .. ")", 3)
    end)
end})

CFG:AddButton({Name = "Load Config", Callback = function()
    if not configDropdown then Notify("Config", "Dropdown not ready!", 3); return end
    local selected = configDropdown:Get()
    if not selected or selected == "(no configs)" then
        Notify("Config", "No config selected!", 3); return
    end
    pcall(function()
        local path = CONFIG_FOLDER .. "/" .. selected .. ".json"
        if isfile and isfile(path) then
            local raw = readfile(path)
            local decoded = HttpService:JSONDecode(raw)
            if type(decoded) == "table" then
                task.spawn(function()
                    local loaded = Window:LoadAllConfig(decoded)
                    Notify("Config", "Loaded: " .. selected .. " (" .. tostring(loaded) .. ")", 3)
                end)
            end
        else
            Notify("Config", "File not found!", 3)
        end
    end)
end})

CFG:AddButton({Name = "Delete Config", Callback = function()
    if not configDropdown then return end
    local selected = configDropdown:Get()
    if not selected or selected == "(no configs)" then
        Notify("Config", "No config selected!", 3); return
    end
    pcall(function()
        local path = CONFIG_FOLDER .. "/" .. selected .. ".json"
        if delfile and isfile and isfile(path) then
            delfile(path)
            refreshConfigList()
            Notify("Config", "Deleted: " .. selected, 2)
        end
    end)
end})

-- ============================================================
-- MOBILE UI (Main toggle button)
-- ============================================================
if isMobile then
    task.spawn(function()
        task.wait(3)
        create_mobile_ui_button()
    end)
end

-- ============================================================
-- FINAL
-- ============================================================
Notify("EAGLE Hub X", "Loaded successfully!", 5)
print("EAGLE Hub X | Loaded! | Mobile: " .. tostring(isMobile))

end)
