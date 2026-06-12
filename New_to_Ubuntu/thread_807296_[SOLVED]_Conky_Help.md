---
title: "[SOLVED] Conky Help"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-25
Im not sure if this is posted in the right place 

But I installed Conky .. using this tutorial [here]("http://ubuntuforums.org/showthread.php?t=205865&highlight=Lm-sensors")

Everything is working but ......  

the conky window even though it appears to be on the desk top  it covers up everything

ie I can see the desk top surface but not any open windows behind it


any
ideas?

---

### Post by EXCiD3 on 2008-05-25
I think you just dont have the .conkyrc configuration correct. If you could post the first part of your .conkyrc then i can see what the problem is. Most likely you dont have one of the "own_window" options set right or maybe you have a compiz setting wrong (if you are running compiz).

Also you don't have to compile conky from source anymore. :) A simple search through synaptic or in terminal: ```
sudo apt-get install conky
``` will suffice.

---

### Post by Joeb454 on 2008-05-25
As EXCiD3 said - can you post your ~/.conkyrc file please? That way we can see what your conky is like, and check all the options in it :)

---

### Post by hufferd on 2008-05-25
> **Joeb454 said:**
> As EXCiD3 said - can you post your ~/.conkyrc file please? That way we can see what your conky is like, and check all the options in it :)

here it is 

> # UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}$color
hdb3:  ${fs_free_perc /media/hdb3}%   ${fs_bar 6 /media/hdb3}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}


This is my conkyrc file

Have a look and let me know


Thanks D :)

---

### Post by hufferd on 2008-05-25
> **EXCiD3 said:**
> I think you just dont have the .conkyrc configuration correct. If you could post the first part of your .conkyrc then i can see what the problem is. Most likely you dont have one of the "own_window" options set right or maybe you have a compiz setting wrong (if you are running compiz).

Also you don't have to compile conky from source anymore. :) A simple search through synaptic or in terminal: ```
sudo apt-get install conky
``` will suffice.

And yes I got that far 

:)

---

### Post by EXCiD3 on 2008-05-25
"own_window_type override" should be "normal" instead.

Haha i figured as much that you got that far :P just checking!

---

### Post by hufferd on 2008-05-25
> **EXCiD3 said:**
> "own_window_type override" should be "normal" instead.

Haha i figured as much that you got that far :P just checking!

:lolflag: I couldn't help it I had to say that hehe  

Ok thanks I will try that in the config file ... And while we are talking about this two more things came to mind...    my cpu temp is show 0 although I have an applet that shows the right temp in the task bar right now....  

also any hints as to how to change the back ground of the conky window or the color of the letters in it?? 

Thanks for you time I will let you know here in a second if I have any other issues :)

---

### Post by EXCiD3 on 2008-05-25
Not sure about the cpu temp showing 0 but for the colors you can set the default colors like this for example:
```
# Default colors and also border colors
default_color black
default_shade_color black
default_outline_color black
```

And to use other colors use this after the "TEXT" portion:
```
${color #606060} (if you know the hex value of the color you want)

or

${color white} (if you want to use a predefined color)
```

---

### Post by hufferd on 2008-05-25
> **EXCiD3 said:**
> Not sure about the cpu temp showing 0 but for the colors you can set the default colors like this for example:
```
# Default colors and also border colors
default_color black
default_shade_color black
default_outline_color black
```

And to use other colors use this after the "TEXT" portion:
```
${color #606060} (if you know the hex value of the color you want)

or

${color white} (if you want to use a predefined color)
```

wow thats great thanks for all your help on this and since I fixed that one line everything is working fine 

Thanks again !
D

:KS

---

### Post by EXCiD3 on 2008-05-25
> **hufferd said:**
> wow thats great thanks for all your help on this and since I fixed that one line everything is working fine 

Thanks again !
D

:KS

No problem just here to help, plus i love conky!! :D

---

