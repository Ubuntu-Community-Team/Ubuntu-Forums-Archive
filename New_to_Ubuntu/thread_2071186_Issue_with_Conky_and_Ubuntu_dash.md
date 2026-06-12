---
title: "Issue with Conky and Ubuntu dash"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by DGINSD on 2012-10-14
I've recently started having an issue between conky and Ubuntu dash. When the dash is opened the area where my conky is set up will continue to show conky. If I move my mouse around, the area of the dash displaying conky will flicker between; the dash that's supposed to be displayed and the conky.

If there's a window covering up conky and the dash is opened, I get the same behavior, except rather than conky showing up in the dash, there is a section of the covering window the size of my conky.

This started all of the sudden, no changes other than usual updates, I had noticed some xorg updates around the time the problem started. 

I'm using the only driver I can to get 3D acceleration (FGLRX), as I have one of the ati/ati hybrid  chipsets. I've tried 4 different versions of the driver, but they changed nothing.

Maybe I have something in my .conkyrc file set up wrong, I'm certainly no expert. I've tried a few small changes, and the only thing that got rid of the issue in the dash, was to comment out "own_window yes" but that causes other issues, mainly conky blinking when the desktop is clicked on. So here's my .conkyrc.

```

draw_borders no
draw_shades yes
double_buffer yes
default_color 000000
own_window yes
own_window_type desktop
own_window_class conky
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager



use_xft true
xftfont sans$:size=10
xftalpha 1
short_units
update_interval  1
temperature_unit fahrenheit
use_spacer right
no_buffers true
# Strictness of if_up. One of: up, link, or address. The later ones imply the further ones, defaults to up.
# 
if_up_strictness address
format_human_readable true

alignment top_right
gap_x 10
gap_y 40

TEXT
${color FFFFFF}${font :size=12}Processor ${shadecolor FFFFFF}$color${hr 3, }$font
${color FFFFFF}${shadecolor 000000}CPU:${offset 25}${execi 30 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor}${offset 75}$acpitemp &#778; $alignr${freq_g cpu0}Ghz
${color FFFFFF}Core 1:  ${cpu cpu1}%${color 555555}${alignr}${cpubar cpu1 10,270 }
${color FFFFFF}Core 2:  ${cpu cpu2}%${color 555555}${alignr}${cpubar cpu2 10,270 }$color
${shadecolor FFFFFF}${voffset -6}${cpugraph 30,375 000000 777777}
${voffset -8}${font :size=8}${shadecolor FFFFFF} Name $alignr PID              CPU%           MEM%  ${font}
${voffset -14}${hr}
${voffset -6}${color FFFFFF}${shadecolor 000000}${top name 1} $alignr ${top pid 1}     ${top cpu 1}%    ${top mem 1}%
${top name 2} $alignr ${top pid 2}     ${top cpu 2}%    ${top mem 2}%
${top name 3} $alignr ${top pid 3}     ${top cpu 3}%    ${top mem 3}%$color
${shadecolor FFFFFF}${voffset -4}${loadgraph 30,375 000000 777777}
#
${color FFFFFF}${shadecolor 000000}${font :size=12}Memory $color ${shadecolor FFFFFF}${hr 3, }$font
${color FFFFFF}${shadecolor 000000}RAM:$alignr${mem} / ${memmax}
${memperc}%${color 555555}${alignr}${membar 10,320 }
${color FFFFFF}Swap:$alignr${swap} / ${swapmax}$color
#Mem usage
#${voffset }${font :size=8}${shadecolor FFFFFF} Name $alignr PID              MEM%           CPU%   ${font}
#${voffset -14}${hr}
#${color FFFFFF}${shadecolor 000000}${top_mem name 1} $alignr ${top_mem pid 1}     ${top_mem mem 1}%    ${top_mem cpu 1}%
#${top_mem name 2} $alignr ${top_mem pid 2}     ${top_mem mem 2}%    ${top_mem cpu 2}%
#${top_mem name 3} $alignr ${top_mem pid 3}     ${top_mem mem 3}%    ${top_mem cpu 3}%$color

#
#
${color FFFFFF}${font :size=12}Power$color ${shadecolor FFFFFF}${hr 3, }$font
${color FFFFFF}${shadecolor 000000}Battery:${offset 75}${battery_time BAT0}${alignr 5}${battery BAT0}
${color 555555}${battery_bar 10,375 BAT0}${color}${color}

${color FFFFFF}${font :size=11}HDD$color ${shadecolor FFFFFF}${hr 3, }$font
${color FFFFFF}${shadecolor 000000}Drive  Read/Write:$alignr${diskio_read  /dev/sda}/   ${diskio_write  /dev/sda}${color}
${shadecolor FFFFFF}${diskiograph /dev/sda 30,375 000000 888888}
${if_mounted /}${shadecolor 000000}${color FFFFFF}Root:${alignr}${fs_free /} / ${fs_size /}   ${fs_used_perc /}% ${color 555555}${fs_bar 10,150 /}${color}${endif}
${if_mounted /home}${color FFFFFF}Home:${alignr}${fs_free /home} / ${fs_size /home}  ${fs_used_perc /home}% ${color 555555}${fs_bar 10,150 /home}${color}${endif}
${if_mounted /media/Windows_7}${color FFFFFF}Windows:${alignr}${fs_free /media/Windows_7} / ${fs_size /media/Windows_7}  ${fs_used_perc /media/Windows_7}% ${color 555555}${fs_bar 10,150 /media/Windows_7}${color}${else}${color }${shadecolor FFFFFF}Windows:${alignr}Not Mounted    ${shadecolor 000000}${fs_bar 10,150 /media/Windows_7}$color${endif}
${if_mounted /media/Secondary_Distro}${color FFFFFF}${shadecolor 000000}Mint:${alignr}${fs_free /media/Secondary_Distro} / ${fs_size /media/Secondary_Distro}  ${fs_used_perc /media/Secondary_Distro}% ${color 555555}${fs_bar 10,150 /media/Secondary_Distro}${color}${else}${color }${shadecolor FFFFFF}Mint:${alignr}Not Mounted    ${shadecolor 000000}${fs_bar 10,150 /media/Secondary_Distro}$color${endif}
${if_mounted /media/SDcard}${color FFFFFF}${shadecolor 000000}SD:$alignr${fs_free /media/SDcard} / ${fs_size /media/SDcard}   ${fs_used_perc /media/SDcard}% ${color 555555}${fs_bar 10,150 /media/SDcard}${color}$else${color }${shadecolor FFFFFF}SD:${alignr}Not Mounted    ${shadecolor 000000}${fs_bar 10,150 /media/SDcard/*}$color${endif}
${if_mounted /media/USBdrive}${color FFFFFF}${shadecolor 000000}USB:${alignr}${fs_free /media/USBdrive} / ${fs_size /media/USBdrive} ${fs_used_perc /media/USBdrive}% ${color 555555}${fs_bar 10,150 /media/USBdrive}${color}${else}${color }${shadecolor FFFFFF}USB:${alignr}Not Mounted    ${shadecolor 000000}${fs_bar 10,150 /media/USBdrive/*}$color${endif}
#

${color FFFFFF}${font :size=12}Net$color ${shadecolor FFFFFF}${hr 3, }$font
${if_up eth0}${color FFFFFF}${shadecolor 000000}LAN Up:$alignr${upspeed eth0}      ${color}${shadecolor FFFFFF}${voffset -7}${upspeedgraph eth0 20,180 000000 555555 -l }
${color FFFFFF}${shadecolor 000000}LAN Down:$alignr${downspeed eth0}      ${color}${shadecolor FFFFFF}${voffset -8}${downspeedgraph eth0 20,180  555555 000000 -l }${endif}
${if_up eth1}${color FFFFFF}${shadecolor 000000}WLAN Up:$alignr${upspeed eth1}      ${color}${shadecolor FFFFFF}${voffset -9}${upspeedgraph eth1 20,180 000000 555555 -l }
${color FFFFFF}${shadecolor 000000}WLAN Down:$alignr${downspeed eth1}      ${color}${shadecolor FFFFFF}${voffset -10}${downspeedgraph eth1 20,180 555555 000000  -l }${endif}

```

I'd really appreciate some help here as I've run out of things to try. My only other option is to not run conky, but that would really bum me out as I wrote the .conkyrc myself and spent a lot of time on it, but ultimately it makes the dash unusable. Any help or suggestions are as always appreciated.

---

### Post by stinkeye on 2012-10-15
Your config works here with the dash.Using nvidia.
Conky disappears when I click the desktop though.
Probably already tried but could use...
```
own_window_type normal
[COLOR="DimGray"]or[/COLOR]
own_window_type override
```
instead of 
```
own_window_type desktop

```

and also test, using **own_window_type normal** with...
```
own_window_argb_visual yes
own_window_argb_value 180
```

Here is a basic config that just prints "TEST" you can run.
Save as **testconkyrc** to your home folder and run with...
```
conky -c ~/testconkyrc
```

Uncomment these to test argb_visual
```
[COLOR="Magenta"]#own_window_argb_visual yes
#own_window_argb_value 180[/COLOR]
```

testconkyrc:```
####
## Use XFT? Required to Force UTF8 (see below).
#
use_xft yes
xftfont Droid Sans:size=8
xftalpha 0.8
text_buffer_size 512

####
## Force UTF8? Requires XFT (see above).
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## Daemonize Conky, aka 'fork to background'.
#
background no

####
## Update interval in seconds.
#
update_interval 1.0

####
## This is the number of times Conky will update before quitting.
## Set to zero to run forever.
#
total_run_times 0

####
## Create own window instead of using desktop (required in nautilus)?
#
own_window yes
own_window_colour 182547
own_window_title conkytest
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
default_color white
[COLOR="magenta"]#own_window_argb_visual yes
#own_window_argb_value 180
[/COLOR]
####
## Use double buffering? Reduces flicker.
#
double_buffer yes

####
## Draw shades?
#
draw_shades yes

####
## Draw outlines?
#
draw_outline no

####
## Draw borders around text?
#
draw_borders no
default_outline_color 000000
####
## Draw borders around graphs?
#
draw_graph_borders no

####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
alignment tl

####
## Minimum size of text area.
#
minimum_size 200 200
maximum_width 200

####
## Gap between text and screen borders.
#
gap_x 100
gap_y 100

####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes

####
## Pad % symbol spacing after numbers.
#
pad_percents 0

####
## Pad spacing between text and borders.
#
border_inner_margin 1
border_outer_margin 1
border_width 1

####
## Limit the length of names in "Top Processes".
#
top_name_width 10

####
## Subtract file system -/+buffers/cache from used memory?
## Set to yes, to produce meaningful physical memory stats.
#
no_buffers yes

####
## Set to yes, if you want all text to be in UPPERCASE.
#
uppercase no

####
## Number of cpu samples to average.
## Set to 1 to disable averaging.
#
cpu_avg_samples 2

####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 2

####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right

####
## My colors (suit yourself).
#
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 FF4040
color5 B5BEC5
color6 Gray
color7 AntiqueWhite4
color8 F9A41E
#color9 red
color9 6A90EF #icon

TEXT
${font Droid Sans:size=48}TEST
```

---

### Post by DGINSD on 2012-10-15
Thanks for the tips after some experimenting the issue went away but I can't figure what change or combo of changes fixed the issue, as I can no longer duplicate the problem by un-doing changes.

I can get the mouse cursor to act buggy when in the dash by changing "own_window_type" back to desktop from normal.

---

