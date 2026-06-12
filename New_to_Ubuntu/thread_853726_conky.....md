---
title: "conky...."
date: 2008-07-08
forum: New to Ubuntu
---

### Post by fignig on 2008-07-08
where is this conkyrc file? so i can edit it to my own satisfaction...

---

### Post by sharks on 2008-07-08
its in home folder(hidden). its name is .conkyrc

---

### Post by spiderbatdad on 2008-07-08
create one in your home folder...called: .conkyrc 

That is; (dot)conkyrc

---

### Post by Dr Small on 2008-07-08
Check here:
```
/etc/xdg/conky/conky.conf
```

That's where I found it on mine.

---

### Post by tad1073 on 2008-07-08
.conkyrc is stored in your home folder

[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

---

### Post by fignig on 2008-07-08
> **sharks said:**
> its in home folder(hidden). its name is .conkyrc

that's neat how u tell me it's hidden, and u don't tell me how u find it...

---

### Post by Dr Small on 2008-07-08
> **fignig said:**
> that's neat how u tell me it's hidden, and u don't tell me how u find it...
By default, there shouldn't be a .conkyrc in your home folder. You have to create one, or use one from someone else.

---

### Post by tjwoosta on 2008-07-08
usually there is no ~/.conkyrc untill you make it

---

### Post by fignig on 2008-07-08
> **tjwoosta said:**
> usually there is no ~/.conkyrc untill you make it

FINALLY! someone w/ a ******* brain...

---

### Post by fignig on 2008-07-08
how do i make .conkyrc if it won't let me?

---

### Post by tjwoosta on 2008-07-08
ok

first find a .conkyrc you like that someone else made

here is a good place to start
[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

then do

```
sudo gedit ~/.conkyrc
```

(this opens a blank text document)

just copy and paste the .conkyrc right from the thread into your text editor then save

now start conky

you may need to make minor changes to the .conkyrc  (like using wlan0 instead of eth0, or maybe changing some text or colors)

---

### Post by fignig on 2008-07-08
i keep getting the error:

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused


i tried changing all of the eth0 to wlan0, but that didn't work, or i didn't find all of them?

---

### Post by fignig on 2008-07-08
> **fignig said:**
> i keep getting the error:

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused


i tried changing all of the eth0 to wlan0, but that didn't work, or i didn't find all of them?

when i try to run conky thru terminal this is what follows it.

Conky: /home/pete/.conkyrc: 30: no such configuration: 'on_bottom'
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: desktop window (10000b6) is subwindow of root window (1a6)
Conky: drawing to desktop window
Conky: drawing to single buffer
Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

---

### Post by fignig on 2008-07-08
actually conky will open, but it just keeps flashing on and off. and i can't seem to position it to where i want it..

---

### Post by Metaleks on 2008-07-08
> **fignig said:**
> actually conky will open, but it just keeps flashing on and off. and i can't seem to position it to where i want it..
This is because you need scripting knowledge to tweak/edit .conkyrc to make it display how you want to. Check out this thread for some of people's conky files:

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Just take someone else's and play around with it.

---

### Post by tjwoosta on 2008-07-08
i think you should either try a different .conkyrc or edit that one

the errors that you are getting are coming from the conkyrc trying to do stuff that your computer doesnt have

> Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused 
this is probly somthing in the configuration trying to check email or something

like i said you may need to go through the configuration and change things to suit your computer

> Conky: /home/pete/.conkyrc: 30: no such configuration: 'on_bottom'

read line 30 of .conkyrc

---

### Post by SkonesMickLoud on 2008-07-09
Everything you need to know about conky can be found in these two threads:

[http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

and

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Both of which are found by using the search feature.

---

### Post by RiceMonster on 2008-07-09
> **tjwoosta said:**
> ok

first find a .conkyrc you like that someone else made

here is a good place to start
[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

then do

```
sudo gedit ~/.conkyrc
```

(this opens a blank text document)

just copy and paste the .conkyrc right from the thread into your text editor then save

now start conky

you may need to make minor changes to the .conkyrc  (like using wlan0 instead of eth0, or maybe changing some text or colors)

It's probably not a good idea to use sudo to edit ~/.conkyrc, since it's in your home directory. He then wouldn't have permissions to use it.

---

### Post by tjwoosta on 2008-07-09
> It's probably not a good idea to use sudo to edit ~/.conkyrc, since it's in your home directory. He then wouldn't have permissions to use it.

thats actually a good point

im just so used to throwing in a sudo

so it should be

```
gedit ~/.conkyrc
``` (NO SUDO)

---

### Post by akiratheoni on 2008-07-09
The best way for me to edit the .conkyrc was just to go through the post your .conkyrc files and find one I liked then copied it into .conkyrc and just edited it from there.

---

### Post by aktiwers on 2008-07-09
> **akiratheoni said:**
> The best way for me to edit the .conkyrc was just to go through the post your .conkyrc files and find one I liked then copied it into .conkyrc and just edited it from there.

Same for me

---

### Post by fignig on 2008-07-09
> **aktiwers said:**
> Same for me

that's what i'm trying to do, and i just keep running into errors. but i'm gonna try a few more, yay!

---

### Post by aktiwers on 2008-07-09
It is actually i little like HTML if you that. The {some stuff here} could be a color for next lines of code. or it could be a graph and so on. Look at the names inside the {} and it wont be to hard to figure out.

Also make sure the one you choose dont have another script it runs, that could cause errors, if you did not download the same script and place it in the same dir as the creator.

Else post your .conkyrc here and your errors or in the "post your .conkyrc" thread and I am sure people will help :)

---

### Post by fignig on 2008-07-09
okay i think i found a good one. is there anyway to make conky always stay on top but u can't click on it? or that would cause problems in itself... discuss, would it be logical? and or possible?

---

### Post by aktiwers on 2008-07-09
Open your .conkyrc file and search for:
own_window_hints

it probably has one or more words afterwards, like "below" or something.

Then replace it with this:
```
own_window_hints undecorated,below,skip_taskbar 
```

---

### Post by TheSlipstream on 2008-07-09
Well, I've been following this thread to create my own Conky install, which worked perfectly until I rebooted. It's in the Startup things, but nothing shows up at startup. When I try to open it through the terminal, I get this: Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Segmentation fault

It still doesn't show up. Help would be much appreciated!

---

### Post by aktiwers on 2008-07-09
Could you post the file here? I mean your .conkyrc :)
Then we can have a look

---

### Post by TheSlipstream on 2008-07-09
All right, here goes.

```
background yes
font Zekton:size=7
xftfont Zekton:size=7
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 220 5
maximum_width 220
default_color d7d7d7
default_shade_color black
default_outline_color black
alignment top_right
gap_x 10
gap_y 40
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
$nodename - $sysname $machine
$kernel
uptime $uptime  
freq ${freq}MHz   
load $loadavg    
${time %a %b %d %Y} ${alignr}

cpu0 ${cpu cpu0}% ${cpubar cpu0}
${cpugraph cpu0}

mem     $mem / $memmax $alignr $memperc%
$membar

swap    $swap / $swapmax $alignr $swapperc%
$swapbar

/           ${fs_used /} / ${fs_size /}$alignr${fs_free_perc /}%
${fs_bar /}

diskIO ${diskio}${diskiograph}

ip       ${execi 600  ruby -e "require 'net/http';Net::HTTP.get_print URI.parse('http://briancarper.net/cgi-bin/ip.cgi')"}
local ip ${addr eth0}

eth0 down ${downspeed eth0} k/s 
${downspeedgraph eth0}
eth0 up ${upspeed eth0} k/s
${upspeedgraph eth0}
total up ${totalup eth0}${alignr}total down ${totaldown ethO}

eth1 down ${downspeed eth1} k/s
${downspeedgraph eth1}
eth1 up ${upspeed eth1} k/s
${upspeedgraph eth1}
total up ${totalup eth1}${alignr}total down ${totaldown eth1}

${color #888888}Port(s)${alignr}#Conns   
$color Inbnd: ${tcp_portmon 1 32767 count}  Outbnd: ${tcp_portmon 32768 61000 count}${alignr}ALL: ${tcp_portmon 1 65535 count}
${color #999999}Inbnd Conn ${alignr} Loc Serv/Prt$color
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
${color #999999}Outbound Connection ${alignr} Remote Service/Port$color
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}


${color #999999}Top Processes:
${color #999999}Name              PID     CPU%   MEM%
$color ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
$color ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
$color ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #999999}Mem usage
$color ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
$color ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
$color ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

```

---

### Post by soxs on 2008-07-09
Either you write something and save it in your home dir named .conkyrc or you copy an allready existing one to your homefolder aka ~
there shouldn't be any issues

Note: .conkyrc is a hidden file, in fact there are a llot hidden config files in your hom dir, so press <STRG><H> to scho/hide them.

---

### Post by aktiwers on 2008-07-09
> **TheSlipstream said:**
> All right, here goes.

```
background yes
font Zekton:size=7
xftfont Zekton:size=7
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 220 5
maximum_width 220
default_color d7d7d7
default_shade_color black
default_outline_color black
alignment top_right
gap_x 10
gap_y 40
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer [COLOR=Red]no
[/COLOR] 
TEXT
$nodename - $sysname $machine
$kernel
uptime $uptime  
freq ${freq}MHz   
load $loadavg    
${time %a %b %d %Y} ${alignr}

cpu0 ${cpu cpu0}% ${cpubar cpu0}
${cpugraph cpu0}

mem     $mem / $memmax $alignr $memperc%
$membar

swap    $swap / $swapmax $alignr $swapperc%
$swapbar

/           ${fs_used /} / ${fs_size /}$alignr${fs_free_perc /}%
${fs_bar /}

diskIO ${diskio}${diskiograph}

ip       ${execi 600  ruby -e "require 'net/http';Net::HTTP.get_print URI.parse('http://briancarper.net/cgi-bin/ip.cgi')"}
local ip ${addr eth0}

eth0 down ${downspeed eth0} k/s 
${downspeedgraph eth0}
eth0 up ${upspeed eth0} k/s
${upspeedgraph eth0}
total up ${totalup eth0}${alignr}total down ${totaldown ethO}

eth1 down ${downspeed eth1} k/s
${downspeedgraph eth1}
eth1 up ${upspeed eth1} k/s
${upspeedgraph eth1}
total up ${totalup eth1}${alignr}total down ${totaldown eth1}

${color #888888}Port(s)${alignr}#Conns   
$color Inbnd: ${tcp_portmon 1 32767 count}  Outbnd: ${tcp_portmon 32768 61000 count}${alignr}ALL: ${tcp_portmon 1 65535 count}
${color #999999}Inbnd Conn ${alignr} Loc Serv/Prt$color
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
${color #999999}Outbound Connection ${alignr} Remote Service/Port$color
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}


${color #999999}Top Processes:
${color #999999}Name              PID     CPU%   MEM%
$color ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
$color ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
$color ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #999999}Mem usage
$color ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
$color ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
$color ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

```

A shot in the dark, but did you try set use_spacer to yes?

---

### Post by TheSlipstream on 2008-07-09
Well, I tried it, and it didn't work. :(

I'll go try some different code.

Edit: Problem resolved through use of different code!

---

