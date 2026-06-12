---
title: "[SOLVED] Traffic, Bandwidth monitor or tracker program"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Redptc on 2008-05-02
Is there a GUI program to monitor the bandwidth or internet usage? :confused:

---

### Post by iSplicer on 2008-05-02
Sure is.

Its called conky, its a monitor thats on your desktop, very customizable. 

sudo apt-get install conky

then alt+f2 type

conky

You will need to set it up though

---

### Post by Redptc on 2008-05-03
Nothing shows on the 'networking' category...up: 0 k/s down: 0 k/s

Any ideas, shouldn't this show networking access?

---

### Post by iSplicer on 2008-05-03
> **Redptc said:**
> Nothing shows on the 'networking' category...up: 0 k/s down: 0 k/s

Any ideas, shouldn't this show networking access?

You need to edit your .conkyrc config file, my friend. Go to /home, hit ctrl+h to see hidden stuff and open .conkyrc.

Go to terminal, type ifconfig, and see what network interface you are using for your internet connection eg eth0 ath0 wlan0, etc.

Paste your .conkyrc file here and I will go ahead and change it for you!

---

### Post by Redptc on 2008-05-03
I can't find .conkyrc at /home??? I did download via Synaptic manager!

PS did use ctl/h

---

### Post by cubeist on 2008-05-03
For an easier solution, the built in system monitor keeps a running total of up and down network traffic since your last launch.  Just open it and then minimize and it will add up your total usage.

---

### Post by iSplicer on 2008-05-03
Try the following:

```
cp /etc/conky/conky.conf ~/.conkyrc
```

Open the file:

```
gedit ~/.conkyrc
```

And post it here, and I (or someone else) will change it for you so you can see your network. Also post the output of 

```
ifconfig
```

Thanks

---

### Post by Redptc on 2008-05-03
This is the result......

# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2007 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
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
# $Id: conky.conf 990 2007-11-22 19:38:17Z pkovacs $

alignment bottom_left
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
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no

TEXT
$nodename - $sysname $kernel on $machine
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
$hr
${color grey}Name                  PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}



Ifconfig indicates eth0, eth1

---

### Post by iSplicer on 2008-05-03
> **Redptc said:**
> Ifconfig indicates eth0, eth1

Which one is plugged into your internet?

---

### Post by iSplicer on 2008-05-03
OK, since eth0 did not work for you, I have used eth1. Just paste this as your .conkyrc file:

```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2007 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program. If not, see <http://www.gnu.org/licenses/>.
#
# $Id: conky.conf 990 2007-11-22 19:38:17Z pkovacs $

alignment bottom_left
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
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no

TEXT
$nodename - $sysname $kernel on $machine
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
/ $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth1} k/s${color grey} - Down:$color ${downspeed eth1} k/s
$hr
${color grey}Name PID CPU% MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}


```

I would still like an output of your ifconfig

---

### Post by Redptc on 2008-05-03
Here is ifconfig.......



eth0      Link encap:Ethernet  HWaddr 00:0F:B5:FF:5D:99  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:feff:5d99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3522055 (3.3 MB)  TX bytes:778007 (759.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:50:FC:E2:EC:8F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:800 (800.0 b)  TX bytes:800 (800.0 b)

---

### Post by iSplicer on 2008-05-03
OK it seems that eth0 is you internet interface (unless you are accessing internet through USB modem).

So your .conkyrc file would be:

```

# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2007 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program. If not, see <http://www.gnu.org/licenses/>.
#
# $Id: conky.conf 990 2007-11-22 19:38:17Z pkovacs $

alignment bottom_left
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
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no

TEXT
$nodename - $sysname $kernel on $machine
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
/ $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
$hr
${color grey}Name PID CPU% MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

```

---

### Post by Redptc on 2008-05-03
Still not working. I am on Netgear usb ethernet but not a modem. Appreciate the help!

---

### Post by cubeist on 2008-05-04
> **Redptc said:**
> Still not working. I am on Netgear usb ethernet but not a modem. Appreciate the help!

Did you try the system monitor? That should provide you with the basic information you were looking for... up/down totals.  Conky is a fine program, but it does take some effort to "tweak". On the other hand, system monitor is built into ubuntu...

---

### Post by Redptc on 2008-05-05
Yes, thanks Cubist, System Monitor works fine! I had hoped to be able to use Conky to develop a 'running' total of accumulated use but if I can't get it to even see the 'traffic' it isn't much good. 

With Conky there are a lot of things that can be personalised and there are a lot of Conky users willing to discuss and show their 'howtos'.

Thanks for your tip, your help is appreciated!

---

### Post by cubeist on 2008-05-06
> **Redptc said:**
> Yes, thanks Cubist, System Monitor works fine! I had hoped to be able to use Conky to develop a 'running' total of accumulated use (...)

Actually, if you open system monitor after you login and then minimize it, or move it to another workspace, it will sum your total up and down traffic... For example, since logging on an hour ago I have used 8.1/1.0 up and down...
cheers

---

### Post by Redptc on 2008-05-06
Again, thank you, Cubist! Oddly, I have been able to get Conky to do what I want, up to a point. I now have it doing the same thing as 'System Monitor'. 'System monitor' is very good and it tracks usage even if you don't 'click' on it. In other words it shows the use since the computer was turned on.

What I want is an accumulation of use over a few days, weeks or even months. I felt there must be some way of recording this so that I can verify that my usage tallies with the usage I am being charged for. 

Ever since I switched to Ubuntu my 'use' has skyrocketed! This may be the sheer delight of the operating system or even all the free downloads and updates, but, it would be nice to check.

At the moment, I can physically note the 'usage' with pen & paper each day but that hardly seems 'nerdy' enough!

---

### Post by Blutack on 2008-05-06
Easiest way I found for a friend.
[http://www.gnome-look.org/content/show.php/Net+Monitor?content=72013](http://www.gnome-look.org/content/show.php/Net+Monitor?content=72013)
You will need to install a program called Screenlets first.

---

### Post by Redptc on 2008-05-06
Looks interesting Blutack, I'll give it a try!

---

### Post by Redptc on 2008-05-07
Got this Screenlet up, Blutack, but it is not running all that well. It shows the down & up loads but does not show the monthly total.

Don't suppose you know how to fix it?

---

### Post by kpkeerthi on 2008-05-07
I use [vnstat]("http://www.cyberciti.biz/tips/keeping-a-log-of-daily-network-traffic-for-adsl-or-dedicated-remote-linux-box.html")

---

### Post by Redptc on 2008-05-07
Dear Kpkeerthi,
 
Sounds good, as did the others, as long as I can get it to work!

What are you running and which version of vnstat do you use. Everything seems to be able to do the job but I really don't need anything too fancy. 

This 'Screenlet' appears to be simple and made for a 'simple' mind like mine. It seems to work for a lot of people so perhaps I am just a tweak away.

After looking at your link, I can understand why you would use vnstat. It is clean, flexible and efficient. Is it complex to set-up?

---

### Post by kpkeerthi on 2008-05-07
vnstat is in universe repository. Before installing vnstat you need enable the universe repository from System -> Admin -> Software Sources. The current version in the repository is 1.6. Setting it up is very easy as you can see from the link I posted earlier.

Here it is again [http://www.cyberciti.biz/tips/keeping-a-log-of-daily-network-traffic-for-adsl-or-dedicated-remote-linux-box.html](http://www.cyberciti.biz/tips/keeping-a-log-of-daily-network-traffic-for-adsl-or-dedicated-remote-linux-box.html)

---

### Post by Redptc on 2008-05-07
Thanks Kp, I think it works but I guess I need to accumulate more statistics to know how well it works. I appreciate your persistence and patience with me.

---

### Post by minuxx on 2008-05-17
Sorry to get in between but I am using the ubuntu server edition 64bit and I too would like to know if there is anything that keeps track of my ping to a specific source as well as logging that to a file ?

---

### Post by Liet_Kynes on 2008-05-17
> **kpkeerthi said:**
> I use [vnstat]("http://www.cyberciti.biz/tips/keeping-a-log-of-daily-network-traffic-for-adsl-or-dedicated-remote-linux-box.html")

Can vnstat monitor two seperate pppoe connections?

---

### Post by Vergo on 2008-05-17
> **Liet_Kynes said:**
> Can vnstat monitor two seperate pppoe connections?

Yes it can. It should be able to monitor any number of interfaces as long as the kernel provides traffic information for the selected interfaces. Currently virtual interfaces seem to be the only ones that aren't supported.

---

### Post by Redptc on 2008-05-17
This thread worked out very nicely,I got 4 different ways of resolving my question!

Cubeist suggested using 'System>Administration>System Monitor' Quick and is simple but doesn't accumulate results.

Ispicer suggested Conky which is great and you can tweak-it into some wonderful configurations. Search these forums to find ways of doing it. You can develop a very personal piece of beneficial 'eye-candy'. Thanks for all your help!

Blutack suggested a screenlet, [HTML]http://www.gnome-look.org/content/sh...?content=72013[/HTML]  terrific screenlet, once up right click on it to 'customise'.       (Thanks also to DRXNELE at Gnome-look.org for his help.)

Kpkeethi recommended ***Vnstat*** follow his links in this thread for an easy set-up for what I think is ideal!

Thanks everybody!

---

### Post by Liet_Kynes on 2008-05-18
> **Vergo said:**
> Yes it can. It should be able to monitor any number of interfaces as long as the kernel provides traffic information for the selected interfaces. Currently virtual interfaces seem to be the only ones that aren't supported.

Thanks. I've been using Bandwithd but it monitors based on IPs and I needed something to monitor 2 ppp connections

---

