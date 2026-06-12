---
title: "conky disappear"
date: 2014-12-22
forum: New to Ubuntu
---

### Post by unreal2 on 2014-12-22
Hi,

ubuntu 14.04 x64bit  unity 

```
ad@pc:~$ cat /proc/version
Linux version 3.13.0-43-generic (buildd@tipua) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014
```

My conky works  few minutes and disappears. (proces worked)
How do I check the cause ?

---

### Post by deadflowr on 2014-12-22
First post your conkyrc,
and then post the output of what you see when you run conky from a terminal.

---

### Post by unreal2 on 2014-12-22
```
ad@pc:~$
ad@pc:~$ killall conky
 ad@pc:~$ conky
Conky: can't open '/sys/class/hwmon/hwmon0/temp2_input': No such file or directory
please check your device or remove this var from Conky
Conky: forked to background, pid is 4215
ad@pc:~$
Conky: desktop window (2a0000a) is subwindow of root window (254)

```
> Now for example i opened a virtualbox and conky disappears.
```

Conky: desktop window (2a0000a) is subwindow of root window (254)
Conky: window type - desktop
Conky: drawing to created window (0x3c00001)
Conky: drawing to double buffer
sh: 1: /home/ad/conky/hddtemp: not found
sh: 1: /home/ad/conky/nvidia: not found
sh: 1: /home/ad/conky/gmail: not found
sh: 1: /home/ad/conky/hddtemp: not found
sh: 1: /home/ad/conky/nvidia: not found
sh: 1: /home/ad/conky/gmail: not found
```
I found on the internet.( copy and paste).
```
background yes
use_xft yes
xftfont Zekton:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
double_buffer yes
no_buffers no
own_window yes
own_window_transparent yes
own_window_type desktop
own_window_hints undecorate,sticky,skip_taskbar,skip_pager
minimum_size 500 5
maximum_width 250
default_color white
alignment top_right
gap_x 12
gap_y 35
uppercase no
override_utf8_locale yes

TEXT

${color #ddaa00}System $hr

${color white}Ubuntu 8.04 "Hardy Heron"
${color white}$sysname ${color white}$kernel (${color white}$machine)
${color white}Procesy: $processes ${color white}w trakcie: $running_processes
${color white}Czas pracy: $uptime

${color #ddaa00}Temperatura $hr

${color white}Procesor: $alignr ${hwmon temp 1}°C  ${hwmon temp 2}°C
${color white}Temperature: ${alignr}${acpitemp}C
${color white}Dysk twardy: $alignr ${execi 60 ~/conky/hddtemp}°C
${color white}NVidia GeForce 7300GT: $alignr ${execi 60 ~/conky/nvidia}°C

${color #ddaa00}Procesor $hr
${color white}CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${color white}CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
$stippled_hr
${color white}Najwi&#281;cej CPU: $alignr ${color white}CPU%
${color white}${top name 1} $alignr ${top cpu 1}
${color white}${top name 2} $alignr ${top cpu 2}
${color white}${top name 3} $alignr ${top cpu 3}

${color #ddaa00}Pami&#281;&#263; RAM $hr
${color white}RAM: ${memperc}% ${membar}

$stippled_hr
${color white}Najwi&#281;cej RAM: $alignr ${color white}RAM%
${color white}${top_mem name 1} $alignr ${top_mem mem 1}
${color white}${top_mem name 2} $alignr ${top_mem mem 2}
${color white}${top_mem name 3} $alignr ${top_mem mem 3}

${color #ddaa00}Dyski $hr

${color white}home: ${fs_used /}/${fs_size /} $alignr ${fs_used_perc /}%
${color white}${fs_bar /}
${color white}swap: ${swap}/${swapmax} $alignr ${swapperc}%
${color white}${swapbar}

${color #ddaa00}Internet $hr

${color white}IP: ${color white}${addr ppp0}
${color white}Pobieranie: ${downspeedf ppp0} KB/s $alignr ${totaldown ppp0}
${color white}Wysy&#322;anie: ${upspeedf ppp0} KB/s $alignr ${totalup ppp0}

${color #ddaa00}Poczta $hr

${color white}${execi 60 ~/conky/gmail}
```

---

### Post by NM5TF on 2014-12-22
try this code:

```
own_window_type normal
```

when it is set to Desktop, every time you press a key it will disappear...

the other error messages point to the fact that you just did a copy & paste of someone else's code that is optimized for THEIR MACHINE....

if you want to use this conky.rc file you will have to modify it for YOUR MACHINE......and for that you will need to know your hardware...

do you have a Nvidia 7300GT video adapter installed....do you use gmail.....do you have the app hwmon installed ???

the error messages tell me that you don't....

there is a good thread about using conky for a system monitor & weather forecast application here:

[http://ubuntuforums.org/showthread.php?t=1771033&page=193](http://ubuntuforums.org/showthread.php?t=1771033&page=193)

this is a very long thread that has been going on for a long time now, but it is very helpful for someone new to conky...you might start at the
end & go back until you find what you need....

tommy

---

### Post by unreal2 on 2014-12-22
> own_window_type normal

It works. Thanks.

> if you want to use this conky.rc file you will have to modify it for YOUR MACHINE

I know but I had no time.

---

### Post by sandyd on 2014-12-22
Hi, if you have sound a solution to your thread, please mark this thread as solved by going to Thread Tools -> Mark as Solved.

Thanks!

---

