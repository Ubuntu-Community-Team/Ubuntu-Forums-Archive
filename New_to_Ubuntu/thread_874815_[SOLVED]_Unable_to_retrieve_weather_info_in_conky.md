---
title: "[SOLVED] Unable to retrieve weather info in conky"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-30
I have weather.sh and weather.xslt in ~/scripts and I think I already configure my conky right (according to [tutorial]("http://ubuntuforums.org/showpost.php?p=4157750&postcount=1489")). However, I do not get the weather info as expected. When run conky in Terminal, I get this error message:

aznan@aznan-laptop:~$ conky
Conky: desktop window (10000c9) is subwindow of root window (59)
Conky: window type - normal
Conky: drawing to created window (3000001)
Conky: drawing to double buffer
/home/aznan/scripts/weather.sh: 14: ~[My: not found
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -

Can anyone interpret this error message for me..

---

### Post by halitech on 2008-07-30
did you put in the proper city code for your area in the xslt file?

---

### Post by wariskampar on 2008-07-30
I just put loc code in weather.sh and conkymain. Do I need to alter .xslt as well.

---

### Post by wariskampar on 2008-07-30
Going down the tutorial, I found this instruction 'This file gives you the coding necessary to edit weather.xslt the way you want. Following the instruction, I get this code;

> &#8722;
<!--
This document is intended only for use by authorized licensees of The Weather Channel. Unauthorized use is prohibited. Copyright 1995-2005, The Weather Channel Interactive, Inc. All Rights Reserved.
-->
&#8722;
<weather ver="2.0">
&#8722;
<head>
<locale>en_US</locale>
<form>MEDIUM</form>
<ut>C</ut>
<ud>km</ud>
<us>km/h</us>
<up>mb</up>
<ur>mm</ur>
</head>
&#8722;
<loc id="NLXX0002">
<dnam>Amsterdam, Netherlands</dnam>
<tm>3:12 PM</tm>
<lat>52.35</lat>
<lon>4.90</lon>
<sunr>5:58 AM</sunr>
<suns>9:35 PM</suns>
<zone>2</zone>
</loc>
&#8722;
<cc>
<lsup>7/30/08 2:55 PM Local Time</lsup>
<obst>Amsterdam, Netherlands</obst>
<tmp>26</tmp>
<flik>27</flik>
<t>Partly Cloudy</t>
<icon>30</icon>
&#8722;
<bar>
<r>1019.0</r>
<d>steady</d>
</bar>
&#8722;
<wind>
<s>13</s>
<gust>N/A</gust>
<d>90</d>
<t>E</t>
</wind>
<hmid>57</hmid>
<vis>10.0</vis>
&#8722;
<uv>
<i>5</i>
<t>Moderate</t>
</uv>
<dewp>17</dewp>
&#8722;
<moon>
<icon>27</icon>
<t>Waning Crescent</t>
</moon>
</cc>
</weather>

But, I don't know how to put this code inside .xslt

---

### Post by halitech on 2008-07-30
I guess its not the xslt file that you need to modify, just looked at mine

can you post the line that you are using in conky to give you the weather

---

### Post by tamoneya on 2008-07-30
can we see your conky main.

---

### Post by Kevbert on 2008-07-30
Have you registered on the Weather channel website, so that you have a user ID and password ?

---

### Post by wariskampar on 2008-07-30
Here is my conkymain. Btw, I do not use phyton script so I don't think I need to register. But maybe I'm wrong. 

> # .conkyrc

# set to yes if you want Conky to be forked in the background
#background yes

update_interval 1.0

double_buffer yes
own_window yes
own_window_transparent yes

# If own_window is yes, you may use type normal, desktop or override
#own_window_type normal

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

use_xft yes
xftfont Sans:size=8
#xftfont Trebuchet MS:size=10

# Text alpha when using Xft
xftalpha 0.9

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
#total_run_times 0

maximum_width 205
default_color white
#alignment top_right
alignment bottom_right

uppercase no

TEXT
${color #ffcb48}$alignc$nodename 
$alignc$sysname $kernel on $machine

${execi 9000 cat /proc/cpuinfo | grep "model name" | sed -e 's/model name.*: //'}

${color lightgrey}Uptime:$color $uptime $alignr${color lightgrey}Load:$color $loadavg
${color lightgrey}CPU: $color ${freq} Mhz ${alignr}${color lightgrey} Usage:$color $cpu% 
${color lightgrey}Processes: $color $processes ${alignr}${color lightgrey}Current: $color $running_processes 
${color black}${cpugraph 000000 5000a0}

${color lightgrey}RAM:$color $mem/$memmax - $memperc% ${alignr}${membar 7,30}$color
${color lightgrey}Swap:$color $swap/$swapmax -  $swapperc% ${alignr}${swapbar 7,30}$color

${color #ffcb48}Processes ${hr 1}
${color lightgrey}Name - ${goto 110}PID${goto 138}CPU%${goto 175}MEM%
${color #999999}${top name 1} ${goto 102}${top pid 1}${goto 135}${top cpu 1}${goto 172}${top mem 1}
${color #999999}${top name 2} ${goto 102}${top pid 2}${goto 135}${top cpu 2}${goto 172}${top mem 2}
${color #999999}${top name 3} ${goto 102}${top pid 3}${goto 135}${top cpu 3}${goto 172}${top mem 3}
${color #999999}${top name 4} ${goto 102}${top pid 4}${goto 135}${top cpu 4}${goto 172}${top mem 4}
${color #999999}${top name 5} ${goto 102}${top pid 5}${goto 135}${top cpu 5}${goto 172}${top mem 5}
${color lightgrey}Memory -
${color #999999}${top_mem name 1} ${goto 102}${top_mem pid 1}${goto 135}${top_mem cpu 1}${goto 172}${top_mem mem 1}
${color #999999}${top_mem name 2} ${goto 102}${top_mem pid 2}${goto 135}${top_mem cpu 2}${goto 172}${top_mem mem 2}
${color #999999}${top_mem name 3} ${goto 102}${top_mem pid 3}${goto 135}${top_mem cpu 3}${goto 172}${top_mem mem 3}
${color #999999}${top_mem name 4} ${goto 102}${top_mem pid 4}${goto 135}${top_mem cpu 4}${goto 172}${top_mem mem 4}
${color #999999}${top_mem name 5} ${goto 102}${top_mem pid 5}${goto 135}${top_mem cpu 5}${goto 172}${top_mem mem 5}

${color #ffcb48}System Storage ${hr 1}
${color grey}Root:     $color${fs_used /} / ${fs_size /} ${alignr}${fs_bar 7,50 /}$color
${color grey}Home:$color${fs_used /home} / ${fs_size /home} ${alignr}${fs_bar 7,50 /home}$color
${color grey}19.7GB:$color${fs_used /media/sda4} / ${fs_size /media/sda4} ${alignr}${fs_bar 7,50 /media/sda4}$color

${color #ffcb48}Ethernet ${hr 1}
${color lightgrey}IP address: $alignr$color${addr eth0}
${color black}${downspeedgraph eth0 23,98 ff0000 0000ff} ${alignr}${color black}${upspeedgraph eth0 23,98 0000ff ff0000}
${voffset -24}${color #f8f8ff}     D/Load: ${color white}${downspeed eth0}k/s              ${color #f8f8ff}Upload: ${color white}${upspeed eth0}k/s ${voffset 15}
${color red}    Total: $color${totaldown eth0} ${color green}       Total: $color${totalup eth0}
${color lightgrey}       Inbound: ${color white}${tcp_portmon 1 32767 count}               ${color lightgrey}Outbound: ${color white}${tcp_portmon 32768 61000 count}

${color #ffcb48}Wi-Fi ${hr 1}
${color lightgrey}Wireless signal: $color${wireless_link_qual ath0}%
${color lightgrey}IP address: $color${addr ath0}
${color lightgrey}Download speed: $color${downspeedf wifi0} Kb/sec

${color #ffcb48}Weather ${hr 1}
${color white}${execi 60 ~/scripts/weather.sh NLXX0002}$color

---

### Post by halitech on 2008-07-30
looks basically about the same as mine
```

${color #e9c703}Local Weather:
$color${execi 1800 /home/daryl/applications/weather/weather.sh CAXX0183}

```

except I put the complete path to where I have my weather.sh file and I have 1800 instead of 60

I wonder if you put the complete path in if that will work?

---

### Post by wariskampar on 2008-07-30
According to Bruce (the man behind the code I use), the code no longer works. He recommend me to use the new Pyhton script which I did and my problem was solved once for all! Now, I'm just curious about using conkyForecast template which was attached in the tutorial. Anyway, that is a different question and I will try to figure it out myself. If I stuck, I'll post new thread. Thanks to all

---

### Post by halitech on 2008-07-30
glad you got it working :) please mark this thread solved so others will know

---

