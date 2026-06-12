---
title: "[SOLVED] Question on conky"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-05-20
I just installed conky and have a question. I used the ```
sudo apt-get install conky
```and then I made a .conkyrc that looks like ```
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
own_window Desktop
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
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

```Now to my question, I wanted to test it so I loaded a terminal and used the command ```
conky
```This loaded it onto my desktop. Is there a way to lower it a little bit? Also, when I close conky it stays on the desktop. The program stops ( at least I think it does) but it stays on the desktop.

---

### Post by Dr Small on 2008-05-20
As for conky not working, run:
```
conky&
```

Or simply launch it from the Run dialog.

---

### Post by Inxsible on 2008-05-20
Just add a couple of blank lines between TEXT and the first line after that to lower it a bit.

and use Alt + F2 and type in ```
conky&
```That way you dont have to keep the terminal around. and it should get off the screen once you kill conky.

---

### Post by muadnu on 2008-05-20
To lower it simply increase the value next to "gap y" in your .conkyrc file.

As for the other question, if I understood what you are doing, I think the default behavior of conky is to be started on the background when you start it, meaning that even if you start it from a terminal and then close it, conky will still run. If the output of conky that you see in the desktop stops being updated, though, it would mean that this is not what's happening...

---

### Post by slughappy1 on 2008-05-20
I did not want conky to run on its own, that's why I didn't use the command ```
conky &
```But muadnu, that's exactly what is happening. When I close conky it stays on the desktop, but it does not update anymore.

About lowering it, I figured it out right before you guys told me. I just entered another blank line between TEXT and the commands. Thanks though

---

### Post by slughappy1 on 2008-05-20
Oh another quick question. Did anyone else have conky make the desktop icons disappear? They come up sometimes, but are not shown most of the time. It is weird and I don't know why.

---

### Post by lswest on 2008-05-20
> **slughappy1 said:**
> I did not want conky to run on its own, that's why I didn't use the command ```
conky &
```But muadnu, that's exactly what is happening. When I close conky it stays on the desktop, but it does not update anymore.

About lowering it, I figured it out right before you guys told me. I just entered another blank line between TEXT and the commands. Thanks though

try changing the first two lines to this: ```
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

the override prevents it from being minimized when you do "show desktop" and the "own_window yes" might fix the (i call it a "ghost" image) image on the desktop.

this should also fix the problem of it hiding your desktop icons.

if that doesn't work, try changing "own_color brown" to "own_color transparent"

---

### Post by BDNiner on 2008-05-20
how are you closing conky? are you killing the process or just closing the terminal? in the terminal type
```

ps -e

```
It will list all currently running processes. then look for the entry relating to conky and get the process ID. Then type:
```

kill (process ID)

```
Where process ID is the process number relating to conky and that will completely close it. you may have several processes named conky, you need to kill them all for it to disappear. be carefull when trying to kill processes you may kill the wrong process by mistake.

---

### Post by lswest on 2008-05-20
> **BDNiner said:**
> how are you closing conky? are you killing the process or just closing the terminal? in the terminal type
```

ps -e

```
It will list all currently running processes. then look for the entry relating to conky and get the process ID. Then type:
```

kill (process ID)

```
Where process ID is the process number relating to conky and that will completely close it. you may have several processes named conky, you need to kill them all for it to disappear. be carefull when trying to kill processes you may kill the wrong process by mistake.

you can also just do ```
kill $(pidof [program name])
or
kill `pidof [program name]`
``` to kill it without needing to know the PID

---

### Post by Inxsible on 2008-05-20
> **lswest said:**
> you can also just do ```
kill $(pidof [program name])
or
kill `pidof [program name]`
``` to kill it without needing to know the PIDand ```
killall *[program name]*
```Of course that will kill all instances of the program, if you have multiple running.

---

### Post by muadnu on 2008-05-20
> **slughappy1 said:**
> But muadnu, that's exactly what is happening. When I close conky it stays on the desktop, but it does not update anymore.


Ok then. I think that that should be fixed by doing what lswest suggests above. As a workaround (though maybe it doesn't even deserve that name), try simply dragging the mouse on your desktop over the area where conky is drawn. It's silly, but I remember this happening to me at some point and that deleted it (simply because it makes the desktop be redrawn at that location I guess), so maybe it works for you...

---

### Post by slughappy1 on 2008-05-20
Ok, following your directions, lswest, I changed all of what you said except "own_color brown" to "own_color transparent" gives an error. ```
jason@Tux:~$ conky
Conky: /home/jason/.conkyrc: 55: no such configuration: 'own_window_color'
Conky: statfs '/media/SWEET': No such file or directory
Conky: desktop window (10000bd) is subwindow of root window (59)
Conky: window type - override
Conky: drawing to created window (2000001)
Conky: drawing to double buffer

``` My file now looks like this ```
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
own_window_hints undecorated,below,sticky,skip_taskbar,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
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

own_window_color transparent
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
${offset 240}${color slate grey}IP:${color } ${addr wlan0}
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

${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}SWEET:  ${color }${fs_free /media/SWEET}/${fs_size /media/SWEET}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed wlan0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed wlan0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

``` It now closes when I stop the program, but sadly still no desktop icons. 

Another question, I was curious on if there is a way to have it display a usb flash drive when it gets inserted/mounted, but not display it when it is not in/unmounted?

EDIT:
I restarted my computer and I now have my icons back

---

### Post by lswest on 2008-05-20
my bad, you should change the "own_color" to "own_window_colour transparent" (note the "u")

also, i use the disk mounter applet on my gnome panel for handling USB sticks.

---

### Post by slughappy1 on 2008-05-20
I switched it back so it has a u, but I don't really understand what you mean by disk mounter applet for gnome. Gnome already has one right? I should have elaborated more. I would like to be able to have conky display the capacity and used space of a drive just inserted but not when there isn't one. I set up mine so that it will tell me for one of my drives, but the way I did that. It always shows up even if it isn't present. But that is only one drive, I would like to set it up so that if I put in any flash drive it will show the used space and the capacity

---

### Post by lswest on 2008-05-20
ah, you could probably set it up using an "if" statement in a script, then executing the script.  Not 100% sure on how the script would be but the basic idea is:
```
if(/media/<mountpoint>/ IS NOT empty){
//display info
}
else{
//hide info
}
``` however, that's not proper code, and i'm not sure if it would work for conky, but maybe someone else knows.  Probably checking the output of "ls /media/<mountpoint" to see if it's empty or not, then running the conky commands to display the info, then stopping those commands when it is empty again.

***EDIT* found out there's a conky "if" statement for mounting drives, it's "if_mounted" see [here]("http://conky.sourceforge.net/variables.html") for more info.**

---

### Post by slughappy1 on 2008-05-20
Thanks! That worked perfectly. ```
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
own_window_hints undecorated,below,sticky,skip_taskbar,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
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
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
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

${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /}
${if_mounted /media/SWEET}${offset 240}${color slate grey}SWEET:  ${color }${fs_free /media/SWEET}/${fs_size /media/SWEET}
${offset 240}${fs_bar 3,100 /media/SWEET}${endif}
${offset 240}${color slate grey}NET: ${color }${wireless_essid wlan0}
${offset 240}${color slate grey}IP:    ${color } ${addr wlan0}
${offset 240}${color}Up: ${color }${upspeed wlan0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed wlan0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}


```

---

### Post by lswest on 2008-05-20
glad i could help...if you found it useful, you could thank me using the medal on the bottom right of my posts ;) </vanity>
glad we got it sorted :)

---

### Post by slughappy1 on 2008-05-20
Sure thing, I always forget about that

---

### Post by lswest on 2008-05-20
haha, thanks, i usually just do it to see if people will do it :P  But thanks for the thanks :)

---

