---
title: "adjusting .conky position"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-06-27
is there a way in which i could adjust the position of my conky layout a little lower so that it doesnt get cut off when i access my menu? i was trying to find an obvious point in my .conkyrc file to adjust but can only decipher a few parts clearly


heres my conky file
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

Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}
Storage: ${alignr}${fs_free /media/disk} / ${fs_size /media/disk}
${fs_bar 4 /media/disk}

NETWORK ${hr 1}${color}

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 24,128} ${alignr}${upspeedgraph wlan0 24,128}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}

```

and my screen shot. anyone know how?

---

### Post by dizee on 2008-06-27
I *think* gap_x is what you need. Try changing 2 to 20 or whatever width your panel is.

actually it's gap_y :p

---

### Post by wenuswilson on 2008-06-27
> alignment top_right
gap_x 2
gap_y 10


I don't know for sure but I would guess you would want to edit gap_y to a larger number and I would guess you would want to then reload conky.

---

### Post by PatrickMoore on 2008-06-27
> **dizee said:**
> I *think* gap_x is what you need. Try changing 2 to 20 or whatever width your panel is.

actually it's gap_y :p

just where i wanted it thank you

---

