---
title: "[SOLVED] conky problem"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by inter-m on 2008-06-15
i just installed conky and im really happy with it... but there is one problem that i cant overcome... the problem is whenever i start my laptop conky starts "which is what i want" but when i start any application conky is always on top... and the only solution i found is for me to kill conky and then restart it again... i hope someone can help with this and thanx in advance...

K.H.

---

### Post by MasterSander on 2008-06-15
I think you can edit it in your conky config file which you should have placed in your home directory.

---

### Post by RSingh on 2008-06-15
try editing your startup command with this which will delay its startup by a bit and should fix your problem
```

sleep 10 && conky
```

---

### Post by inter-m on 2008-06-15
this is my conkyrc file im bit confused where should i do the editing...
```
# UBUNTU-CONKY
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
sda1:  ${fs_free_perc /dev/sda1}%   ${fs_bar 6 /dev/sda1}$color
hdb3:  ${fs_free_perc /media/hdb3}%   ${fs_bar 6 /media/hdb3}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

---

### Post by RSingh on 2008-06-15
actually you dont need to edit the conkyrc file. Its the startup command (SYSTEM >> PREFERENCES/ADMINISTRATION >> SESSIONS).

The line: 
```

sleep 10 && conky
```

should be used instead of the default command.

---

### Post by inter-m on 2008-06-18
> **RSingh said:**
> actually you dont need to edit the conkyrc file. Its the startup command (SYSTEM >> PREFERENCES/ADMINISTRATION >> SESSIONS).

The line: 
```

sleep 10 && conky
```

should be used instead of the default command.

i tried it but i think i didnt do it correctly cuz conky wouldnt start now with startup... check out the attachments...

---

### Post by RSingh on 2008-06-19
from what I see, the command you have written is:
```

sleep 10&& /usr/bin/conky
```

try changing it to:

```
sleep 10 && conky
```

Note: Take care of the space between 10 and '&&'

---

### Post by jolx on 2008-06-19
in ur conkyrc u could change 'own_window_type' from override to normal, that solved my problem the only problem is then it wont always  show all of the fortune

---

### Post by inter-m on 2008-06-22
> **jolx said:**
> in ur conkyrc u could change 'own_window_type' from override to normal, that solved my problem the only problem is then it wont always  show all of the fortune

that fixed my problem thanx... now i need to figure out better ways to configure my conkyrc file... thanx all... :)

K.H.

---

### Post by aktiwers on 2008-06-22
There is tons of tips and inspiration here:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by Sunships on 2009-02-14
> **inter-m said:**
> that fixed my problem thanx... now i need to figure out better ways to configure my conkyrc file... thanx all... :)

K.H.

I'd like to add that I had the same problem, and tried all the startup script solutions, but only changing from "override" to "normal" worked in then end. :)

---

