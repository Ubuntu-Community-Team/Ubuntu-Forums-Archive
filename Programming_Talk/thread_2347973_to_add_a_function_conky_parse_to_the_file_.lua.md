---
title: "to add a function conky_parse to the file .lua"
date: 2016-12-30
forum: Programming Talk
---

### Post by Night Train on 2016-12-30
hi guys ... and happy new year!

I have updated conky to 1.10.6 version and, as you will know, I have owed rewrite the syntax of the commands, but now all perfectly works

I would want to add the function that allows to know the dimension of an any folder (in conky only the partitions they are managed of default)

now, if I insert the command in the configuration file of conky, I don't have any problem ... I have used the syntax (example):
```

${offset 165}${font Ubuntu:size=8:style=normal}${color1}Used: ${font Ubuntu:size=8,weight:normal}${color3}${texeci 600 du -sh "/path/of/folder"|cut --fields=1}
```

and I get the desired result

but if I wanted to insert it in the file .lua as I could do?

from what I have read, I should use the function conky_parse, but also to create the variable... in practice, I don't know whether to do

guys, can you help me?

thank you so much

I attach example-lua.txt
(which totally works for a partition)

```

require 'cairo'

gauge = {

-- Storage rings
{
    name='fs_used_perc',           arg='/',                  max_value=100,
    x=70,                          y=410,
    graph_radius=36,
    graph_thickness=8,
    graph_start_angle=180,
    graph_unit_angle=2.7,          graph_unit_thickness=2.7,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.05,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.15,
    hand_fg_colour=0xE37222,       hand_fg_alpha=0.7,
    txt_radius=26,
    txt_weight=1.0,                txt_size=8.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.7,
    graduation_radius=30,
    graduation_thickness=0,        graduation_mark_thickness=2,
    graduation_unit_angle=27,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    caption='root',
    caption_weight=0.8,            caption_size=9.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=0.5,
},
}

-- converts color in hexa to decimal
function rgb_to_r_g_b(colour, alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

-- convert degree to rad and rotate (0 degree is top/north)
function angle_to_position(start_angle, current_angle)
    local pos = current_angle + start_angle
    return ( ( pos * (2 * math.pi / 360) ) - (math.pi / 2) )
end


-- displays gauges
function draw_gauge_ring(display, data, value, border)
    local max_value = data['max_value']
    local x, y = data['x'] + border, data['y'] + border
    local graph_radius = data['graph_radius']
    local graph_thickness, graph_unit_thickness = data['graph_thickness'], data['graph_unit_thickness']
    local graph_start_angle = data['graph_start_angle']
    local graph_unit_angle = data['graph_unit_angle']
    local graph_bg_colour, graph_bg_alpha = data['graph_bg_colour'], data['graph_bg_alpha']
    local graph_fg_colour, graph_fg_alpha = data['graph_fg_colour'], data['graph_fg_alpha']
    local hand_fg_colour, hand_fg_alpha = data['hand_fg_colour'], data['hand_fg_alpha']
    local graph_end_angle = (max_value * graph_unit_angle) % 360

    -- background ring
    cairo_arc(display, x, y, graph_radius, angle_to_position(graph_start_angle, 0), angle_to_position(graph_start_angle, graph_end_angle))
    cairo_set_source_rgba(display, rgb_to_r_g_b(graph_bg_colour, graph_bg_alpha))
    cairo_set_line_width(display, graph_thickness)
    cairo_stroke(display)

    -- arc of value
    local val = value % (max_value + 1)
    local start_arc = 0
    local stop_arc = 0
    local i = 1
    while i <= val do
        start_arc = (graph_unit_angle * i) - graph_unit_thickness
        stop_arc = (graph_unit_angle * i)
        cairo_arc(display, x, y, graph_radius, angle_to_position(graph_start_angle, start_arc), angle_to_position(graph_start_angle, stop_arc))
        cairo_set_source_rgba(display, rgb_to_r_g_b(graph_fg_colour, graph_fg_alpha))
        cairo_stroke(display)
        i = i + 1
    end
    local angle = start_arc

    -- hand
    start_arc = (graph_unit_angle * val) - (graph_unit_thickness)
    stop_arc = (graph_unit_angle * val)
    cairo_arc(display, x, y, graph_radius, angle_to_position(graph_start_angle, start_arc), angle_to_position(graph_start_angle, stop_arc))
    cairo_set_source_rgba(display, rgb_to_r_g_b(hand_fg_colour, hand_fg_alpha))
    cairo_stroke(display)

    -- graduations marks
    local graduation_radius = data['graduation_radius']
    local graduation_thickness, graduation_mark_thickness = data['graduation_thickness'], data['graduation_mark_thickness']
    local graduation_unit_angle = data['graduation_unit_angle']
    local graduation_fg_colour, graduation_fg_alpha = data['graduation_fg_colour'], data['graduation_fg_alpha']
    if graduation_radius > 0 and graduation_thickness > 0 and graduation_unit_angle > 0 then
        local nb_graduation = graph_end_angle / graduation_unit_angle
        local i = 0
        while i < nb_graduation do
            cairo_set_line_width(display, graduation_thickness)
            start_arc = (graduation_unit_angle * i) - (graduation_mark_thickness / 2)
            stop_arc = (graduation_unit_angle * i) + (graduation_mark_thickness / 2)
            cairo_arc(display, x, y, graduation_radius, angle_to_position(graph_start_angle, start_arc), angle_to_position(graph_start_angle, stop_arc))
            cairo_set_source_rgba(display,rgb_to_r_g_b(graduation_fg_colour,graduation_fg_alpha))
            cairo_stroke(display)
            cairo_set_line_width(display, graph_thickness)
            i = i + 1
        end
    end

    -- text
    local txt_radius = data['txt_radius']
    local txt_weight, txt_size = data['txt_weight'], data['txt_size']
    local txt_fg_colour, txt_fg_alpha = data['txt_fg_colour'], data['txt_fg_alpha']
    local movex = txt_radius * math.cos(angle_to_position(graph_start_angle, angle))
    local movey = txt_radius * math.sin(angle_to_position(graph_start_angle, angle))
    cairo_select_font_face (display, "ubuntu", CAIRO_FONT_SLANT_NORMAL, txt_weight)
    cairo_set_source_rgba (display, rgb_to_r_g_b(txt_fg_colour, txt_fg_alpha))
    cairo_set_font_size (display, txt_size)
    if txt_radius > 0 then
        cairo_move_to (display, x + movex - (txt_size / 2), y + movey + 3)
        cairo_show_text (display, value)
        cairo_stroke (display)
    end

    -- caption
    local caption = data['caption']
    local caption_weight, caption_size = data['caption_weight'], data['caption_size']
    local caption_fg_colour, caption_fg_alpha = data['caption_fg_colour'], data['caption_fg_alpha']
    local tox = graph_radius * (math.cos((graph_start_angle * 2 * math.pi / 360)-(math.pi/2)))
    local toy = graph_radius * (math.sin((graph_start_angle * 2 * math.pi / 360)-(math.pi/2)))
    cairo_select_font_face (display, "ubuntu", CAIRO_FONT_SLANT_NORMAL, caption_weight);
    cairo_set_font_size (display, caption_size)
    cairo_set_source_rgba (display, rgb_to_r_g_b(caption_fg_colour, caption_fg_alpha))
    cairo_move_to (display, x + tox + 5, y + toy + 3)
    -- bad hack but not enough time !
    if graph_start_angle < 105 then
        cairo_move_to (display, x + tox - 30, y + toy + 1)
    end
    cairo_show_text (display, caption)
    cairo_stroke (display)
end


-- loads data and displays gauges
function go_gauge_rings(display, border)
    local function load_gauge_rings(display, data)
        local str, value = '', 0
        if data['conky_line'] == nil then
            str = string.format('${%s %s}',data['name'], data['arg'])
        else
            str = data['conky_line']
        end
        str = conky_parse(str)
        value = tonumber(str)
        if (value == nil) then
            value = 0
        else
            value = math.floor(value + 0.5)
        end
        draw_gauge_ring(display, data, value, border)
    end

    for i in pairs(gauge) do
        load_gauge_rings(display, gauge[i])
    end

end


-- other util functions

function conky_nproc()
  return io.popen('nproc'):read('*n')
end

function cpu_freq_list()
  fl = {}
  for i=1, conky_nproc() do
    fl[i] = conky_parse('${freq ' .. i .. '}')
  end
  return fl
end

function conky_freq_min()
  return math.min(unpack(cpu_freq_list()))
end

function conky_freq_max()
  return math.max(unpack(cpu_freq_list()))
end

function conky_freq_avg()
  fl = cpu_freq_list()
  sum = 0
  for i=1, #fl do
    sum = sum + fl[i]
  end
  return sum / #fl
end


-------------------------------------------------------------------------------
--                                                                         MAIN
function conky_main()
    if conky_window == nil then
        return
    end

    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    local display = cairo_create(cs)

    go_gauge_rings(display, conky_window.border_outer_margin)

    cairo_surface_destroy(cs)
    cairo_destroy(display)

end
```

Night Train

---

### Post by Night Train on 2017-01-03
hi guys

is there someone who can help me?

I would want to modify from "name='fs_used_perc'" to "name='folder-size'" and from "arg='/'" to "arg='/path/of/folder'"

also, I believe, I should create the function in the file .lua

thank you so much

Night Train

---

### Post by paramvir on 2017-01-06
Happy new year !!!

I got your message - Amigo mio How can I forget you lol - you did all the hard work of translating conkywx to Italian ;)

Ok here is the new code. I have taken the liberty to make **some** improvements.  It is spiced up !!

I am using conky patched for lua 5.3 and tolua++ for 5.3 - so it should work with lua51 as well. Soooooo - let me know if you are doing back flips or banging your head on the wall huahahahahaha :D

I still need to share the patches with Vincent so that Ubuntu can also come up to speed ;)

In the conky.config section - use normal syntax for conky 1.10.x [PHP]lua_load = 'path to this file name.lua',[/PHP]

You can supply variables in the conky.text section - pass three variables like shown - they can be in any order. If any one of the variables is missing - the default value will be used from the gauge table. Commas are optional between variables.

[PHP]

${lua main name=folder-size,  caption=huha, arg=/home/param/backup, }

or

${lua main } will use default values arg='/' and name='fs_used_perc'


[/PHP]

In the code below - you will notice I am using **df --output='pcent'** in place of using **du** - as this gives us the percent used by the folder with respect to it's partition - which is actually what you want.

NOTE:: The folders with spaces are not handled !!!

This is the main code now::

[PHP]

require 'cairo'

local PI      = 3.14159265358979323846
local floor   = math.floor
local cos     = math.cos
local sin     = math.sin
local tonum   = tonumber
local sprintf = string.format

-- Storage rings
local gauge = {
    name='fs_used_perc',           arg='/',                  max_value=100,
    x=70,                          y=110,
    graph_radius=36, graph_thickness=8,
    graph_start_angle=180,
    graph_unit_angle=2.7,          graph_unit_thickness=2.7,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.05,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.15,
    hand_fg_colour=0xE37222,       hand_fg_alpha=0.7,
    txt_radius=26,
    txt_weight=1.0,                txt_size=8.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.7,
    graduation_radius=30,
    graduation_thickness=0,        graduation_mark_thickness=2,
    graduation_unit_angle=27,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    caption='root',
    caption_weight=0.8,            caption_size=9.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=0.5,
}

-- converts color in hexa to decimal
local function rgb_to_r_g_b(colour, alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

-- convert degree to rad and rotate (0 degree is top/north)
local function angle_to_position(start_angle, current_angle)
    local pos = current_angle + start_angle
    return ( ( pos * (2 * PI / 360) ) - (PI / 2) )
end


-- displays gauges
local function draw_gauge_ring(cr, data, value, border)
    local x, y = data.x + border, data.y + border
    local graph_end_angle = (data.max_value * data.graph_unit_angle) % 360

    -- background ring
    cairo_arc(cr, x, y, data.graph_radius, angle_to_position(data.graph_start_angle, 0), angle_to_position(data.graph_start_angle, graph_end_angle))
    cairo_set_source_rgba(cr, rgb_to_r_g_b(data.graph_bg_colour, data.graph_bg_alpha))
    cairo_set_line_width(cr, data.graph_thickness)
    cairo_stroke(cr)

    -- arc of value
    local val = value % (data.max_value + 1)
    local start_arc = 0
    local stop_arc = 0
    local i = 1
    while i <= val do
        start_arc = (data.graph_unit_angle * i) - data.graph_unit_thickness
        stop_arc = data.graph_unit_angle * i
        cairo_arc(cr, x, y, data.graph_radius, angle_to_position(data.graph_start_angle, start_arc), angle_to_position(data.graph_start_angle, stop_arc))
        cairo_set_source_rgba(cr, rgb_to_r_g_b(data.graph_fg_colour, data.graph_fg_alpha))
        cairo_stroke(cr)
        i = i + 1
    end
    local angle = start_arc

    -- hand
    start_arc = (data.graph_unit_angle * val) - (data.graph_unit_thickness)
    stop_arc = (data.graph_unit_angle * val)
    cairo_arc(cr, x, y, data.graph_radius, angle_to_position(data.graph_start_angle, start_arc), angle_to_position(data.graph_start_angle, stop_arc))
    cairo_set_source_rgba(cr, rgb_to_r_g_b(data.hand_fg_colour, data.hand_fg_alpha))
    cairo_stroke(cr)

    -- graduations marks
    if data.graduation_radius > 0 and data.graduation_thickness > 0 and data.graduation_unit_angle > 0 then
        local nb_graduation = graph_end_angle / data.graduation_unit_angle
        local i = 0
        while i < nb_graduation do
            cairo_set_line_width(cr, data.graduation_thickness)
            start_arc = (data.graduation_unit_angle * i) - (data.graduation_mark_thickness / 2)
            stop_arc = (data.graduation_unit_angle * i) + (data.graduation_mark_thickness / 2)
            cairo_arc(cr, x, y, data.graduation_radius, angle_to_position(data.graph_start_angle, start_arc), angle_to_position(data.graph_start_angle, stop_arc))
            cairo_set_source_rgba(cr,rgb_to_r_g_b(data.graduation_fg_colour,data.graduation_fg_alpha))
            cairo_stroke(cr)
            cairo_set_line_width(cr, data.graph_thickness)
            i = i + 1
        end
    end

    -- text
    local movex = data.txt_radius * cos(angle_to_position(data.graph_start_angle, angle))
    local movey = data.txt_radius * sin(angle_to_position(data.graph_start_angle, angle))
    cairo_select_font_face(cr, "ubuntu", CAIRO_FONT_SLANT_NORMAL, data.txt_weight)
    cairo_set_source_rgba(cr, rgb_to_r_g_b(data.txt_fg_colour, data.txt_fg_alpha))
    cairo_set_font_size(cr, data.txt_size)
    if data.txt_radius > 0 then
        cairo_move_to (cr, x + movex - (data.txt_size / 2), y + movey + 3)
        cairo_show_text (cr, value)
        cairo_stroke (cr)
    end

    -- caption
    local tox = data.graph_radius * (cos((data.graph_start_angle * 2 * PI / 360)-(PI/2)))
    local toy = data.graph_radius * (sin((data.graph_start_angle * 2 * PI / 360)-(PI/2)))
    cairo_select_font_face(cr, "ubuntu", CAIRO_FONT_SLANT_NORMAL, data.caption_weight);
    cairo_set_font_size(cr, data.caption_size)
    cairo_set_source_rgba(cr, rgb_to_r_g_b(data.caption_fg_colour, data.caption_fg_alpha))
    cairo_move_to(cr, x + tox + 5, y + toy + 3)
    -- bad hack but not enough time !
    if data.graph_start_angle < 105 then
        cairo_move_to(cr, x + tox - 30, y + toy + 1)
    end
    cairo_show_text(cr, data.caption)
    cairo_stroke(cr)
end

local function getFolderSize(str)
    if str then
        f1, err = io.popen( [[ df --output='pcent' ]] .. str )
        if f1 and not err then
            local rinfo = f1:read("*a")
            f1:close()
            rinfo = rinfo:gsub( ".*$%\n", '' )
            rinfo = rinfo:match( "%d+" )
            return rinfo
        else
            return nil
        end
    else
        return nil
    end
end

-- other util functions

function conky_nproc()
  return io.popen('nproc'):read('*n')
end

function cpu_freq_list()
  fl = {}
  for i=1, conky_nproc() do
    fl[i] = conky_parse('${freq ' .. i .. '}')
  end
  return fl
end

function conky_freq_min()
  return math.min(unpack(cpu_freq_list()))
end

function conky_freq_max()
  return math.max(unpack(cpu_freq_list()))
end

function conky_freq_avg()
  fl = cpu_freq_list()
  sum = 0
  for i=1, #fl do
    sum = sum + fl[i]
  end
  return sum / #fl
end


-------------------------------------------------------------------------
-- MAIN
function conky_main(...)
    if conky_window == nil then return '' end

    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    local cr = cairo_create(cs)

    local po = { caption='caption', arg='arg', name='name' }
    local p = {...}
    for i = 1, #p do
        if po[p[i]:match('(.-)=.*$')] then
            local key, val = p[i]:match('(.-)=(.-),?$')
            po[key] = val
        end
    end

    local windowSize = conky_window.border_outer_margin

    -- loads data and displays gauges
    if po.name    ~= 'name'    then gauge.name     = po.name    end
    if po.arg     ~= 'arg'     then gauge.arg      = po.arg     end
    if po.caption ~= 'caption' then gauge.caption  = po.caption end

    local str
    if gauge.name == 'folder-size' then
        str = getFolderSize(gauge.arg) or 0
    else
        str = conky_parse(sprintf('${%s %s}',gauge.name, gauge.arg))
    end

    local value = floor((tonum(str) or 0) + 0.5)
    draw_gauge_ring(cr, gauge, value, windowSize)

    cairo_surface_destroy(cs)
    cairo_destroy(cr)

    return ''

end





[/PHP]


ciao

---

### Post by oldos2er on 2017-01-06
Thread moved to *Programming Talk*

---

### Post by paramvir on 2017-01-06
@oldos2er 
Thanks - yes this is a better home for this thread

@NightTrain
Here is version 2.0

I just realised that **df** thingy will get you the same thing as **fs_used_perc** - soooo back with **du**. Now the way I have looked at it - you really cannot use just the folder size and see it on a curve! We need a percent value - and the best solution - at the moment ;) - is to use it as an alarm of sorts with a **max_size** and thus a percent of the folder size.

Example case - you have a folder which at present is about 1 Gb and you want a **max_size** of 2 Gb - you will see 50% for this folder and the gauge will nicely display the arc.

I have added another value in the gauge table **max_size** {value in Kilobytes} for this purpose. Now you can add any of the gauge elements in the command line in conky. A little more elegance in code ;)

My test case in conky.text::
[PHP]
${lua main name=folder-size,  x=150 caption=workout_2Gb, max_size=2097152
    arg=/home/param/media/Music/workout y=110 }
[/PHP]

Version 2::

[PHP]


require 'cairo'

local PI      = 3.14159265358979323846
local floor   = math.floor
local cos     = math.cos
local sin     = math.sin
local tonum   = tonumber
local sprintf = string.format

-- Storage rings
local gauge = {
    name='fs_used_perc',           arg='/',          max_value=100,
    x=70,                          y=110,            max_size=100,
    graph_radius=36, graph_thickness=8,
    graph_start_angle=180,
    graph_unit_angle=2.7,          graph_unit_thickness=2.7,
    graph_bg_colour=0xffffff,      graph_bg_alpha=0.05,
    graph_fg_colour=0xFFFFFF,      graph_fg_alpha=0.15,
    hand_fg_colour=0xE37222,       hand_fg_alpha=0.7,
    txt_radius=26,
    txt_weight=1.0,                txt_size=8.0,
    txt_fg_colour=0xFFFFFF,        txt_fg_alpha=0.7,
    graduation_radius=30,
    graduation_thickness=0,        graduation_mark_thickness=2,
    graduation_unit_angle=27,
    graduation_fg_colour=0xFFFFFF, graduation_fg_alpha=0.3,
    caption='root',
    caption_weight=0.8,            caption_size=9.0,
    caption_fg_colour=0xFFFFFF,    caption_fg_alpha=0.5,
}

-- converts color in hexa to decimal
local function rgb_to_r_g_b(colour, alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

-- convert degree to rad and rotate (0 degree is top/north)
local function angle_to_position(start_angle, current_angle)
    local pos = current_angle + start_angle
    return ( ( pos * (2 * PI / 360) ) - (PI / 2) )
end


-- displays gauges
local function draw_gauge_ring(cr, data, value, border)
    local x, y = data.x + border, data.y + border
    local graph_end_angle = (data.max_value * data.graph_unit_angle) % 360

    -- background ring
    cairo_arc(cr, x, y, data.graph_radius, angle_to_position(data.graph_start_angle, 0), angle_to_position(data.graph_start_angle, graph_end_angle))
    cairo_set_source_rgba(cr, rgb_to_r_g_b(data.graph_bg_colour, data.graph_bg_alpha))
    cairo_set_line_width(cr, data.graph_thickness)
    cairo_stroke(cr)

    -- arc of value
    local val = value % (data.max_value + 1)
    local start_arc = 0
    local stop_arc = 0
    local i = 1
    while i <= val do
        start_arc = (data.graph_unit_angle * i) - data.graph_unit_thickness
        stop_arc = data.graph_unit_angle * i
        cairo_arc(cr, x, y, data.graph_radius, angle_to_position(data.graph_start_angle, start_arc), angle_to_position(data.graph_start_angle, stop_arc))
        cairo_set_source_rgba(cr, rgb_to_r_g_b(data.graph_fg_colour, data.graph_fg_alpha))
        cairo_stroke(cr)
        i = i + 1
    end
    local angle = start_arc

    -- hand
    start_arc = (data.graph_unit_angle * val) - (data.graph_unit_thickness)
    stop_arc = (data.graph_unit_angle * val)
    cairo_arc(cr, x, y, data.graph_radius, angle_to_position(data.graph_start_angle, start_arc), angle_to_position(data.graph_start_angle, stop_arc))
    cairo_set_source_rgba(cr, rgb_to_r_g_b(data.hand_fg_colour, data.hand_fg_alpha))
    cairo_stroke(cr)

    -- graduations marks
    if data.graduation_radius > 0 and data.graduation_thickness > 0 and data.graduation_unit_angle > 0 then
        local nb_graduation = graph_end_angle / data.graduation_unit_angle
        local i = 0
        while i < nb_graduation do
            cairo_set_line_width(cr, data.graduation_thickness)
            start_arc = (data.graduation_unit_angle * i) - (data.graduation_mark_thickness / 2)
            stop_arc = (data.graduation_unit_angle * i) + (data.graduation_mark_thickness / 2)
            cairo_arc(cr, x, y, data.graduation_radius, angle_to_position(data.graph_start_angle, start_arc), angle_to_position(data.graph_start_angle, stop_arc))
            cairo_set_source_rgba(cr,rgb_to_r_g_b(data.graduation_fg_colour,data.graduation_fg_alpha))
            cairo_stroke(cr)
            cairo_set_line_width(cr, data.graph_thickness)
            i = i + 1
        end
    end

    -- text
    local movex = data.txt_radius * cos(angle_to_position(data.graph_start_angle, angle))
    local movey = data.txt_radius * sin(angle_to_position(data.graph_start_angle, angle))
    cairo_select_font_face(cr, "ubuntu", CAIRO_FONT_SLANT_NORMAL, data.txt_weight)
    cairo_set_source_rgba(cr, rgb_to_r_g_b(data.txt_fg_colour, data.txt_fg_alpha))
    cairo_set_font_size(cr, data.txt_size)
    if data.txt_radius > 0 then
        cairo_move_to (cr, x + movex - (data.txt_size / 2), y + movey + 3)
        cairo_show_text (cr, value)
        cairo_stroke (cr)
    end

    -- caption
    local tox = data.graph_radius * (cos((data.graph_start_angle * 2 * PI / 360)-(PI/2)))
    local toy = data.graph_radius * (sin((data.graph_start_angle * 2 * PI / 360)-(PI/2)))
    cairo_select_font_face(cr, "ubuntu", CAIRO_FONT_SLANT_NORMAL, data.caption_weight);
    cairo_set_font_size(cr, data.caption_size)
    cairo_set_source_rgba(cr, rgb_to_r_g_b(data.caption_fg_colour, data.caption_fg_alpha))
    cairo_move_to(cr, x + tox + 5, y + toy + 3)
    -- bad hack but not enough time !
    if data.graph_start_angle < 105 then
        cairo_move_to(cr, x + tox - 30, y + toy + 1)
    end
    cairo_show_text(cr, data.caption)
    cairo_stroke(cr)
end

local function getFolderSize(str, max)
    if str then
        f1, err = io.popen( [[ du -d 0 ]] .. str )
        if f1 and not err then
            local rinfo = f1:read("*a")
            f1:close()
            rinfo = rinfo:match( "(%d+)%s*.*" )
            return sprintf( "%2.0f", (rinfo/max)*100)
        else
            return nil
        end
    else
        return nil
    end
end

-- other util functions
function conky_nproc()
  return io.popen('nproc'):read('*n')
end

function cpu_freq_list()
  fl = {}
  for i=1, conky_nproc() do
    fl[i] = conky_parse('${freq ' .. i .. '}')
  end
  return fl
end

function conky_freq_min()
  return math.min(unpack(cpu_freq_list()))
end

function conky_freq_max()
  return math.max(unpack(cpu_freq_list()))
end

function conky_freq_avg()
  fl = cpu_freq_list()
  sum = 0
  for i=1, #fl do
    sum = sum + fl[i]
  end
  return sum / #fl
end

------------------------------------------------------
-- MAIN
function conky_main(...)
    if conky_window == nil then return '' end

    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    local cr = cairo_create(cs)

    local po = {}
    for v, _ in pairs(gauge) do po[v] = v end

    local p = {...}
    for i = 1, #p do
        if po[p[i]:match('(.-)=.*$')] then
            local key, val = p[i]:match('(.-)=(.-),?$')
            gauge[key] = val
        end
    end

    local windowSize = conky_window.border_outer_margin

    local str
    if gauge.name == 'folder-size' then
        str = getFolderSize(gauge.arg, gauge.max_size) or 0
    else
        str = conky_parse(sprintf('${%s %s}',gauge.name, gauge.arg))
    end

    local value = floor((tonum(str) or 0) + 0.5)
    draw_gauge_ring(cr, gauge, value, windowSize)

    cairo_surface_destroy(cs)
    cairo_destroy(cr)

    return ''

end



[/PHP]

---

