---
title: "Conky issues"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Inxsible on 2008-08-11
I have an 'if_running' clause for mpd and an 'if_mounted' clause for my external drive.

However, I think its not checking the conditions because I get these errors on my vc/1

```
Conky: statfs '/media/WD500' : No such file or directory

Conky: MPD error: problems getting a response from localhost on port 6600: Connection refused
```Needless to say this is on a fresh boot up and I still havent mounted my external drive and neither started mpd daemon.

Here's my conkyrc ```
background yes
font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 210 5
maximum_width 210
default_color white
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 6
gap_y 22
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer none
#User: $alignr$user_names
#Computer: $alignr$nodename
TEXT
${offset 80}${font openlogos-archupdate:size=40}${color blue}B${font}${color}
${font DigitalReadoutExpanded:style=Bold:pixelsize=25}${alignc}${time %r}${font Snap.se:size=8}
${alignr}${time %A, %e %B %G}
${font Aerial:style=Bold:pixelsize=12}CALENDAR${font Snap.se:size=8}${hr 1}
${font DejaVu Sans Mono :size=12}${pre_exec cal}
${font DejaVu Sans Mono :size=6}${pre_exec cal -3 | cut -c23-44 --complement}
${font Aerial:style=Bold:pixelsize=12}SYSTEM${font Snap.se:size=8} ${hr 1 }
$alignc$sysname $kernel ($machine)
Uptime: $alignr$uptime
Load: ${alignr}$loadavg
Processes: ${alignr}$processes ($running_processes running)
${font Snap.se:size=8}${hr 1 }
Highest CPU%
${color red}${top name 1}${top cpu 1}
${color}${top name 2}${top cpu 2}
${top name 3}${top cpu 3}
${top name 4}${top cpu 4}
${font Snap.se:size=8}${hr 1 }
Highest MEM%
${color red}${top_mem name 1}${top_mem mem 1}
${color}${top_mem name 2}${top_mem mem 2}
${top_mem name 3}${top_mem mem 3}
${top_mem name 4}${top_mem mem 4}
${font Snap.se:size=8}${hr 1 }
Battery ${alignr}(${battery BAT1})
${battery_bar 4 BAT1}
CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph 0000ff 00ec00}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

${font Aerial:style=Bold:pixelsize=12}FILE SYSTEM${font Snap.se:size=8}${hr 1}
ROOT: ${alignr}${fs_used /} / ${fs_size /}
${fs_bar 4 /}
HOME: ${alignr}${fs_used /home} / ${fs_size /home}
${fs_bar 4 /home}
${if_mounted /media/WD500}WD500: ${alignr}${fs_used /media/WD500} / ${fs_size /media/WD500}
${fs_bar 4 /media/WD500}
$endif
${font Aerial:style=Bold:pixelsize=12}CONNECTION${font Snap.se:size=8}${hr 1}
Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 000000 ffffff} ${alignr}${upspeedgraph eth0 25,107 000000 ffffff}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

${if_running mpd}
${font Aerial:style=Bold:pixelsize=12}$mpd_status ${font Snap.se:size=8} ${hr 1 }
$mpd_smart $mpd_elapsed/$mpd_length
$mpd_album 
$endif
```How can I get rid of these issues?

---

### Post by Inxsible on 2008-08-12
Once I mount the WD500 and start mpd, the errors stop appearing on my screen.

My question is, why does it keep checking for mpd and the mount point even if there are "if conditions" on it?

Shouldn't it just check to see if mpd is running ...and if it is not, then just not take any action? Why does it keep giving those errors?

---

### Post by mc4100 on 2008-08-12
I'm unsure why you're getting the errors, but if it's really bugging you, then why not have a script that waits five minutes after your login, and then stars conky, like, I don't know:
```
#!/bin/bash
sleep 300
conky
```
So that way, you have time to mount the drive, and start MPD.

---

### Post by Inxsible on 2008-08-12
> **mc4100 said:**
> I'm unsure why you're getting the errors, but if it's really bugging you, then why not have a script that waits five minutes after your login, and then stars conky, like, I don't know:
```
#!/bin/bash
sleep 300
conky
```So that way, you have time to mount the drive, and start MPD.Thanks, but that's not what I am looking for. I just needed to understand how conky works and why wouldn't it honor the "if" conditions. The error is not such a big deal to me.

I can always append startx output to /dev/null, in bash_profile or .xinitrc and never see those errors.

---

### Post by kaivalagi on 2008-08-12
> **Inxsible said:**
> I have an 'if_running' clause for mpd and an 'if_mounted' clause for my external drive.

However, I think its not checking the conditions because I get these errors on my vc/1

```
Conky: statfs '/media/WD500' : No such file or directory

Conky: MPD error: problems getting a response from localhost on port 6600: Connection refused
```Needless to say this is on a fresh boot up and I still havent mounted my external drive and neither started mpd daemon.


I have a similar issue when using if_running for xmms2, for each refresh I get the following console output:

Conky: xmms2 connection failed. xmms2d is not running.

Again if I running xmms2 then console output stops...

You would expect the if_running to only try the enclosed variables if satisfied, but I think it must just defer the text output only.

Must be a conky "feature" :)

You could try asking why at the #conky irc channel on freenode? Maybe there is an compile option or a setting to use at run time to stop this?

---

### Post by houbysoft.xf.cz on 2008-08-12
It's not a bug, just an undocumented feature. :) :) :)

---

### Post by nicedude on 2008-08-12
I see Ubuntu has conky 1.51-1 in the repos, but conky at sourceforge is at 1.6.0 and I see in the change log at least 1 thing that sounds close. Here are the change that could be related I saw, but could be more that apply check the changelog at sourceforge as there are a whole page of updates since 1.5.1 .

2008-07-16
	* Fixed bug with $if_empty and $mpd_* vars (sf.net #2008752)


I guess if one of the changes is it you will have to compile from source.

Hope this helps

---

### Post by Inxsible on 2008-08-12
Maybe thats it !! Thanks nicedude.

I will try and install from source and see if that works out. However, the conky website still says that the latest stable release is 1.5.1-1. But on the download page, it also has 1.6.0 under stable releases.

Maybe they haven't updated the site yet !

---

