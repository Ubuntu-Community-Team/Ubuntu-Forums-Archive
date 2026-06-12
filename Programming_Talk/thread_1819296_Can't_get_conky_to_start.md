---
title: "Can't get conky to start"
date: 2011-08-05
forum: Programming Talk
---

### Post by slashwannabe94 on 2011-08-05
Hello all, i am trying to start conky on boot and so far i'm having no luck.

My .conkyrc file is as follows: 

```

# sTaTiC's .conkyrc
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft true0

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase yes  # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_argb_visual yes
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 50

# stuff after 'TEXT' will be formatted on screen

use_xft yes
xftfont 123:size=8
xftalpha 0.1

TEXT

${offset 240}${color #ddaa00}${time %a, } ${color }${time %e %B %G}
${offset 240}${color #ddaa00}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color #ddaa00}UpTime: ${color }$uptime
${offset 240}${color #ddaa00}Kern:${color }$kernel
${offset 240}${color #ddaa00}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 #ddaa00}
${offset 240}${color #ddaa00}Load: ${color }$loadavg
${offset 240}${color #ddaa00}Processes: ${color }$processes  
${offset 240}${color #ddaa00}Running:   ${color }$running_processes

${offset 240}${color #ddaa00}Highest CPU Processes:
${offset 240}${color lightgrey} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color #ddaa00}Highest RAM Processes:
${offset 240}${color lightgrey} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color #ddaa00}RAM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color #ddaa00}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color #ddaa00}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color #ddaa00}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}

#ppp0 interface graphs
${offset 240}${color #ddaa00}NET PPP0: 
${offset 240}${color}Up: ${color }${upspeed ppp0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed ppp0}k/s${color}
${offset 240}${downspeedgraph ppp0 20,130 000000 ffffff}

#wlan0 interface graphs
${offset 240}${color #ddaa00}NET WLAN0:
${offset 240}${color}Up: ${color }${upspeed wlan0} k/s
${offset 240}${upspeedgraph wlan0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed wlan0}k/s${color}
${offset 240}${downspeedgraph wlan0 20,130 000000 ffffff}

#mon0 interface graphs
${offset 240}${color #ddaa00}NET MON0:
${offset 240}${color}Up: ${color }${upspeed mon0} k/s
${offset 240}${upspeedgraph mon0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed mon0}k/s${color}
${offset 240}${downspeedgraph mon0 20,130 000000 ffffff}

#eth0 interface graphs
${offset 240}${color #ddaa00}NET ETH0:
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

```

I have also tried using the command below to start on boot but it still doesn't start. 

```
sudo update-rc.d /etc/init.d/conky.sh defaults
```

The output of that command is:
```

static@static-desktop:/etc/init.d$ sudo update-rc.d conky.sh defaults
update-rc.d: warning: /etc/init.d/conky.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/conky.sh ...
   /etc/rc0.d/K20conky.sh -> ../init.d/conky.sh
   /etc/rc1.d/K20conky.sh -> ../init.d/conky.sh
   /etc/rc6.d/K20conky.sh -> ../init.d/conky.sh
   /etc/rc2.d/S20conky.sh -> ../init.d/conky.sh
   /etc/rc3.d/S20conky.sh -> ../init.d/conky.sh
   /etc/rc4.d/S20conky.sh -> ../init.d/conky.sh
   /etc/rc5.d/S20conky.sh -> ../init.d/conky.sh

```

The script conky.sh simply contains 
```

#!/bin/bash
conky

```

Any help is much appreciated guys, 

Thank you, 
SlashWannabe94

---

### Post by Habitual on 2011-08-05
[General Help](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by whatthefunk on 2011-08-05
Try to put a delay in your bash script.  

```
#!/bin/bash
sleep 60
conky
```

This will hold the startup for 60 sec to allow other things on your desktop to settle first.

Also, Im assuming that your script is executable?  Have you tested it?

---

### Post by slashwannabe94 on 2011-08-06
> **whatthefunk said:**
> Try to put a delay in your bash script.  

```
#!/bin/bash
sleep 60
conky
```This will hold the startup for 60 sec to allow other things on your desktop to settle first.

Also, Im assuming that your script is executable?  Have you tested it?

Yes it is, i ran the ```
chmod +x /etc/init.d/conky.sh
``` command.

---

### Post by whatthefunk on 2011-08-06
Have you tried using the GUI?

---

### Post by slashwannabe94 on 2011-08-11
> **whatthefunk said:**
> Have you tried using the GUI?

It worked, i used the GUI. Thanks for the suggestion :)

---

