---
title: "conky desktop configure/setup"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-20
I just sudo installed conky.  I then brought it up from the terminal. but this is not what I want.  I want to put it on my desktop and make it look nice the way I have seen it on yours.  I still have difficulty making my way around the CLI so I'm kind of stuck right here.

---

### Post by drubin on 2008-07-20
Here is the ~/.conkyrc file that Dr Small gave me yesterday...

Seems to be a little better then then standard window that comes up by default. I am still having issues getting it to stay as a "screenlet" on my desktop.

This one currently refreshes but if you move a window over it, the window acts as an eraser and removes part of the conky display. Maybe some one else with more experience can help a bit more. 

To use this, Open up Gedit, and open the .conkyrc file in your home directory. replace the contents with this.  restart conky.  

```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Displays:
#	* Date		* LAN IP
#	* Time		* WAN IP
#	* UpTime	* Connection Status
#	* Downloaded	* CPU Graph
#	* CPU %		* Processes
#	* Running	* Highest Memory
#	* Mem Space	* Swap Space
#	* Home Space	* Net Graph (UP / DOWN)
#
# Comprehensive Simplicity Script by Dr Small


# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer no

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 60.0

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

override_utf8_locale yes
xftfont Terminus:size=8
xftalpha 0.8



TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %B %e %G}
${offset 240}${color slate grey}${time %Z,  }${color }${time %I:%M:%S}
${offset 240}${color slate grey}Day:  ${color }${time %j}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kernel: ${color }$kernel

${offset 240}${color slate grey}LAN IP:  ${color }${addr ath0}
${offset 240}${color slate grey}Connection: ${color }${wireless_link_qual ath0}%${color }
${offset 240}${color slate grey}DNS Server: ${color }${nameserver}
${offset 240}${color slate grey}Download: ${color }${totaldown ath0}
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}CPU:${color } $cpu% 
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}

${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed ath0} k/s
${offset 240}${upspeedgraph ath0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed ath0}k/s${color}
${offset 240}${downspeedgraph ath0 20,130 000000 ffffff}
```

---

### Post by spiderbatdad on 2008-07-20
create a file called .conkyrc in your home folder. Put conky configuration in it. You can start conky with Alt+F2 or create a panel launcher for it.

See this thread for examples of .conkyrc you can copy/modify to your liking:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by collinp on 2008-07-20
Edit /etc/conky/conky.conf as root (sudo gedit /etc/conky/conky.conf), look for own_window, and replace yes with no. Reload conky, now it should be like everyone elses. If you need to kill conky for some reason, go into a termial, run ps x, look for anything about conky, then kill the process based on id. Or, install xfce4-taskmanager for a gui task manager.

---

### Post by halitech on 2008-07-20
try this one

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

${color CC0D00}SYSTEM OVERVIEW
${color CC0D00}${time}
${color FFFF00}Host: ${color white}$nodename
${color FFFF00}Kernel: ${color white}$kernel ${machine} (Gutsy Gibbon)
${color FFFF00}Uptime: ${color white}$uptime

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${execi 30 acpi -t show cpu temps}
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
home:  ${fs_free_perc /home/daryl}%   ${fs_bar 6 /home/daryl}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color #e9c703}Local Weather:
$color${execi 1800 /home/daryl/applications/weather/weather.sh CAXX0183}

```

to fix the one you are using, change
```

# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_hints undecorated,below,skip_taskbar
background no

```
to
```

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes

```
and this```

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer no

```
to
```

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

```

---

### Post by spiderbatdad on 2008-07-20
> **Hellow said:**
> Edit /etc/conky/conky.conf as root (sudo gedit /etc/conky/conky.conf), look for own_window, and replace yes with no. Reload conky, now it should be like everyone elses. If you need to kill conky for some reason, go into a termial, run ps x, look for anything about conky, then kill the process based on id. Or, install xfce4-taskmanager for a gui task manager.
err... not really.

---

### Post by collinp on 2008-07-20
> **spiderbatdad said:**
> err... not really.

It works for me.

---

### Post by halitech on 2008-07-20
> **Hellow said:**
> Edit /etc/conky/conky.conf as root (sudo gedit /etc/conky/conky.conf), look for own_window, and replace yes with no. Reload conky, now it should be like everyone elses. If you need to kill conky for some reason, go into a termial, run ps x, look for anything about conky, then kill the process based on id. Or, install xfce4-taskmanager for a gui task manager.

if he has (or creates) a .conkyrc file, he won't need to do anything as root as it will be in his home folder

---

### Post by collinp on 2008-07-20
> **halitech said:**
> if he has (or creates) a .conkyrc file, he won't need to do anything as root as it will be in his home folder

It should be easier to load conky from the default file though, as it is the default file. Guess I like doing things my way :b.

---

### Post by drubin on 2008-07-20
Don't mean to high jack this thread but any one else experiencing  "currently refreshes but if you move a window over it, the window acts as an eraser and removes part of the conky display." with those config files?

---

### Post by spiderbatdad on 2008-07-20
> **rubinboy said:**
> Don't mean to high jack this thread but any one else experiencing  "currently refreshes but if you move a window over it, the window acts as an eraser and removes part of the conky display." with those config files?

background yes
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

---

### Post by drubin on 2008-07-20
> own_window_type override

Thanks solved the issue...

---

### Post by halitech on 2008-07-20
> **Hellow said:**
> It should be easier to load conky from the default file though, as it is the default file. Guess I like doing things my way :b.

thats the nice thing about *nix, more then one way of doing everything and no real right or wrong (in most cases :P ) Reason I like having a .conkyrc file in my home folder is so I can set up different 'profiles' in each users home folder so they see different things.

---

### Post by spiderbatdad on 2008-07-20
> Default configuration file location is $HOME/.conkyrc or ${sysconfdir}/conky/conky.conf. On most systems, sysconfdir is /etc, and you can find the sample config file there (/etc/conky/conky.conf). 

[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

conky is designed to be run in userspace not as root. The file in /etc/conky/conky.conf is a sample file. Users of ubuntu should use .conkyrc in their home directory.

---

### Post by adamogardner on 2008-07-20
thanks I'm getting the picture.  It's a script and there are many and I can tweak one I like say give it a red font to contrast the background.  I have to do this in gedit by deleting what exists and pasting one from somewhere else.  What Is in the home folder exactly the script I made in gedit?  I save it to the folder I am making?  Is this right: "mkdir somefoldername",   then "mv somefoldername Home"?

---

### Post by spiderbatdad on 2008-07-20
.conkyrc is a text file you put in your /home/user_name directory. You can do this graphically by opening your home folder and right clicking and create a document. Name it .conkyrc. Dot files will be hidden. To display them ls -al or View>>show hidden files from the file browser. If you look at the .conkyrc thread, you can copy/paste any one of those into your .conkyrc file then run it with ALT+F2...enter conky.

You can also create a panel launcher by right click on the panel and "Add to panel." Select "custom application launcher." The command is: conky

---

### Post by adamogardner on 2008-07-20
so this folder I made in my home directory named .conkyrs is empty but if I copy and past a script into it something is going to happen?  I think I'm missing a huge step

---

### Post by adamogardner on 2008-07-20
stupid quetion:  how do I paste something into an empty folder?  what kind of . I don't get it.

---

### Post by tdrusk on 2008-07-20
> **adamogardner said:**
> stupid quetion:  how do I paste something into an empty folder?  what kind of . I don't get it.
create a text file and paste the text in there.

I found some really good .conkyrc files in here.
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by spiderbatdad on 2008-07-20
> **adamogardner said:**
> stupid quetion:  how do I paste something into an empty folder?  what kind of . I don't get it.

ok. It is not a folder. It is a file. A text file named .conkyrc see screenshot. You navigate to Places>>Home Folder. From within your home folder, you right click and select create a Document>>empty document...name it .conkyrc. Now use the View menu at the top of the window to show hidden files. Click on the .conkyrc file and an empty document will open.

Use another workspace and navigate to a .conkyrc file you want to copy...drag your mouse over the entire text and when it is all highlighted, right click and select copy...see screenshot.

Now go back to your .conkyrc file. Right click on the empty space in the file and select paste. Then click the floppy disk icon near the top of the window to save the file. whew.

---

### Post by adamogardner on 2008-07-20
ok  thanks  totally on track.  hunting for script now

---

### Post by adamogardner on 2008-07-20
I'm sure I did everything As described but I got this both times: in the terminal I get this output:

adamogardner@CRONUS:/$ conky
Conky: missing text block in configuration; exiting
adamogardner@CRONUS:/$ conky
Conky: missing text block in configuration; exiting
adamogardner@CRONUS:/$ 

and if I type conky after alt f2   nothing happens.  What am I missing?

---

### Post by spiderbatdad on 2008-07-20
not sure. I haven't used conky for a long time. I just quickly ran sudo apt-get install conky...pasted this into my .conkyrc :```
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 250 

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

# Default colors and also border colors
default_color black

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 40

# stuff after 'TEXT' will be formatted on screen

TEXT
${color}Linux $kernel
$hr
Uptime: $uptime
$hr
CPU:   ${color white}$cpu%  ${freq} MHz$color
RAM:   ${color B9D3EE}$memperc%  ${mem}B / ${memmax}B$color
Swap:  ${color 26466D}$swapperc%  ${swap}B / ${swapmax}B$color
$hr
${color}Internet/Networking Status: (${addr eth0})$color
Down: ${color B9D3EE}${downspeedf eth0}k/s $color${alignr}Up: ${color 26466D}${upspeedf eth0}k/s$color
${downspeedgraph eth0 25,180 000000 B9D3EE} ${alignr}${upspeedgraph eth0 
25,180 000000 26466D}
```

Pressed Alt+F2 and entered conky.

Now I have the screenshot below...conky in upper left...I'll admit it isn't a very elegant conky, but just a quick cut/paste from the conky thread.

---

### Post by Dr Small on 2008-07-20
> **rubinboy said:**
> Thanks solved the issue...
Hey, glad to see you got you problem fixed :D

---

### Post by adamogardner on 2008-07-20
Dr small,  I believe you posted to the wrong thread.
anyone.  I am trying varios scripts from alt f2.  I get nothing.  If I try to launch from the terminal then I get message I just pasted in my previous post about missing text block in the configuration.

---

### Post by Semilton on 2008-11-11
> **adamogardner said:**
> Dr small,  I believe you posted to the wrong thread.
anyone.  I am trying varios scripts from alt f2.  I get nothing.  If I try to launch from the terminal then I get message I just pasted in my previous post about missing text block in the configuration.


I am also having this problem, i have tried everything i can find on fixing it and, none of it is working.If anybody has a solution it would be greatly appreciated. ;D


Edit: I think the reason mine isn't working is because, it says conky.conf.gz isn't a directory. I have tried reinstalling and it still saying it isn't. I think that is why it's not finding .conkyrc but, i don't know how to fix that.

---

