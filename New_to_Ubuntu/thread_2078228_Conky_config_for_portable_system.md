---
title: "Conky config for portable system"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by bgalfond on 2012-10-30
I have conky running beautifully on my persistent USB with 12.04 Ubuntu.  It uses **[conky colors]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328")** and the cairo theme.

What I would like to do is have it run on other computers when I move the USB.  The problem I am having is that my normal desktop where it works is quad-core, while my secondary computer is single core.  I edited the conkyrc like so:

```
# |--CPU
${if_existing /sys/devices/system/cpu/cpu0}
${goto 100}${font Ubuntu:style=Bold:size=8}${color2}${freq_g 1}${color} GHZ${font}
${goto 100}CPU1: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font}
${goto 100}Temp: ${font Ubuntu:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 0' | awk '{print $3}' | sed 's/+//' | sed 's/\.0//g'}${color}${font}
${voffset 15}
${endif}
${if_existing /sys/devices/system/cpu/cpu1}
${goto 100}${font Ubuntu:style=Bold:size=8}${color2}${freq_g 2}${color} GHZ${font}
${goto 100}CPU2: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font}
${goto 100}Temp: ${font Ubuntu:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 1' | awk '{print $3}' | sed 's/+//' | sed 's/\.0//g'}${color}${font}
${voffset 15}
${endif}
${if_existing /sys/devices/system/cpu/cpu2}
${goto 100}${font Ubuntu:style=Bold:size=8}${color2}${freq_g 3}${color} GHZ${font}
${goto 100}CPU3: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu3}%${color}${font}
${goto 100}Temp: ${font Ubuntu:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 2' | awk '{print $3}' | sed 's/+//' | sed 's/\.0//g'}${color}${font}
${voffset 15}
${endif}
${if_existing /sys/devices/system/cpu/cpu3}
${goto 100}${font Ubuntu:style=Bold:size=8}${color2}${freq_g 4}${color} GHZ${font}
${goto 100}CPU4: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu4}%${color}${font}
${goto 100}Temp: ${font Ubuntu:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 3' | awk '{print $3}' | sed 's/+//' | sed 's/\.0//g'}${color}${font}
${endif}

```

I still get an error message when I try to run it saying I am trying to use too many cores.  Any suggestions?

Thanks!

---

