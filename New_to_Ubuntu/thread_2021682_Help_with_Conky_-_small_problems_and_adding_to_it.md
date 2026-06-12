---
title: "Help with Conky - small problems and adding to it"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by jozi on 2012-07-09
I followed the tutorial as posted [here]("http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/#idc-cover") but I'm having some problems that I can't figure out or solve from the comments.

First of all I can't get the weather to work at all, I've tried renaming folders and changing the path but nothing worked.

Another problem I have is the width of the side bar seems excessive, the cpu usage bars and email cool be a bit shorter, I can't figure out how though. The width of the time/date to me looks like it would be plenty for the whole thing.

Lastly, how can I add more things to it like cpu temp, fan speed etc? Can it display music playing in a scrolling bar?

Here's my conky script:
```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 4D6844
update_interval 5.0


TEXT
 ${color D3DADF}${font OpenLogos:size=45} u t
 ${font weather:size=82}${color C9CFD4}${execi 600 /home/jozi/.scripts/conditions.sh}${color 265276}${font} ${voffset -25}  ${execi 1200 /home/jozi/.scripts/pogodynka.sh}

   ${color 4EA9F3}${font weather:size=28}x ${font}HDD ${execi 1 ~/.scripts/hddmonit.sh}°C 
    
   ${color}${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}
   ${font StyleBats:size=16}A${font}  CPU2: ${cpu cpu2}% ${cpubar cpu2}


   ${font FreeSans:size=16}@${font}${execpi 300 python ~/.scripts/gmail_parser.py bren.jozi@gmail.com pashley2 3}

   ${color 014A7F}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


   ${color 014A7F}${font Radio Space:size=14}${time %A, %d-%m-%Y}
      ${font Radio Space:size=55}${time %H:%M}



```

I'm getting a error which I dont understand when ran from terminal (nothing about the weather though)
```
jozi@Jozi:~$ conky
Conky: /home/jozi/.conkyrc: 14: no such configuration: 'border_margin'
Conky: desktop window (1400095) is subwindow of root window (15a)
Conky: window type - override
Conky: drawing to created window (0x3a00001)
Conky: drawing to double buffer

```

---

### Post by Kopkins on 2012-07-09
The only thing I can think is that you need to set the permissions for your scripts to make them executable.

```

sudo chmod +x /path/to/executable/file.sh

```You can add cpu temp with lm-sensors. 

```

sudo apt-get install lm-sensors

#Now detect the sensors that your computer has. 
sudo sensors-detect

# now you can get cpu temp with the command:
sensors

#you may need to do 
sudo modprobe coretemp
#before sensors will work. 

```You can use this in conky in addition to 'cut' and 'grep' to get the cpu temp. 
```

sensors | grep Core | cut -c18-21
# 67.0
# 66.0

```In conky 
```
Core 1 (${execi 6 sensors | grep 'Core 0' | cut -c18-21} C)
#Core 1 (64.0 C)

Core 2 (${execi 6 sensors | grep 'Core 1' | cut -c18-21} C)
#Core 2 (65.0 C)

```Hope this helps,
Kopkins

---

### Post by jozi on 2012-07-09
> **Kopkins said:**
> The only thing I can think is that you need to set the permissions for your scripts to make them executable.


That worked a treat! Thanks! I now have 2 icons, one of which is kinda weird but I'll look into it and the other stuff from your post tomorrow.

Thanks

---

### Post by jozi on 2012-07-15
Not really been at the pc much the last few days, I'm still having Conky problems. It won't run at all for me :(

I have the following set to run at start-up

conky-startup.sh
```
#!/bin/bash
sleep 15 && conky ;
```

Which to my knowledge means it should run 15sec after start-up, however nothing happens :(

When I type "conky" into terminal it runs as before in my op. Any idea's? Any way to see what happens at start-up to see if there's a fault logged?

---

### Post by Kopkins on 2012-07-15
Can you run the script from the terminal? 
```
/path/to/conky-startup.sh
```

Kopkins

---

### Post by jmfal on 2012-07-15
You might have to change conky to .conkyrc in startup script.

---

### Post by HeroOfCanton on 2012-07-15
Try
```

#!/bin/bash
sleep 15 && conky -d;
exit 0

```or

```

#!/bin/bash
sleep 15 && conky -d -c ~/.conkyPath/.conkyScript;
exit 0

```Obviously change the path and script name on the last one. Also, 15 seconds seems like an awful lot. Normally 5-8 seconds is plenty.

---

### Post by NikTh on 2012-07-16
> **jozi said:**
> Not really been at the pc much the last few days, I'm still having Conky problems. It won't run at all for me :(

I have the following set to run at start-up

conky-startup.sh
```
#!/bin/bash
sleep 15 && conky ;
```Which to my knowledge means it should run 15sec after start-up, however nothing happens :(

When I type "conky" into terminal it runs as before in my op. Any idea's? Any way to see what happens at start-up to see if there's a fault logged?
Hi ,
This is my conky.sh with  delay of 10secs .. 
```
#!/bin/sh
sleep 10
conky
exit 0
```i added the script to startup applications with full path.. /home/username/conky.sh 
hope this help.

Also run the script from terminal and see any weird output.. ```
./conky-startup.sh
```
Thanks

---

### Post by jozi on 2012-07-16
> **Kopkins said:**
> Can you run the script from the terminal? 
```
/path/to/conky-startup.sh
```

Kopkins

The problem lay within the script as it didn't run.

> **HeroOfCanton said:**
> Try
```

#!/bin/bash
sleep 15 && conky -d;
exit 0

```or


This worked for me! I even have the weather part working (albeit not properly).

Thanks guys! Now to start configuring Conky to display lots of things :D

---

### Post by jozi on 2012-07-16
Just spotted my time in Conky is different to the time in my top bar :P

---

### Post by HeroOfCanton on 2012-07-16
> **jozi said:**
> This worked for me! I even have the weather part working (albeit not properly).

Thanks guys! Now to start configuring Conky to display lots of things :D

Great! Love it when things actually work out. :) Don't forget to mark the thread solved...

---

### Post by jozi on 2012-07-16
> **HeroOfCanton said:**
> Great! Love it when things actually work out. :) Don't forget to mark the thread solved...

Oops! Didn't know about that :oops:

---

