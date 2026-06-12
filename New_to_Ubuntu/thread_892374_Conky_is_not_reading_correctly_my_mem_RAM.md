---
title: "Conky is not reading correctly my mem RAM"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by esemns on 2008-08-17
Hi, i have this problem where my conky read that I'm using 98% of my RAM, when i go to gnome-monitor it's says I'm using 56% of it, everything else in conky reads fine, cpu usage, swap, root and home size except for the ram memory usage.

This is my .conkyrc

```
# Conky configuration
background yes
use_xft yes
xftfont URW Gothic L:size=11
out_to_console no
update_interval 1
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 5
border_margin 4
border_width 1
default_color black
default_shade_color black
default_outline_color black
alignment middle_right
gap_x 30
gap_y 47
no_buffers no
uppercase no
cpu_avg_samples 2
override_utf8_locale yes

TEXT
$alignc$sysname $kernel on $machine
$alignc${exec whoami} @ $nodename

Fecha:${alignr}${time %A, %d %B}
Hora:${alignr}${time %I:%M:%S}${alignr}
T. Encendido:${alignr}$uptime

CPU:$alignc${cpu cpu1}% 
${cpubar cpu1}
RAM:$alignc$memperc%
$membar
Swap:$alignc$swapperc%
$swapbar

${alignc}Sistema de Ficheros
root ${alignr}${fs_used /} de ${fs_free /}
${fs_bar /}
Home ${alignr}${fs_used /home/jesus/} de ${fs_free /home/jesus}
${fs_bar /home/jesus}
```

Thanks for your help.

---

### Post by Mud.Knee.Havoc on 2008-08-17
I think it's fine.  I've read quite a few posts about people worrying about displayed RAM usage, but people often reply that it's supposed to be that way (due to the particular way Linux manages memory).

---

### Post by hyper_ch on 2008-08-17
run
```

free -m

```

---

### Post by esemns on 2008-08-17
Ok, but why gnome system monitor show something and conky shows another, shouldn't they be reading mem usage from the same source or something like that?

---

### Post by nicedude on 2008-08-17
They more than likely don't use the same command or source so to speak for that number and therefore the discrepancy. I wouldn't worry about it. With linux there is always more than one way to skin the cat (so to speak) and they are probably just skinning him with 2 separate ways :-)

---

### Post by esemns on 2008-08-17
Now the real question is (and I know it is not a big issue but...) how to get conky to read the real mem usage

---

### Post by cleopete on 2008-10-27
I have the same issue.  The problem seems to be with the data refresh. On mine, the RAM usage just goes up and never comes back down.  It's not really a usage bar so much as a record of peak usage.

Is this what yours is doing?

I haven't had this problem with any other stats.

---

### Post by reg4c on 2008-10-27
Connky has a bug that I notices as well

The amount of memory that it shows in use is the actually amount in use plus the cached amount

Put ${cached} under the free memory in your .conkyrc and then memory in use [not in percents] minus cached is the amount in use that gnome-system-monitor

Cheers

---

### Post by deh1963 on 2008-12-05
Could I please trouble someone for a line of code that I can insert into conky to accomplish this subtraction function?

Thanks in advance.

---

### Post by Raffles10 on 2009-02-28
I know it's been awhile since the last post in this thread, but I found an answer to this problem that others might find useful. :D

Conky shows the amount of RAM actually being used + cached memory, unlike HTOP which just shows the former. To get Conky's RAM display to match HTOP's just change the buffer setting:

```
no_buffers yes
```

This shows just the value of the actual ram being used.

---

### Post by archeryguru2000 on 2009-03-02
> **hyper_ch said:**
> run
```

free -m

```

I've received an interesting response to this command. :-k 
```

$: free -m
             total       used       free     shared    buffers     cached
Mem:          2978        795       2183          0         11        386
-/+ buffers/cache:        396       2582
Swap:            0          0          0

```
Could anyone explain that one?  I never realized that my swap was not being utilized (I think that is what this means).  Is there any way to modify this?

~~archery~~

---

### Post by hyper_ch on 2009-03-05
enable it in your fstab

---

### Post by archeryguru2000 on 2009-03-06
Thank you very much for the response hyper_ch.  I also found [**_[COLOR="Blue"]this thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=691986").  Now my swap prob's are solved.  Thanks.

~~archery~~

---

