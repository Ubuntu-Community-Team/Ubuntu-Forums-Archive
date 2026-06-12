---
title: "Conky Issues with conky 1.8.1"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by KrisDeniseRiley1 on 2012-01-05
So I am putting together a conky script and can't seem to get some of my wireless things like wireless quality, ssid and bitrate to work. I am working with Ubuntu 11.10. Here is my Conky Script so far:

```
use_xft yes
xftfont verdana:size=8
alignment top_left
xftalpha 0.8
own_window class Conky
own_window yes
#own_window_type override
own_window_type conky
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 4D6844

color0 E6E6E6
color1 A7CC5C
color2 E6E6E6

override_utf8_locale yes



#border_inner_margin 0
#border_outer_margin 0

minimum_size 310 310
maximum_width 310
    

#alignment tl
gap_x -20
gap_y 40

# -- Graphics settings -- #
#draw_graph_borders yes

# -- Text settings -- #
use_xft yes
#xftfont MaiandraGD:size=24
#xftalpha 0.4

#default_color 8b8b8b



TEXT
#######################################
###             Logo              #####
#######################################
#${color D3DADF}${font OpenLogos:size=40}   S  
#######################################
###         HTC Weather            ####
#######################################  
${voffset 30}${font Helvetica LT Std :style=Condensed:size=60}${color 434343}${goto 42}${time %H}${goto 142}${color 434343}${time %M}${font Helvetica LT Std :size=15:style=condensed}${color 808080}${goto 229}${time %S}
${voffset 55}${color whitesmoke}${font Helvetica LT Std :size=8}${alignr 105}${time %A},${time %e},${time %B},${time %G}
${voffset -45}${goto 22}${font Helvetica LT Std :size=8}${color 909090}${execi 600 conkyForecast -i --location=USOR0304 --datatype=CN --refetch}
#${voffset 8}${font Helvetica LT Std :size=10}${color 707070}${goto 24}&#1041;&#1091;&#1088;&#1075;&#1072;&#1089;
${font Helvetica LT Std :size=8}${color whitesmoke}${goto 24}${execi 1800 conkyForecast -i --location=USOR0304 --datatype=CT}${voffset -10}${goto 200}${font Helvetica LT Std :size=25}${color d4d4d4}${execi 1800 conkyForecast -i --location=USOR0304 -u
--datatype=HT}
${voffset 35}${font Helvetica LT Std :size=8}${color white}${goto 34}${execi 600 conkyForecast -i --location=USOR0304 --datatype=HT -u --startday=1}/${color 707070}${execi 600 conkyForecast -i --location=USOR0304 --datatype=LT -u --startday=1}${font Helvetica LT Std :size=8}${color white}${goto 79}${execi 600 conkyForecast -i --location=USOR0304 --datatype=HT -u --startday=2}/${color 707070}${execi 600 conkyForecast -i --location=USOR0304 --datatype=LT -u --startday=2}${font Helvetica LT Std :size=8}${color white}${goto 128}${execi 600 conkyForecast -i --location=USOR0304 --datatype=HT -u --startday=3}/${color 707070}${execi 600 conkyForecast -i --location=USOR0304 --datatype=LT -u --startday=3}${font Helvetica LT Std :size=8}${color white}${goto 169}${execi 600 conkyForecast -i --location=USOR0304 --datatype=HT -u --startday=4}/${color 707070}${execi 600 conkyForecast -i --location=USOR0304 --datatype=LT -u --startday=4}
${font Helvetica LT Std :size=8}${color 707070}${goto 34}${execi 600 conkyForecast -i --location=USOR0304 --datatype=DW --shortweekday --startday=1}${font Helvetica LT Std :size=8}${color 707070}${goto 79}${execi 600 conkyForecast -i --location=USOR0304 --datatype=DW --shortweekday --startday=2}${font Helvetica LT Std :size=8}${color 707070}${goto 120}${execi 600 conkyForecast -i --location=USOR0304 --datatype=DW --shortweekday --startday=3}${font Helvetica LT Std :size=8}${color 707070}${goto 169}${execi 600 conkyForecast -i --location=USOR0304 --datatype=DW --shortweekday --startday=4}
${voffset -10}${font Helvetica LT Std :size=8}${color 707070}${goto 216}${execi 600 conkyForecast -i --location=USOR0304 --datatype=DW --shortweekday --startday=5}
${voffset -23}${font Helvetica LT Std :size=8}${color white}${goto 216}${execi 600 conkyForecast -i --location=USOR0304 --datatype=HT -u --startday=5}/${color 707070}${execi 600 conkyForecast -i --location=USOR0304 --datatype=LT -u --startday=5}
${image /home/kris/.images/base.png -p 12,30 -s 238x140}
${image /home/kris/.images/base.png -p 12,190 -s 238x40}
${image /home/kris/.images/flip_bg.png -p 30,10 -s 100x110}
${image /home/kris/.images/flip_bg.png -p 130,10 -s 100x110}
${execpi 600 conkyForecast -i --location=USOR0304 --template=/home/kris/.vreme.template}
####################################
###          Email Setup        ####
####################################
${voffset -32}${color black}${font OpenLogos:size=46}S${color gray}${font WW2 BlackltrAlt:size=22}Current Emails & PC Vitals${color white}
${color lightgrey}${hr 2}
${voffset -9}${font OpenLogos:size=38}J${font Radio Space:size=22}${color yellow}${execpi 300 python ~/scripts/gmail_parser.py hornerkris@gmail.com June10th 3}${font Radio Space:size=14}${color 014A7F} New Message(s)
####################################
###       Battery Bar           ####
####################################
${color lightgrey}${font OpenLogos:size=26}T${color 014A7F}${font}  Battery: ${battery_percent}% ${battery_bar}
${color ffffff}${color lightgrey}${font OpenLogos:size=26}K${color 014A7F}${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
${color lightgrey}${font OpenLogos:size=26}K${color 014A7F}${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}
${color lightgrey}${font OpenLogos:size=30}t${color 014A7F}${font}  Work:  ${uptime_short}
####################################
###         Network Info        ####
####################################
${font WW2 BlackltrAlt:size=22}Network Info${color white}
${voffset -32}${color black}${font Poky:size=44}Y${color gray}${image /home/kris/.images/wlanbg2.png  -s 400x140 -p -50,565}
${offset 15}${alignc}${execp /home/kris/wlanscript.sh}
${voffset -105}${color black}${font WW2 BlackltrAlt:size=13}${alignc -20}SSID: ${wireless_essid eth1}
${alignc -20}Bitrate: ${wireless_bitrate eth1}
${alignc -50}Local: ${addr eth1}
${alignc -54}Public: ${execi 300 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${voffset -25}${offset 25}${wireless_link_qual eth1}%
```I dont know if its a version of conky thats the issue or what. Any help would be great!

---

### Post by heyandy889 on 2012-01-05
Hey, dude! I just learned that Conky is "a light-weight system monitor." I don't know how to use it, but you might be able to crawl through their documentation . . . [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Also, do you know about the built-in system monitor? It shows CPU, memory, and network usage, as well as detailed info on running processes. You can run it in Ubuntu 11.10 by pressing Super, type "mon" and a little icon show up for "System Monitor."

---

### Post by Smilax on 2012-01-05
maybe try to replace


wireless_link_qual eth1

with

wireless_link_qual wlan0

---

### Post by KrisDeniseRiley1 on 2012-01-05
I have already tried using wlan0. When giving the iwconfig, my interface comes up as eth1. I'm thinking that it's a conky compatability thing.

---

### Post by &#1048;&#1075;&#1086;&#1088; on 2012-02-24
How do You connect to WiFi: -You have NiC or AP?:confused:
If you have AP, than you can nothing with conky....
P.S. Sorry for my english

---

