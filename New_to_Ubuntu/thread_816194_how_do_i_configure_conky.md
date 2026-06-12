---
title: "how do i configure conky"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-06-02
i want to mount it to my desktop and have it start on startup preferably anyone know how to do that or has a system monitor thats easy to work with?

---

### Post by Joeb454 on 2008-06-02
I'm not sure about adding it to conky, but you need a .conkyrc file in your home folder (a.k.a in **~/.conkyrc**) If you want a sample one you can have mine

Please find it below

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
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 1

# Minimum size of text area
minimum_size 200 5

#maximum size
maximum_size 150 1

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 15

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=7.5
xftalpha 0.8

#Add this for Network Up/Down graphs
#${upspeedgraph eth1 20,130 000000 ffffff}
#${downspeedgraph eth1 20,130 000000 ffffff}

#${color #989898}Swap: ${color } $swap/$swapmax
#$alignc${swapbar 5,100}    $swapperc%

TEXT
$alignc ${color #ddaa00}$sysname    $machine

${color #989898}Date: ${color #ddaa00}${time %a, } ${color }${time %e %B %G}
${color #989898}Time: ${color }${time %H:%M:%S} ${color 
#ddaa00}${time %Z,    }
${color #989898}Up Time: ${color }$uptime
${color #989898}Kernel: ${color }$kernel ${color #ddaa00}@ ${color 
}$nodename 
${color #989898}Power: ${color }${battery BAT1} $alignr ${battery_time BAT1}          
${color #ddaa00}$stippled_hr
${color #989898}Intel(R) Core(TM)2 CPU$alignr ${color #ddaa00}Temp: ${color #989898}$acpitemp${color #ddaa00}c${color #989898}
T5300 ${color #ddaa00} @ ${color #989898}1.73Ghz

${color #ddaa00}Core 1: $color${freq 1} MHz
$alignc${color lightgrey}${cpubar 5, 100 cpu1}$color  ${cpu cpu1}%
${color #ddaa00}Core 2: $color${freq 2} MHz
$alignc${color lightgrey}${cpubar 5, 100 cpu2}$color  ${cpu cpu2}%

${color #989898}Processes: ${color }$processes  
${color #989898}Running:   ${color }$running_processes
${color #ddaa00}$stippled_hr
${color #989898}Highest CPU:
${color #ddaa00} ${top name 1}$alignr${top_mem cpu 1}            
${color lightgrey} ${top name 2}$alignr${top cpu 2}            
${color lightgrey} ${top name 3}$alignr${top cpu 3}            
${color lightgrey} ${top name 4}$alignr${top cpu 4}            

${color #989898}Highest RAM:
${color #ddaa00} ${top_mem name 1}$alignr${top_mem mem 1}            
${color lightgrey} ${top_mem name 2}$alignr${top_mem mem 2}            
${color lightgrey} ${top_mem name 3}$alignr${top_mem mem 3}            
${color lightgrey} ${top_mem name 4}$alignr${top_mem mem 4}            
${color #ddaa00}$stippled_hr
${color #989898}RAM:  ${color } $mem/$memmax
$alignc${membar 5,100}    $memperc% Used

${color #989898}Root:    ${color }${fs_used /}/${fs_size /}
$alignc${fs_bar 5,100 /}    ${fs_free_perc /}% Free

${color #989898}Home:    ${color }${fs_used /home}/${fs_size /home}
$alignc${fs_bar 5,100 /home}    ${fs_free_perc /home}% Free
${color #ddaa00}$stippled_hr
${color #989898}Network Info: 
$alignc${color #ddaa00}Up: ${color }${upspeed eth1} kb/s
$alignc${color #989898}Total Up: ${color }${totalup eth1}

$alignc${color #ddaa00}Down: ${color }${downspeed wlan0}kb/s${color}
$alignc${color #989898}Total Down: ${color }${totaldown wlan0}

${color #989898}Wireless Strength: ${color}
$alignc${wireless_link_bar 5, 100wlan0}    ${wireless_link_qual wlan0}%
${color #989898}Wireless SSID/Bitrate: ${color} 
$alignc${wireless_essid wlan0}    ${wireless_bitrate wlan0}

${color #989898}IP: ${color} ${addr wlan0}   |   ${color #989898}Public IP: ${color }${execi 7200 wget -O - http://whatismyip.org/ | tail}

```

---

### Post by TeoBigusGeekus on 2008-06-02
You need to create a file called .conkyrc in your /home folder where you will have your conky configuration.
You also need to create a script for conky to start upon boot up. Only thing is, you need to put a line in your script to have conky load a bit later than compiz, else it will be on top of everything on your Desktop. So the script should be something like 
```
sleep 10
conky
```
Save it somewhere and go to sessions to make it run upon startup.

As for the .conkyrc file, there is a terrific thread with many wonderful ideas.
[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

Look at this page as well
[http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")

---

### Post by Joeb454 on 2008-06-02
I can't use ```
sleep 10
conky
```

Because it slows my login down until conky has started for some reason, so I just start conky manually, after my wireless has initialised :)

---

### Post by PatrickMoore on 2008-06-02
> **TeoBigusGeekus said:**
> You need to create a file called .conkyrc in your /home folder where you will have your conky configuration.
You also need to create a script for conky to start upon boot up. Only thing is, you need to put a line in your script to have conky load a bit later than compiz, else it will be on top of everything on your Desktop. So the script should be something like 
```
sleep 10
conky
```
Save it somewhere and go to sessions to make it run upon startup.

As for the .conkyrc file, there is a terrific thread with many wonderful ideas.
[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

Look at this page as well
[http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")

how do you create the file?

---

### Post by TeoBigusGeekus on 2008-06-02
Have you tried with different values, i.e
sleep 7
or 
sleep 5

---

### Post by TeoBigusGeekus on 2008-06-02
Open a terminal and type
```
gedit ~/home/.conkyrc
```
Copy and paste the configuration file of your liking, do the alterations necessary to your system and save.

---

### Post by bumanie on 2008-06-02
Follow this:
 One thing you need to do if you want to auto start conky is make sure there is delay before it loads. In the past it conflicted with compiz and beryl and I don't know if that has ever been fixed. To do that, create a text file called .conky_start.sh and past this text:

#!/bin/bash
sleep 60 && conky;

Save it and then from a terminal type

chmod a+x .conky_start.sh

Then in system-preferences-session-startup programs add a line for .conky_start.sh

That should cause it to wait 60 seconds before starting conky and should be enough to allow compiz to load first. Of course, if you are not using compiz then this probably won't fix the problem.
It comes from [here]("https://answers.launchpad.net/ubuntu/+question/20811")

---

### Post by PatrickMoore on 2008-06-02
looks fabulous thanks guys

---

