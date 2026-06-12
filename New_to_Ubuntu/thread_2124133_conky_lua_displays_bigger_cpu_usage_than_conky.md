---
title: "conky lua displays bigger cpu usage than conky"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by Froylan on 2013-03-09
I edited the conky lua rings 
here is the conkyrc file ```
background yes
use_xft yes
xftfont 123:size=7
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager,below
double_buffer yes
minimum_size 180 500
maximum_width 800
draw_shades no
format_human_readable yes
draw_outline no
draw_borders no
draw_graph_borders no
default_color gray
default_shade_color red
default_outline_color green
alignment top_left
gap_x 50
gap_y 0
no_buffers no
uppercase no
cpu_avg_samples 4
cpu_avg_samples 3
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes
text_buffer_size 25
# Lua Load  #
lua_load ~/.lua/scripts/clock_rings.lua
lua_draw_hook_pre clock_rings

TEXT
${font openlogos:size=20}THE ${font Arial:size=20}${color Tan1}KILLING ${color Ivory}OS ${font openlogos:size=20}
${color slate grey}${time %a, } ${color }${time %e %B %G}
${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}
${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
CPU0  ${cpu cpu0}% ${cpubar cpu0}
CPU1  ${cpu cpu1}% ${cpubar cpu1}
CPU2  ${cpu cpu2}% ${cpubar cpu2}
CPU3  ${cpu cpu3}% ${cpubar cpu3}
cpu4  ${cpu cpu4}% ${cpubar cpu4}
${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar
${font Arial:bold:size=10}${color Tan1}HOME FOLDER ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 1}${alignr}${top mem 1} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %
${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
Strength: ${wireless_link_qual_perc wlan0}% $alignr 
$font${color DimGray}IP on wlan0 $alignr ${addr wlan0}
Down $alignr ${downspeed wlan0}
Up $alignr ${upspeed wlan0}
have: $alignr  ${totaldown wlan0}
given: $alignr  ${totalup wlan0}
${image /home/froylan/Pictures/umbrella_lua.png -s 319x249 -p -90,475}
${voffset 900}
${offset 250}
```

here is the clock_rings.lua ```
--[[
Clock Rings by Linux Mint (2011) reEdited by despot77

This script draws percentage meters as rings, and also draws clock hands if you want! It is fully customisable; all options are described in the script. This script is based off a combination of my clock.lua script and my rings.lua script.

IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.

To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/clock_rings.lua
    lua_draw_hook_pre clock_rings
    
Changelog:
+ v1.0 -- Original release (30.09.2009)
   v1.1p -- Jpope edit londonali1010 (05.10.2009)
*v 2011mint -- reEdit despot77 (18.02.2011)
]]

settings_table = {
    {
        name='cpu',
        arg='cpu1',
        max=60,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xFF6600,
        fg_alpha=0.4,
        x=100, y=600,
        radius=56,
        thickness=5,
        start_angle=0,
        end_angle=360
    },
    {
        name='cpu',
        arg='cpu2',
        max=60,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xFF6600,
        fg_alpha=0.6,
        x=100, y=600,
        radius=62,
        thickness=5,
        start_angle=0,
        end_angle=360
    },
    {
        name='cpu',
        arg='cpu3',
        max=31,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xFF6600,
        fg_alpha=0.8,
        x=100, y=600,
        radius=70,
        thickness=5,
        start_angle=0,
        end_angle=360
    },
    {
        name='cpu',
        arg='cpu4',
        max=12,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xFF6600,
        fg_alpha=1,
        x=100, y=600,
        radius=76,
        thickness=5,
        start_angle=0,
        end_angle=360
    },
}
-- Use these settings to define the origin and extent of your clock.


-- "clock_x" and "clock_y" are the coordinates of the centre of the clock, in pixels, from the top left of the Conky window.

clock_x=100
clock_y=150

show_seconds=true

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(cr,t,pt)
    local w,h=conky_window.width,conky_window.height
    
    local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

    local angle_0=sa*(2*math.pi/360)-math.pi/2
    local angle_f=ea*(2*math.pi/360)-math.pi/2
    local t_arc=t*(angle_f-angle_0)

    -- Draw background ring

    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
    
    -- Draw indicator ring

    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
end

function draw_clock_hands(cr,xc,yc)
    local secs,mins,hours,secs_arc,mins_arc,hours_arc
    local xh,yh,xm,ym,xs,ys
    
    secs=os.date("%S")    
    mins=os.date("%M")
    hours=os.date("%I")
        
    secs_arc=(2*math.pi/60)*secs
    mins_arc=(2*math.pi/60)*mins+secs_arc/60
    hours_arc=(2*math.pi/12)*hours+mins_arc/12
        
    -- Draw hour hand
    
    xh=xc+0.7*clock_r*math.sin(hours_arc)
    yh=yc-0.7*clock_r*math.cos(hours_arc)
    cairo_move_to(cr,xc,yc)
    cairo_line_to(cr,xh,yh)
    
    cairo_set_line_cap(cr,CAIRO_LINE_CAP_ROUND)
    cairo_set_line_width(cr,5)
    cairo_set_source_rgba(cr,1.0,1.0,1.0,1.0)
    cairo_stroke(cr)
    
    -- Draw minute hand
    
    xm=xc+clock_r*math.sin(mins_arc)
    ym=yc-clock_r*math.cos(mins_arc)
    cairo_move_to(cr,xc,yc)
    cairo_line_to(cr,xm,ym)
    
    cairo_set_line_width(cr,3)
    cairo_stroke(cr)
    
    -- Draw seconds hand
    
    if show_seconds then
        xs=xc+clock_r*math.sin(secs_arc)
        ys=yc-clock_r*math.cos(secs_arc)
        cairo_move_to(cr,xc,yc)
        cairo_line_to(cr,xs,ys)
    
        cairo_set_line_width(cr,1)
        cairo_stroke(cr)
    end
end

function conky_clock_rings()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
        
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
        
        value=tonumber(str)
        pct=value/pt['max']
        
        draw_ring(cr,pct,pt)
    end
    
    -- Check that Conky has been running for at least 5s

    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    
    local cr=cairo_create(cs)    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
    end
    
    draw_clock_hands(cr,clock_x,clock_y)
end
```

---

