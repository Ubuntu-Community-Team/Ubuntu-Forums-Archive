---
title: "Configuring Conky"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by brickmack on 2012-06-18
So, I just got Ubuntu about 12 hours ago, so its entirely possible I'm just making some obvious mistake, but here is my problem.

Using the instructions here: [https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky) I got Conky installed, and it works fine. However, when I got to the part in the instructions where it said to create the .conkyrc folder, put it a copy of conky.conf from the /etc/conky folder, edit that, and then run the killall -SIGUSR1 conky

command, I ran into a problem. I made a few changes from the default
settings, saved it, and ran the command, but it didn't work. Conky
restarted, but it was still using the original configuration. Here is
the conky.conf file right now:
```

alignment top_right
background yes
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
xftfont DejaVu Sans Mono:size=12
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${scroll 16 $nodename - $sysname $kernel on $machine | }
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
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
```I've changed alignment to top_right from top_left, changed background to yes, and removed the frequency in GHz line. It shows the same as it did before I changed anything, though. Any help?

---

### Post by stinkeye on 2012-06-19
You don't create a **.conkyrc** folder. You create a **.conkyrc** file. 
Copy the default config at **/etc/conky/conky.conf **to your home folder and rename as **.conkyrc**

Run this in the terminal to do just that.
```
cp /etc/conky/conky.conf $HOME/.conkyrc
```

Then to edit... 
Open your home folder and open **.conkyrc** with gedit.
The file will be hidden.(ctrl+h to show hidden)
**[SIZE="3"]or[/SIZE]**
Run in the terminal
```
gedit ~/.conkyrc
```

---

### Post by brickmack on 2012-06-19
^ Ok, looks like I misunderstood that part of the instructions. I did all of that stuff, edited the new file, and then when I ran the killall -SIGUSR1 conky command, it did the same thing as before. Conky restarted, but using the original conky.conf file.

EDIT: Nevermind, I got it. Just had to click elsewhere on the desktop to close conky, then run conky & to restart it, and it worked. Thanks.

---

### Post by stinkeye on 2012-06-19
Add these settings to your config above "TEXT" to stop conky disappearing when you click the desktop.
```
own_window yes
own_window_type override
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky

```

Also when you add conky to startup applications use the 
inbuilt delay so it loads after the window manager.
eg...delays conky start for 20 secs.
```
conky -p 20
```

---

