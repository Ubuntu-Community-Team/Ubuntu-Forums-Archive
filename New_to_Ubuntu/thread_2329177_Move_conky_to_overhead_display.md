---
title: "Move conky to overhead display"
date: 2016-06-28
forum: New to Ubuntu
---

### Post by alexander.g.braun on 2016-06-28
I have a two monitor setup with monitor A above monitor B.  Conky natively appears on monitor B.  I am unable to move it to the above monitor A.  I have tried the gap_x, gap_y tricks, but to no avail.  Any suggestions would be appreciated.

Here is my .conkyrc:
```
background yes
use_xft yes
xftfont HandelGotD:size=11
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 220
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color grey
default_shade_color red
default_outline_color green
alignment top_right
gap_x 5
gap_y 5
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes


TEXT


$sysname $kernel on $machine


Uptime $alignr $uptime


CPU $alignr ${cpu cpu0}%
${cpubar cpu0}


Core1 $alignr ${cpu cpu1}%
${cpugraph cpu1}
Core2 $alignr ${cpu cpu2}%
${cpugraph cpu2}
Core3 $alignr ${cpu cpu3}%
${cpugraph cpu3}
Core4 $alignr ${cpu cpu4}%
${cpugraph cpu4}
RAM $alignc $mem / $memmax $alignr $memperc%
$membar


swap $alignc $swap / $swapmax $alignr $swapperc%
$swapbar


/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}


$processes processes ($running_processes running)


NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}


CPU temp:$alignr${hwmon temp 1}°C
Core1 temp:$alignr${hwmon temp 2}°C
Core2 temp:$alignr${hwmon temp 3}°C
GPU temp: $alignr ${execi 60 nvidia-settings -query GPUCoreTemp | perl -ne 'print $1 if /GPUCoreTemp.*?: (\d+)./;'}°C
GPU Usage: $alignr ${exec nvidia-smi | grep % | cut -c 62-63} %
${execgraph nvidia-smi | grep % | cut -c 62-63}
GPU VRAM: $alignr ${exec nvidia-smi | grep % | cut -c 37-40}MB


Inbound $alignr ${downspeed eth0}
${downspeedgraph eth0}
Outbound $alignr ${upspeed eth0}
${upspeedgraph eth0}

```

---

