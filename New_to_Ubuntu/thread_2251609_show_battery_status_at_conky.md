---
title: "show battery status at conky"
date: 2014-11-05
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-11-05
Hi all, 

I'd like to show battery status at conky. 

Here is how do I get battery status in console: 

*upower -i /org/freedesktop/UPower/devices/battery_BAT0| grep -E "state|to\ full|percentage"*

Please find my conky settings below: 

[I]###  Begin Window Settings  ##################################################
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager #sticky
# own_window_colour brown
own_window_title Shortcut Keys
own_window_class Conky

# Use the Xdbe extension? (eliminates flicker)
# It is highly recommended to use own window with this one
# so double buffer won't be so big.
double_buffer yes

#minimum_size 50 0     ## width, height
#maximum_width 50       ## width, usually a good idea to equal minimum width

gap_x 25 # left-right
gap_y 25 # up-down 

alignment tr
###################################################  End Window Settings  ###
###  Font Settings  ##########################################################
# Use Xft (anti-aliased font and stuff)
use_xft yes
#xftfont Anonymous Pro:size=9
#xftfont monofur:bold:size=9
#xftfont monofur:bold:size=10
xftfont zekton:bold:size=9
#xftfont Bitstream Vera Sans Mono:size=12

# Alpha of Xft font. Must be a value at or between 1 and 0 ###
xftalpha 1
# Force UTF8? requires XFT ###
override_utf8_locale yes

uppercase no
######################################################  End Font Settings  ###
###  Color Settings  #########################################################
### WARNING ### These do NOT play well with /media/5/Conky/LUA/draw-bg.lua ###
draw_shades yes #### <<<--- yes --- To see it easier on light screens.
default_shade_color black ##000000
draw_outline no #### <<<--- yes --- Amplifies text if yes OJO with changing fonts
default_outline_color 000000

default_color DCDCDC #220 220 220    Gainsboro
color0 8FBC8F #143 188 143    DarkSeaGreen
color1 778899 #119 136 153 LightSlateGray
color2 D8BFD8 #216 191 216 Thistle
color3 9ACD32 #154 205  50 YellowGreen
color4 48D1CC # 72 209 204 MediumTurquoise
color5 FFDEAD #255 222 173    NavajoWhite
color6 00BFFF #  0 191 255    DeepSkyBlue
color7 5F9EA0 # 95 158 160    CadetBlue
color8 BDB76B #189 183 107    DarkKhaki
color9 CD5C5C #205  92  92    IndianRed  #FF0000 #255   0   0    Red
###  Borders Section  ########################################################
draw_borders no
# Stippled borders?
stippled_borders 0
# border margins
border_inner_margin 5
border_outer_margin 0
# border width
border_width 0
# graph borders
draw_graph_borders no #yes
default_graph_size 15 40
#####################################################  End Borders Secton  ###
###  Miscellaneous Section  ##################################################

# Boolean value, if true, Conky will be forked to background when started.
background no

# Adds spaces around certain objects to stop them from moving other things
# around, this only helps if you are using a mono font
# Options: right, left or none
use_spacer none

# Default and Minimum size is 256 - needs more for single commands that
# "call" a lot of text IE: bash scripts
text_buffer_size 1028

# Subtract (file system) buffers from used memory?
no_buffers yes

# change GiB to G and MiB to M
short_units yes

# Like it says, ot pads the decimals on % values
# doesn't seem to work since v1.7.1
pad_percents 2
##############################################  End Miscellaneous Section  ###

update_interval 1

TEXT
${color C2BAB6}${font zekton:normal:size=9}Host:$nodename
${color yellow}${execi 3600 date +"%A %B %d, %Y (Week: %V)"}
${execi 1  date +"%T"}${color C2BAB6}
Linux Kernel:$kernel
Uptime: $uptime 
RAM: $mem / $memmax
$memperc% $membar
PC Temperature ${execi 8 sensors | grep -A 1 'temp1' | cut -c13-21 | sed '/^$/d'}C

Ethernet Address: ${addr eth0}
Wi-Fi Network SSID: ${wireless_essid wlan0}
Wi-Fi Address: ${addr wlan0}
Wi-Fi Connection quality: $alignr ${wireless_link_qual_perc wlan0}%
${font}
[/I]

---

### Post by Frogs Hair on 2014-11-05
Here are a couple of things to try and you may want look for some complete conky themes that include that option in the style you want. 

```
Battery$alignr${battery_percent BAT0}%

```
Bar:  
```
${battery_bar}${battery_percent BAT0}%

```
AC Adapter:
```
ACPI $alignr ${acpiacadapter}
```

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by vasa1 on 2014-11-05
> **marchello_lippi2 said:**
> ```

...
TEXT
...
${color yellow}${execi 3600 date +"%A %B %d, %Y (Week: %V)"}
${execi 1  date +"%T"}${color C2BAB6}
...
PC Temperature ${execi 8 sensors | grep -A 1 'temp1' | cut -c13-21 | sed '/^$/d'}C
...

```
I'm quite new to Conky and still learning the basics. I want to ask you why you use "execi"? According to **man conky**, things like *exec*, and *execp* are relatively heavy on resources:> 
       exec command
              Executes  a shell command and displays the output in conky. warning:
              this takes a lot more resources than other variables. I'd  recommend
              coding wanted behaviour in C and posting a patch.

Of course, there are features that can only be had by using shell commands or scripts but doesn't Conky natively offer something equivalent (and lighter in terms of resources)?

---

### Post by marchello_lippi2 on 2014-11-06
*I'm quite new to Conky and still learning the basics. I want to ask you why you use "execi"? According to **man conky**, things like exec, and execp are relatively heavy on resources*

I'm new to Conky too... 
It would be great if you can suggest something else. 
But honestly I can't see that my conky slows down my computer.

---

### Post by vasa1 on 2014-11-06
> **marchello_lippi2 said:**
> *I'm quite new to Conky and still learning the basics. I want to ask you why you use "execi"? According to **man conky**, things like exec, and execp are relatively heavy on resources*
...
But honestly I can't see that my conky slows down my computer.
That probably is true. I use an oldish laptop and so like to keep things as minimal (and cool) as possible :) 

As for suggesting something else, I don't know what your codes achieve but I have this:```
${time %a, %d %b} ${color B3492B}${time %H:%M}$color ${utime (%H:%M)}  ${acpitemp}
```which gives me, going from left to right:
Thu, 06 Nov 17:16 (11:46) 44 where "17:16" is colored differently, (11:46) is UTC and "44" is some temperature, probably CPU, because it relates well with %CPU usage.

---

### Post by marchello_lippi2 on 2014-11-06
How do I display in conky: 

1) time remaining to work on battery 

2) time remaining till full charge 

?

---

