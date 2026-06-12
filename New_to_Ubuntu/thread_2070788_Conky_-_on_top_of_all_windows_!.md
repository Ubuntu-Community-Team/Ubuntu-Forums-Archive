---
title: "Conky - on top of all windows !"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by mattyjames on 2012-10-13
Hi folks!  Ive installed conky on my Ubuntu install (precise/gnome classic) and no matter what i do in the .conkyrc file (background true) it still sits on top of any open windows. 

Please help ! Ive apt-get purge conky - reinstalled - just about everything ! Please help!!!!!

Here is my .conkyrc file........


> #==============================================================================
#                               conkyrc_lunatico
#
#  Date    : 22/06/2011
#  author  : DCM
#  version : v0.2
#  license : Distributed under the terms of GNU GPL version 2 or later
#  This version is a modification of conkyrc_orange found at
#    [http://gnome-look.org/content/show.php?content=137503&forumpage=0](http://gnome-look.org/content/show.php?content=137503&forumpage=0)
#
#==============================================================================

background true

update_interval 1

cpu_avg_samples 2
net_avg_samples 2
temperature_unit celsius

double_buffer yes
no_buffers yes
text_buffer_size 2048

gap_x 10
gap_y 100
minimum_size 180 500
maximum_width 180
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
alignment tr

draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5
uppercase no

default_color FFFFFF
color1 DDDDDD
color2 AAAAAA
color3 888888
color4 1734F0

lua_load ~/.conky/conky_lunatico.lua
lua_draw_hook_post main


TEXT
${font Ubuntu:size=7,weight:bold}${color4}SYSTEM ${hr 2}
${offset 10}${font Ubuntu:size=7,weight:normal}${color1}$sysname $kernel
${offset 10}${font Ubuntu:size=7,weight:normal}${color1}$nodename
${offset 10}${font Ubuntu:size=7,weight:normal}${color1}Uptime: $uptime

${voffset 10}
${offset 65}${cpugraph 20,110 666666 666666}${voffset -15}
${offset 45}${font Ubuntu:size=7,weight:bold}${color}CPU
${offset 55}${font Ubuntu:size=7,weight:normal}${color4}${top name 1}${alignr}${top cpu 1}%
${offset 55}${font Ubuntu:size=7,weight:normal}${color1}${top name 2}${alignr}${top cpu 2}%
${offset 55}${font Ubuntu:size=7,weight:normal}${color2}${top name 3}${alignr}${top cpu 3}%
${offset 55}${font Ubuntu:size=7,weight:normal}${color3}${top name 4}${alignr}${top cpu 4}%
${offset 55}${font Ubuntu:size=7,weight:normal}${color3}${top name 5}${alignr}${top cpu 5}%

${voffset 24}
${offset 45}${font Ubuntu:size=7,weight:bold}${color}MEM
${offset 55}${font Ubuntu:size=7,weight:normal}${color4}${top_mem name 1}${alignr}${top_mem mem 1}%
${offset 55}${font Ubuntu:size=7,weight:normal}${color1}${top_mem name 2}${alignr}${top_mem mem 2}%
${offset 55}${font Ubuntu:size=7,weight:normal}${color2}${top_mem name 3}${alignr}${top_mem mem 3}%
${offset 55}${font Ubuntu:size=7,weight:normal}${color3}${top_mem name 4}${alignr}${top_mem mem 4}%
${offset 55}${font Ubuntu:size=7,weight:normal}${color3}${top_mem name 4}${alignr}${top_mem mem 5}%

${voffset 8}
${offset 65}${diskiograph 20,110 666666 666666}${voffset -15}
${offset 45}${font Ubuntu:size=7,weight:bold}${color}DISK
#${offset 55}${diskiograph 20,150 666666 666666}${voffset -30}
${offset 55}${font Ubuntu:size=7,weight:normal}${color}Used: ${fs_used /}

${voffset 65}
${offset 10}${font Ubuntu:size=7,weight:bold}${color}ETHERNET             WIRELESS
${offset 10}${color2}${addr eth0}${alignr}${addr wlan0}
#${offset 10}${color}Up: $color2${upspeed eth0} ${alignr}${color}Down: $color2${downspeed wlan0}
#${offset 10}${color}Down: $color2${downspeed eth0} ${alignr}${color}Down: $color2${downspeed wlan0}
${color4}${hr 2}

:confused:

Thanks in advance,

Matt

---

### Post by PaulInBHC on 2012-10-13
I don't know enough to help you but conky is an addiction.

This thread will keep you busy for a long while

[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

There is also a thread in the Community Cafe with shots and configs.

---

### Post by Wim Sturkenboom on 2012-10-13
Below the beginning of my conkyrc file. It's transparent in Unity. You can try it or compare with yours.


```

alignment top_right
background no
border_width 1
cpu_avg_samples 2
default_color white
#default_color lightblue
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=9
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky

#own_window_type desktop
own_window_type override

#WimS
# make it transparent
own_window_transparent yes
# prevent garbled display when info is updated
double_buffer yes

stippled_borders 0
update_interval 3.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

```

---

### Post by ajgreeny on 2012-10-13
Here is the important parts of my .conkyrc file which affect the window display, with variations from your version shown in red.  Mine works great on 12.04, and like you, I do not run unity but the gnome classic desktop without effects.
```
# set to yes if you want Conky to be forked in the background
background [COLOR=Red]yes[/COLOR]

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type [COLOR=Red]normal[/COLOR]

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by mattyjames on 2012-10-13
:) ajgreeny ! You are indeed the man! :) Thanks mate now my desktop is looking the mutleys nutleys, aaand conky is behaving !


Happy days !

\\:D/\\:D/\\:D/\\:D/\\:D/

---

### Post by ajgreeny on 2012-10-13
Great!

Now can you mark the thread as solved from the Thread Tools menu at the top.

---

