---
title: "Invisible Conky (calendar)"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by wariskampar on 2008-08-05
I want to display a conky calendar on my desktop along with my main conky. However, when I test run the code, that conky do not appear. System Monitor however indicates that it is running. I run the conky using this code:
```
conky -c ~/Desktop/conkyCal
``` 

This is my full code:
```
#background yes
#font Snap.se:size=8
#xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 5.0
total_run_times 0
#own_window yes
#own_window_type override
#own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 206 5
maximum_width 206
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment middle_right
#gap_x 6
#gap_y 30
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer none
color0 FFFFFF
color1 AFAFFF
text_buffer_size 256


TEXT
${font Aerial:style=Bold:pixelsize=14}${execi 60 date +"%B %Y" | tr "[:lower:]" "[:upper:]"}${font Snap.se:size=8} ${hr 1 }

${font Bitstream Vera Sans Mono:style=Bold:size=13}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color1}'"$DJS"'${color0}'" "/}
```

I just copy this code from this forum so if the owner happen to come across this this post, I would like to say thank you and hopefully you do not mind:)

---

### Post by PurposeOfReason on 2008-08-05
Are you sure it is not overlapping your current conky?

---

### Post by wariskampar on 2008-08-05
for current conky;
alignment top_right

for conkyCal;
alignment middle_right

---

### Post by PurposeOfReason on 2008-08-05
> **wariskampar said:**
> for current conky;
alignment top_right

for conkyCal;
alignment middle_right
Can you post your normal conky then?

---

### Post by wariskampar on 2008-08-05
```
# set to yes if you want Conky to be forked in the background
background true

# Create own window
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering
double_buffer yes

use_spacer yes

# Text stuff
use_xft yes
xftfont Liberation Sans:size=8
xftalpha 0.9
text_buffer_size 1024
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
draw_graph_borders no

# Update interval in seconds
update_interval 1.0

# Draw shades?
draw_shades no

maximum_width 205
default_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap size
#gap_x 10
gap_y 30
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

${color grey}Root:     $color${fs_used /} / ${fs_size /} ${alignr}${fs_bar 7,50 /}$color
${color grey}Home: $color${fs_used /home} / ${fs_size /home} ${alignr}${fs_bar 7,50 /home}$color
${color grey}19.7GB: $color${fs_used /media/sda4} / ${fs_size /media/sda4} ${alignr}${fs_bar 7,50 /media/sda4}$color

${color lightgrey}Ethernet: $alignr$color${addr eth0}
${color black}${downspeedgraph eth0 23,98 ff0000 0000ff} ${alignr}${color black}${upspeedgraph eth0 23,98 0000ff ff0000}
${voffset -24}${color #f8f8ff}     D/Load: ${color white}${downspeed eth0}k/s              ${color #f8f8ff}Upload: ${color white}${upspeed eth0}k/s ${voffset 15}
${color red}    Total: $color${totaldown eth0} ${color green}       Total: $color${totalup eth0}
${color lightgrey}       Inbound: ${color white}${tcp_portmon 1 32767 count}               ${color lightgrey}Outbound: ${color white}${tcp_portmon 32768 61000 count}

${color lightgrey}Wi-Fi signal: $color${wireless_link_qual ath0}% $alignr$color${addr ath0}
${color lightgrey}D/load speed: $color${downspeedf wifi0} Kb/sec

${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=CN --refetch}
Day: ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=DW}
Conditions: ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=CC}
Temp: ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=HT}
Wind: ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=WS}
Wind Direction: ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=WD}$alignr${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=HT}/${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=LT}
Humidity: ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=HM}
Sun Rise: ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=SR} Sunset: ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=SS}
${alignr}${voffset -80}${offset -50}${font Weather:size=48}${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0002 --datatype=WF}${font}

${execi 1800 python /home/aznan/.scripts/conkyForecast.py --location=NLXX0002 --template=/home/aznan/.scripts/conkyForecast.template --refetch}
   ${voffset -90}${font Weather:size=40}${execi 3600 python /home/aznan/.scripts/conkyForecast.py --location=NLXX0002 --datatype=WF --startday=1 --endday=3 --spaces=5 --refetch}${font}
```

---

### Post by PurposeOfReason on 2008-08-05
I just tried it. Your first conky is too long and covers up the one you have middle aligned.

---

### Post by wariskampar on 2008-08-05
What should I do then?

I intend to display 2 conky on my desktop; conkyrc and conkyCal. I will alter my conky_start later on to include both setting.

---

### Post by PurposeOfReason on 2008-08-05
You could either shorten the first conky or put conky cal in the bottom right or left side of the screen.

---

