---
title: "weather forecast in conky"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-06-25
```
background yes
font Zekton:size=8
xftfont Zekton:size=8
use_xft yes
xftalpha 0.1
update_interval 0.6
total_run_times 0
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
own_window_transparent yes


double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 256 5
maximum_width 300
default_color 000000
default_shade_color black
default_outline_color black
alignment top_right
gap_x 2
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Zekton:style=Bold:pixelsize=24}${alignc}${time %l:%M:%S %p}${font Zekton:size=8}
SYSTEM ${hr 1 }

CPU       ${alignc} ${freq_dyn}MHz / ${acpitempf}F ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Processes: ${alignr}$processes ($running_processes running)

Highest CPU $alignr CPU%       MEM%
${top name 1}$alignr${top cpu 1}         ${top mem 1}
${top name 2}$alignr${top cpu 2}         ${top mem 2}
${top name 3}$alignr${top cpu 3}         ${top mem 3}

Load: ${alignr}$loadavg

FILESYSTEM ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}
Storage: ${alignr}${fs_free /media/disk} / ${fs_size /media/disk}
${fs_bar 4 /media/disk}

NETWORK ${hr 1}${color}

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 24,128} ${alignr}${upspeedgraph wlan0 24,128}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}

CURRENT CONDITIONS ${hr 1}${color}

${execi 3600 perl ~/scripts/weather.pl 60123 f 1w}
${execi 3600 perl ~/scripts/weather.pl 60123 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl 60123 f t}
${voffset -15}$alignr${offset -60}${font weather:size=32}${execi 3600 perl ~/scripts/weather.pl 60123 f cp}$font
5 DAY FORECAST ${hr 1}${color}

${font weather:size=55}${execi 3600 perl ~/scripts/weather.pl 60123 f 5dp}${font}$color
${voffset -70}${execi 3600 perl ~/scripts/weather.pl 60123 f 5dt}

```

im trying to modify the weather forecast so that it shows for my area. anyone got any ideas?

---

### Post by Inxsible on 2008-06-25
I see that you are using the weather.pl script. and I think you are entering your zipcode as input.

That script does not take the zip code, but a different code that weather.com uses. Go to weather.com and then type in your city and state name. Do not use the zipcode to get weather, or you will not get that code.

if 60123 is your city code then the weather.com code for you is USIL0360.

When I type in elgin, IL, I get 2, elgin and south elgin. I gave you the code for Elgin. If you want south elgin, type in south elgin, IL in the weather.com page and then get the code from 'USILxxxx'

Replace all the '60123' with 'USIL0360' in your conkyrc file. Save and restart conky

Hope that helps !

---

### Post by Doorslammer on 2008-06-25
my 5 day stopped working few months ago 
so not sure if your is going to work  as it's the same thing I'm using  
my current conditions  work  but not the 5 day

---

### Post by PatrickMoore on 2008-08-02
> **Inxsible said:**
> I see that you are using the weather.pl script. and I think you are entering your zipcode as input.

That script does not take the zip code, but a different code that weather.com uses. Go to weather.com and then type in your city and state name. Do not use the zipcode to get weather, or you will not get that code.

if 60123 is your city code then the weather.com code for you is USIL0360.

When I type in elgin, IL, I get 2, elgin and south elgin. I gave you the code for Elgin. If you want south elgin, type in south elgin, IL in the weather.com page and then get the code from 'USILxxxx'

Replace all the '60123' with 'USIL0360' in your conkyrc file. Save and restart conkys

Hope that helps !

i have it with the city code and it still does not want to show up. my conky can see my weather.pl script but still doesnt  show anything. can anyone help me resolve this

---

### Post by wardrich on 2008-11-20
I've seen this "weather.pl" file referenced all over the place, but I can't find it anywhere...  Can somebody point me in the right direction pleeaaaase?

---

