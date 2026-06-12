---
title: "Conky problem"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by tomzzv3 on 2008-06-18
i cannot start conky on startup or from terminal it keeps saying segmentation  fault. Here is my output  in terminal.

thomas@thomas-desktop:~$ conky
Conky: diskio device '20' does not exist
Conky: desktop window (12000ad) is subwindow of root window (88)
Conky: window type - normal
Conky: drawing to created window (3200001)
Conky: drawing to double buffer
Segmentation Fault


Here is my conkyrc configuration file.



background no
use_xft yes
xftfont Hemi head 426:size=6.5
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 300
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase yes

TEXT
$stippled_hr
$nodename - $sysname $kernel ($machine)
$stippled_hr

Kernel: $alignr $kernel
Uptime: $alignr $uptime

$stippled_hr
SYSTEM
$stippled_hr

CPU0: ${alignr} ${cpu cpu0}%
${cpugraph 20}
Load: $alignr $loadavg
Processes: $alignr $processes
Running: $alignr $running_processes

RAM: $alignr $mem/$memmax
${membar 3}
Swap: $alignr $swap / $swapmax
${swapbar 3}

Name $alignr  PID      CPU    MEM 
${color #ddaa00} ${top name 1} $alignr ${top pid 1} ${top cpu 1} ${top mem 1}$color
 ${top name 2} $alignr ${top pid 2} ${top cpu 2} ${top mem 2}
 ${top name 3} $alignr ${top pid 3} ${top cpu 3} ${top mem 3}
 ${top name 4} $alignr ${top pid 4} ${top cpu 4} ${top mem 4}
 ${top name 5} $alignr ${top pid 5} ${top cpu 5} ${top mem 5}
 ${top name 6} $alignr ${top pid 6} ${top cpu 6} ${top mem 6}
 ${top name 7} $alignr ${top pid 7} ${top cpu 7} ${top mem 7}
 ${top name 8} $alignr ${top pid 8} ${top cpu 8} ${top mem 8}
 ${top name 9} $alignr ${top pid 9} ${top cpu 9} ${top mem 9}
 ${top name 10} $alignr ${top pid 10} ${top cpu 10} ${top mem 10}

Mem usage$color
${color #ddaa00} ${top_mem name 1} $alignr ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}$color
 ${top_mem name 2} $alignr ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
 ${top_mem name 3} $alignr ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
 ${top_mem name 4} $alignr ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}
 ${top_mem name 5} $alignr ${top_mem pid 5} ${top_mem cpu 5} ${top_mem mem 5}
 ${top_mem name 6} $alignr ${top_mem pid 6} ${top_mem cpu 6} ${top_mem mem 6}
 ${top_mem name 7} $alignr ${top_mem pid 7} ${top_mem cpu 7} ${top_mem mem 7}
 ${top_mem name 8} $alignr ${top_mem pid 8} ${top_mem cpu 8} ${top_mem mem 8}
 ${top_mem name 9} $alignr ${top_mem pid 9} ${top_mem cpu 9} ${top_mem mem 9}
 ${top_mem name 10} $alignr ${top_mem pid 10} ${top_mem cpu 10} ${top_mem mem 10}

$stippled_hr
HDD
$stippled_hr

 Write: $alignr $diskio_write
${diskiograph_write 20}
 Read: $alignr $diskio_read
${diskiograph_read 20}

ROOT: $alignr ${fs_free /} / ${fs_size /}
${fs_bar 3 /}
My Book: $alignr ${fs_free /media/My Book} / ${fs_size /media/My Book}
${fs_bar 3 /media/My Book}

$stippled_hr
Network
$stippled_hr

IP on wlan0 $alignr ${addr wlan0}

Down:
${color #ddaa00} Speed: $alignr ${downspeed wlan0} k/s$color
 Tot: $alignr ${totaldown wlan0}

${downspeedgraph wlan0 20} ${alignr}${upspeedgraph wlan0 20}

Up:
${color #ddaa00} Speed: $alignr ${upspeed wlan0} k/s$color
 Tot: $alignr ${totalup wlan0}

${upspeedgraph wlan0 20} ${alignr}${upspeedgraph wlan0 20}


I also have a file in my home dirrectory called .conkyrc.swp I was just wondering if i need this or should i delete it.

---

### Post by Joeb454 on 2008-06-18
```
mv ~/.conkyrc.swp ~/conkyrc-backup
``` just to make sure that it isn't causing issues :)

Though I'm not sure why you're getting a seg-fault :confused:

---

### Post by tomzzv3 on 2008-06-18
after doingg that and dleteing i get 

thomas@thomas-desktop:~$ conky
Conky: diskio device '20' does not exist
Conky: desktop window (12000ad) is subwindow of root window (88)
Conky: window type - normal
Conky: drawing to created window (2e00001)
Conky: drawing to double buffer
Segmentation fault
thomas@thomas-desktop:~$

---

