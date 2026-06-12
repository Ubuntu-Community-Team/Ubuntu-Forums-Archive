---
title: "Howto: Make Conky display information on different parts of your screen"
date: 2007-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by AegisTalons on 2007-08-12
Before I start, I have to give props to herbster, felicity, and camtech for helping me with this problem. Now I am here to pass it on to you.

So you got Conky working, and you want it to display information on different parts of the desktop. If you have not gotten Conky working, check out these threads:

[Howto: Get a beautiful Conky 1.4.2 setup]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky")

For help with your Conky scripts check this thread:
[Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865")

This has been tested with Ubuntu 7.04 Feisty Fawn x64 bit, but this should work with 32 bit version.

**Explanation:** This is a how-to to get Conky to display information on different parts of your screen. For example, the date at the bottom left and the time at the bottom right.

**Required Items:** Conky installed and working properly

**Uninstalling/Undoing:** Delete the scripts created

Before we start, I want to let you know that there are two possible ways of doing this: 
**First:** (Easier/less tinkering) have as many conky daemons run as there are areas on your desktop that you want information. (2 scripts if you want information at the bottom left and the bottom right). In addition to those scripts you need another script to start that many instances of conky.

**Second:** (More tinkering) run conky under one script (.conkyrc) but you separate out the data by using the **offset** command.

An example of the offset command is provided by camtech. This is his script below:

```
# *No longer the* Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
#options are: normal, desktop, override, utility
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 4

# border margins
border_margin 10

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 2

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${font samanata}${offset 1647}
${font samanata:size=20}${time %b %d %y} ${alignr} ${time %l:%M %p}${font samanata:size=12}
CPU @ ${freq_g}GHz | Load: $cpu% | Uptime: $uptime ${alignr} Wireless:  Down: ${downspeed ath0}k/s  ${totaldown ath0} | Up: ${upspeed ath0}k/s  ${totalup ath0}
```

You will have to play around with the offset number depending on your resolution and exactly where you want to place it.

You should note that the second method requires only one instance of conky running while the first method requires more than one. If you do not want to run multiple instances of conky, then use offset and play around with it. As for performance hits, you will probably not recognize the difference between conky not running at all, and conky running one instance, or conky running multiple instances.

As for the first method, getting conky running using multiple scripts follow this procedure.

1) First edit your .conkyrc file in /home/USERNAME/ to your taste.
This is my .conkyrc file.
```
double_buffer yes
update_interval 1
background yes

own_window yes
own_window_transparent yes
own_window_type override
#own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

use_xft yes
override_utf8_locale no
xftfont Telegraphem:size=9
xftalpha 0.8
draw_shades no
draw_outline no
draw_borders no
uppercase no
use_spacer no

border_margin 0
border_width 0

default_color white
default_outline_color black

alignment bottom_left
gap_x 5
gap_y 5

TEXT
${font Telegraphem:bold:size=20}${time %B %e}$font
Core 1:  ${color #E68600}${cpu cpu1}%${color}
Core 2:  ${color #E68600}${cpu cpu2}%
```

2) Create your second file and name something like conky_time for example. I saved it in /home/USERNAME/scripts folder with other scripts that I have.
This is my second conky file called conky_time:

```
double_buffer yes
update_interval 1
background yes

own_window yes
own_window_transparent yes
own_window_type override
#own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

use_xft yes
override_utf8_locale no
xftfont Telegraphem:size=9
xftalpha 0.8
draw_shades no
draw_outline no
draw_borders no
uppercase no
use_spacer no

border_margin 0
border_width 0

default_color white
default_outline_color black

alignment bottom_right
gap_x 5
gap_y 5

TEXT
${font Telegraphem:bold:size=20}$alignr${time %I:%M %p}$font
${alignr}Uptime: ${color #E68600}${uptime}${color}
Down: ${color #E68600}${downspeed eth0}${color}Kb/s|${alignr}Up: ${color #E68600}${upspeed eth0}${color}Kb/s
```

3) Now you need to run these scripts with conky as "one operation". To achieve this use this little script and change it to suit your locations of the conky scripts. Save this script (dual_conky.sh) alongside your conky_time script:

```
#!/bin/bash

sleep 9 &&
conky -d -c /home/alex/.conkyrc &
sleep 9 &&
conky -d -c /home/alex/scripts/conky_time &
exit
```

The -d arguement daemonizes Conky, aka fork to background. The -c arguement uses a config file to load instead of $HOME/.conkyrc. Sleep 9 means it will wait 9 secs and then execute the rest of the script.

Now you need to test out your scripts. In a terminal, cd to the directory containing your dual_conky.sh file and type:

```
sh dual_conky.sh
```

See if conky starts up after 9 seconds and is displaying like you want it.

Now we need to get conky to start up at boot. To do that, go to:
System -> Preferences -> Sessions

On the Startup Program Tab, click the **New** button on the right.

Name: Conky
Command*: sh [script location]

*In my case: sh /home/alex/scripts/dual_conky.sh

Now conky will start up when you boot. See the attached image for an example of my desktop.

Go ahead and give it a test run. If you have any problems/questions/comments, please feel free to post them.

---

### Post by matthew on 2007-09-30
Thanks for this. I was stuck on one small point in the startup script and your example cleared it up for me. (I was using too many &s at the end of a row... doh!)

---

### Post by h4roldpb on 2008-02-10
hey man nice work! i was trying to do something like this but didn't have a clue!

btw, regarding the script.. is it necessary to keep the 9 seconds delay? could I set mine to like 1 or 2 ... ??

---

### Post by thecapuchin on 2008-02-10
I believe the delay is mostly to make sure that conky shows up after the rest of the desktop environment so it actually shows up above the background but below any other windows.  I would guess that a compromise int he delay would be a good choice (3-5 sec I would say).

---

### Post by PurposeOfReason on 2008-02-10
He probably has a larger delay if he is running compiz so that conky loads after compiz. If it does not, it gets a shadow around it.

---

### Post by h4roldpb on 2008-02-10
ok, well now i did it.. if anyone cares to see what i did...

---

### Post by AegisTalons on 2008-02-10
looks awesome. Glad to see the guide is helping. Regarding the delay, I'm running Compiz and I have conky turn on after some time to allow Compiz time to fully get started.

---

### Post by Anduu on 2008-02-11
Thanx for the How-To...now to see if I can do something creative with it :p

---

### Post by tom957 on 2008-02-20
this howto was simple, yet great. thanks!

---

### Post by Plasma_NZ on 2008-06-23
Ok.. gotta question....  I already have a conky that runs nice setup how i like, that is on all 5 virtual desktops under compiz... now i'd like to run a "second" conkyweather and times for each timezone for each of the weather area's i want, but only have it on 1 virtual desktop... how do i go about this.?

---

### Post by Plasma_NZ on 2008-06-23
Solved my problem..

---

### Post by AegisTalons on 2008-06-27
Glad to hear you solved your problem. Do you want to explain or give the script you used so that others who might be interested in doing something similar have something to go by.

---

### Post by u-blunt-2 on 2008-08-27
thanks for the how to. I had tried by simply adding another startup command under Settings -> Prefs -> Sessions, with the "-c /2nd_script_location" option. It didn't work. 
I tried with the "-d" option also, to no avail. 
Found your how to, and added the shell script with all good commands to my session startup list. I always get the original conky layout, but the second conky layout appears far from where it is supposed to (e.g. upper left instead of lower right!).
I should mention I am also running avant-window-manager, which I suspect is messing things up. 
Anyone stumble upon such a problem? 
I will try to use ${offset} with the first script to circumvent this. will post back.

---

### Post by u-blunt-2 on 2008-08-28
the offset option makes things messy !
I ended up changing the sleep time to 20 seconds, this way AWN doesn't seem to interfere.
The second script not being run got fixed after a reboot. For some reason that x-session was reading an old script that had been moved.

---

### Post by AegisTalons on 2008-09-03
So what other issues are you still running into? Getting the individual scripts to display at the proper place on screen?

---

### Post by gighsmighly on 2009-08-29
well ... this is nice..  but my conky keeps blinking when i run a second instance..  is there a reason for that?

---

