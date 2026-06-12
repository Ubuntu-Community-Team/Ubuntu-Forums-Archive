---
title: "modifyng my storage meter on my conkyrc file"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-06-25
```
background yes
font Zekton:size=8
xftfont Zekton:size=8
use_xft yes
xftalpha 0.1
update_interval 0.6
total_run_times 0
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
own_window_transparent yes


double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 256 5
maximum_width 300
default_color 000000
default_shade_color black
default_outline_color black
alignment top_right
gap_x 2
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Zekton:style=Bold:pixelsize=24}${alignc}${time %l:%M:%S %p}${font Zekton:size=8}
SYSTEM ${hr 1 }

CPU       ${alignc} ${freq_dyn}MHz / ${acpitempf}F ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Processes: ${alignr}$processes ($running_processes running)

Highest CPU $alignr CPU%       MEM%
${top name 1}$alignr${top cpu 1}         ${top mem 1}
${top name 2}$alignr${top cpu 2}         ${top mem 2}
${top name 3}$alignr${top cpu 3}         ${top mem 3}

Load: ${alignr}$loadavg

FILESYSTEM ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}
Storage: ${alignr}${fs_free /media/storage} / ${fs_size /media/storage}
${fs_bar 4 /media/storage}

NETWORK ${hr 1}${color}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 24,128} ${alignr}${upspeedgraph eth0 24,128}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

CURRENT CONDITIONS ${hr 1}${color}

${execi 3600 perl ~/scripts/weather.pl 60123 f 1w}
${execi 3600 perl ~/scripts/weather.pl 60123 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl 60123 f t}
${voffset -15}$alignr${offset -60}${font weather:size=32}${execi 3600 perl ~/scripts/weather.pl 60123 f cp}$font
5 DAY FORECAST ${hr 1}${color}

${font weather:size=55}${execi 3600 perl ~/scripts/weather.pl 60123 f 5dp}${font}$color
${voffset -70}${execi 3600 perl ~/scripts/weather.pl 60123 f 5dt}

```

basically i have a storage meter on my conky that is inactive and i want to either show my external h.d. or i want to show my flash drive. anyone know how

---

### Post by MasterSander on 2008-06-25
Are you sure the folder is called /media/storage? or is it /media/Storage, these differ.

---

### Post by PatrickMoore on 2008-06-25
> **MasterSander said:**
> Are you sure the folder is called /media/storage? or is it /media/Storage, these differ.



found the issue thank you for the guidance...

does anyone know how i can modify the network monitor in conky to show what im using

---

### Post by MasterSander on 2008-06-25
depends on what you use? Here it is set to eth0, but if you're wireless you're probably wlan0, Type iwconfig in terminal to see what's running.

---

### Post by PatrickMoore on 2008-06-25
wlan0 thank you works like a charm. now i have almost everything running on conky. last step is the weather. i think i need another forum for that

---

