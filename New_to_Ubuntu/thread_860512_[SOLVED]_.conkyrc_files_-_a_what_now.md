---
title: "[SOLVED] .conkyrc files - a what now?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-07-15
I'm going to sound very silly here but what is a .conkyrc file?

can someone pity me with an answer :)

thanks

---

### Post by ibuclaw on 2008-07-15
It is the residual configuration file for the program conky... (something tells me that will need more explanation than that...) :D

Regards
Iain

---

### Post by halitech on 2008-07-15
I'll break it down a little more for you :)

.conkyrc is the file that conky will look for to determine what information is shown on the desktop when you have conky running. it is completely customizable to show whatever you want and to take out what you don't want.

---

### Post by Joeb454 on 2008-07-15
It's located in your /home/user/ directory (they're often referred to as ~/.conkyrc which is the same place).

Here's mine ```
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

${color #989898}Processes: ${color }$processes     $alignr${color #989898}Running:   ${color }$running_processes
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
$alignc${fs_bar 5,100 /}    ${fs_used_perc /}% Used

${color #989898}Home:    ${color }${fs_used /home}/${fs_size /home}
$alignc${fs_bar 5,100 /home}    ${fs_used_perc /home}% Used
${color #ddaa00}$stippled_hr
$alignc${color #989898}Latest Headlines:
${color lightgrey}$alignc${rss http://newsrss.bbc.co.uk/rss/newsonline_uk_edition/technology/rss.xml 5 item_title 0}
${color #ddaa00}$alignc${rss http://newsrss.bbc.co.uk/rss/newsonline_uk_edition/technology/rss.xml 5 item_title 1}
${color lightgrey}$alignc${rss http://newsrss.bbc.co.uk/rss/newsonline_uk_edition/technology/rss.xml 5 item_title 2}
${color #ddaa00}$stippled_hr
${color #989898}Network Info: 
$alignc${color #ddaa00}  Up${color}/${color #ddaa00}Total: ${color }${upspeed wlan0} kb/s    ${totalup wlan0}
$alignc${color #ddaa00}Down${color}/${color #ddaa00}Total: ${color }${downspeed wlan0} kb/s    ${totaldown wlan0}

${color #989898}Wireless Strength: ${color}  ${wireless_link_bar 5,100 wlan0}   ${wireless_link_qual wlan0}%
${color #989898}Wireless SSID/Bitrate: ${color} $alignc${wireless_essid wlan0}    ${wireless_bitrate wlan0}

${color #989898}IP: ${color} ${addr wlan0}   |   ${color #989898}Public IP: ${color }${execi 7200 wget -O - http://whatismyip.org/ | tail}

${color #989898}Gmail: ${color #ddaa00}${execi 120 perl ~/.scripts/gmail.pl n} Unread Messages
```

---

### Post by wariskampar on 2008-07-15
i'll add a bit more;

to edit it you enter this code;

sudo gedit ~/.conkyrc 

by default, there is no .conkyrc file

---

### Post by Dr Small on 2008-07-15
> **wariskampar said:**
> i'll add a bit more;

to edit it you enter this code;

sudo gedit ~/.conkyrc 

by default, there is no .conkyrc file
No need for sudo if it is in your Home Directory. ;)

---

### Post by wariskampar on 2008-07-15
oopp...my mistake!:)

---

### Post by phantomjoker on 2008-07-15
> **halitech said:**
> I'll break it down a little more for you :)

.conkyrc is the file that conky will look for to determine what information is shown on the desktop when you have conky running. it is completely customizable to show whatever you want and to take out what you don't want.

So in simple terms it....

plus - what is conky?!

thanks guys

---

### Post by Dr Small on 2008-07-15
> **phantomjoker said:**
> So in simple terms it....

plus - what is conky?!

thanks guys
Conky Screenshots:
[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

---

### Post by halitech on 2008-07-15
there are also a few threads on here on setting it up and screenshots and sample .conkyrc files for you to look at. I use it on my main desktop and on my laptop (old P3 750) and no hit on performance on either machine as long as you don't include any heavy apps.

---

