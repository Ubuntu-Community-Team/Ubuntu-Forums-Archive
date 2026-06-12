---
title: "Conky: Disappears from screen but is running"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-09-06
Conky simply disappears from screen (although it is running and doesn't seem to be crashed - you can see it is reading from its .conf file, allocating memory, etc). It just disappears. 

Same behavior using single or double buffer. Same thing using own_window or not. 

My compiz settings are default. Latest Proprietary NVidia Driver 64bits working flawlessly for 2d, 3d accel and video/vdpau, so I don't think this is the issue. Disabling compiz settings, effects, animations, makes no difference.

I can't find a way to properly reproduce the situation or locate the flaw since there is no crash/output. Seems aleatory. But it happens for me every 1 or 1,5 hours at most.

Is it working OK for other NVidia users?

Regards,
Effenberg

---

### Post by Quackers on 2011-09-06
It's fine here.
Are you using unity or gnome-shell?
Please post your .conkyrc content (before TEXT line)

---

### Post by wgarcia on 2011-09-06
For me conky is also working fine (in Unity). Only thing that I noticed after the 11.10 upgrade is that the default width got larger and that I had to start using a new parameter to fix this: maximum_width.

---

### Post by Quackers on 2011-09-06
Is it going off when you click/right-click on the desktop background?

---

### Post by wgarcia on 2011-09-06
Quackers, if you are asking me, no, it just starts and stays wider under 11.10 than under 11.04. I haven't checked but conky's version may have changed.

---

### Post by Quackers on 2011-09-06
No wgarcia :-) I was asking the OP.
The problem with the width appeared for me when the new conky-all update was run a couple of weeks ago.

---

### Post by Script Warlock on 2011-09-06
don't know if we have the same issue before, what i did as suggested is make the window_type own or normal and not desktop. or a startup script and delay the sleep until everything ubuntu loads.

---

### Post by effenberg0x0 on 2011-09-06
Thanks for all the replies guys. Here's my conky.conf:

```


$ sudo cat /etc/conky/conky.conf
[sudo] password for al: 
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2010 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

double_buffer yes
own_window yes
own_window_class Conky
own_window_type desktop

alignment top_right

background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=8
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${color grey}$nodename - $sysname $kernel on $machine
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (MHz/GHz):$color $freq/$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} ${color grey} - Down:$color ${downspeed eth0}
$hr
${color grey}Name              PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color lightgrey} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}
${color lightgrey} ${top name 6} ${top pid 6} ${top cpu 6} ${top mem 6}
${color lightgrey} ${top name 7} ${top pid 7} ${top cpu 7} ${top mem 7}
${color lightgrey} ${top name 8} ${top pid 8} ${top cpu 8} ${top mem 8}
${color lightgrey} ${top name 9} ${top pid 9} ${top cpu 9} ${top mem 9}
${color lightgrey} ${top name 10} ${top pid 10} ${top cpu 10} ${top mem 10}
$hr
${color grey}Local Temperatures:
${color lightgrey} CPU: ${execi 6 /usr/bin/sensors | grep "CPU Temperature:"| paste -s | cut -c23-26}
${color lightgrey} MB:  ${execi 6 /usr/bin/sensors | grep "MB Temperature:"| paste -s | cut -c23-26}
$hr
${color grey}Remote Temperatures:
NAS HDD01 (sda):${hddtemp /dev/sda 192.168.1.3 7634}
NAS HDD02 (sdb):$alignr{hddtemp /dev/sdb 192.168.1.3 7634}
NAS HDD03 (sdc):$alignr {hddtemp /dev/sdc 192.168.1.3 7634}
NAS HDD04 (sdd):$alignr {hddtemp /dev/sdd 192.168.1.3 7634}
NAS HDD05 (sde):$alignr {hddtemp /dev/sde 192.168.1.3 7634}
NAS HDD06 (sdf):$alignr {hddtemp /dev/sdf 192.168.1.3 7634}

```

Quackers => I am using Unity. Clicking / right-clicking the desktop doesn't seem to be related to it disappearing.

Regards,
EFfenberg

---

### Post by effenberg0x0 on 2011-09-06
Script Warlock => No luck, same behavior with own_window and desktop.

Regards,
Effenberg

---

### Post by Quackers on 2011-09-06
Do you have a hidden file in your home folder called .conkyrc 
You will need to press ctrl + h to see it.
The conky.conf file you posted is a standard one (I think). The hidden .conkyrc file will be the file that is controlling everything - or it is here :-)

---

### Post by effenberg0x0 on 2011-09-07
Script Warlock
> don't know if we have the same issue before, what i did as suggested is make the window_type own or normal and not desktop. or a startup script and delay the sleep until everything ubuntu loads. 

I didn't take the "delay" advice serious when you first mentioned it but that is what fixed my problem. If I take conky off startup and manually start it after the system is fully loaded, or if I add like a 30 seconds sleep to its init script, I no longer get the disappearing problem.

Thank you,
Effenberg

---

### Post by Quackers on 2011-09-07
Glad you sorted things out :-)
A sleep parameter seems to work better nowadays. It's something to do with how the desktop is drawn, I think.

---

