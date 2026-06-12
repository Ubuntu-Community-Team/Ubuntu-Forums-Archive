---
title: "Conky on Ubuntu 11.10"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by Deerhunter01 on 2013-02-19
Hey guys, King noob here, this has probably be asked many times but i cant find it, so sorry.

Im trying to get conky working, i have the conkyrc file and the conky theme i want 

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
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

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
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
```


But its not working when i save it, i came from crunchbang and conky was so easy there. Maybe im missing something.

If anyone could help me out, that would be great..

---

### Post by Frogs Hair on 2013-02-19
You may have done this but here it goes.```
 sudo apt-get install conky-all
``` ```
sudo apt-get install lm-sensors
``` ```
sudo sensors-detect
``` Answer Yes to all questions and close the terminal 

Name the theme text any name conkyrc and save.Copy the conkyrc to home and press Ctrl + H to show hidden folders. Rename the text file .conkyrc and close home. Use Alt + F2 and type conky.

Themes with Lua rings will require different types of hidden folders.

Edit: You may have to play with the x-y alignment if using Unity.

---

### Post by Deerhunter01 on 2013-02-19
Life saver, thanks.

Just one more thing, if i want to change my conky theme later, do i just paste it in conkyrc, save it and run conky again..

---

### Post by Frogs Hair on 2013-02-19
Delete the old .conkyrc and add the new to hidden folders. I keep my original rc files in a folder and copy to home when I want to use them.

---

### Post by deadflowr on 2013-02-19
> **Deerhunter01 said:**
> Life saver, thanks.

Just one more thing, if i want to change my conky theme later, do i just paste it in conkyrc, save it and run conky again..

You can run different versions of conky by using the --config flag

```
conky --config path to file
```

This way you don't have to erase your old and known to work conkyrc file.
I just create a hidden folder .conky and throw all my "let's see if this will work" conkyrc files in it.
Then to launch just run the above command with the path and name(You can name it whatever you'd like, not just conkyrc)

---

