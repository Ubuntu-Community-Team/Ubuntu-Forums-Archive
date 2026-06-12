---
title: "CPU, Temp, Ram monitoring etc."
date: 2012-09-28
forum: New to Ubuntu
---

### Post by CJ_Hudson on 2012-09-28
Hi,
I found this useful thread [http://ubuntuforums.org/showthread.php?p=12265877#post12265877](http://ubuntuforums.org/showthread.php?p=12265877#post12265877)

...but can't seem to get the real-time monitoring graphs etc. widgets on the screen (ideally superimposed on top of any windows I subsequently open).

---

### Post by vasa1 on 2012-09-28
Search the Ubuntu Software Center for "System Load Indicator".

---

### Post by Lars Noodén on 2012-09-28
I've been looking at something similar.  It needs to have the package lm-sensors installed to work.   There's probably a better way.

Anyway, install the package conky and then add this to .conkyrc in your home directory:

```

# Based on UBUNTU-CONKY
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
# border_margin 4

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
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
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
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

${offset 240}${color slate grey}CPU0:   ${color} ${execi 8 sensors | awk '$1 == "Core" && $2 =="0:"{sub(/^\+/,"",$3);gsub(/[^0-9\.]*/,"",$3); print $3}' } C 
${offset 240}${color}${execbar sensors | awk '$1 == "Core" && $2 =="0:"{sub(/^\+/,"",$3);gsub(/[^0-9\.]*/,"",$3); print $3}' }
${offset 240}${color slate grey}CPU1:   ${color} ${execi 8 sensors | awk '$1 == "Core" && $2 =="1:"{sub(/^\+/,"",$3);gsub(/[^0-9\.]*/,"",$3); print $3}' } C 
${offset 240}${color}${execbar sensors | awk '$1 == "Core" && $2 =="1:"{sub(/^\+/,"",$3);gsub(/[^0-9\.]*/,"",$3); print $3}' }

${offset 240}${color}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EFRO temperature 30 }C  ${color}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EFRO wind_speed 30 } kph   ${color}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EFRO wind_dir 30 }    
${offset 240}${color}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EFRO humidity 30 }%    ${color}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EFRO cloud_cover 30 }

```

The awk statements with 'core' will have to be adjusted to reflect the actual output of [sensors](http://manpages.ubuntu.com/manpages/precise/en/man1/sensors.1.html) for your machine.  The particular machine in  the example above has two cores.

I'm sure there's a better way to do it, but that's the first way I found that got it working.  There are thousands more examples here:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by CJ_Hudson on 2012-10-03
Sorry to sound stupid or whatever, but to edit this file do I do: 

Gedit /usr/share/doc/conky/examples/conkyrc.sample.gz

?

Edit #1
...and please, how do I run conky?
Edit #2
...and it is a dual-core cpu.

---

### Post by Lars Noodén on 2012-10-03
You should look at it to see what it contains and if it contains the file .conkyrc, you can open it in your home directory.

```

tar ztf  /usr/share/doc/conky/examples/conkyrc.sample.gz
tar zxf  /usr/share/doc/conky/examples/conkyrc.sample.gz

```

You run conky by entering 'conky' at the terminal or adding /usr/bin/conky to your Startup Applications menu. 

When you find a .conkyrc that works, make a back up copy of it before changing it or trying others.  [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by stinkeye on 2012-10-03
When you run **conky** it will look for a config at **~/.conkyrc** and if no **~/.conkyrc** exists 
it will load the sample config @ **/etc/conky/conky.conf**
You have to create the **~/.conkyrc** config.

You can either download someone elses config,save as **.conkyrc** to your home folder and edit to your computing environment
or
copy the basic config @ **/etc/conky/conky.conf** to **~/.conkyrc** and edit.
To copy the sample config to **~/.conkyrc** in  terminal...
```
cp /etc/conky/conky.conf ~/.conkyrc
```

Then to edit...
```
gedit ~/.conkyrc
```

If you want to run more than one config you can use the **-c** option to specify a config.
eg
```
conky -c *[COLOR="Gray"]/path/to/your/config[/COLOR]*
```

For CPU and HDD temps you need to install **lm-sensors** and **hddtemp**

Some links:
[**_[COLOR="DarkRed"]How to get sensors in conky[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11013044&postcount=18302")
[**_[COLOR="darkred"]Setting Up Conky[/COLOR]_**]("https://help.ubuntu.com/community/SettingUpConky")



Pic of a conky config I use positioned under a fully transparent unity panel which shows...
cpu load/temp,drive temp, gpu temp, free memory and down/upload speeds.

---

### Post by CJ_Hudson on 2012-10-06
Aha! <ching> *lightbulb*

---

