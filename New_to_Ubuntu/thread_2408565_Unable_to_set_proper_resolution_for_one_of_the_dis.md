---
title: "Unable to set proper resolution for one of the displays"
date: 2018-12-20
forum: New to Ubuntu
---

### Post by saleb on 2018-12-20
Yes, new to Ubuntu. I have switched yesterday without much preparation form an unexpectedly crushed windows 10. Nevermind.

The hardware is Asus ROG X370-F Gaming, Ryzen 7 1700, 16gb, 500gb ssd, Nvidia GTX 660, three displays (a 4k tv and 2x full hd displays).

I have run a Live 18.04 from a flash for a few hours, tried to get to know the environment and arrived at a problem that one of the displays did not go above 1024x768. I have found the solution which worked. 

```
cvt -r 1920 1080
xrandr --newmode "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync
xrandr --addmode DVI-I-0 1920x1080R
xrandr --output DVI-I-0 --mode 1920x1080R

```

When I chose to install the system the installation did not go smooth. First errored out saying that it cannot install grub, to restart find the image and init and boot manually. The second reinstall blocked during user/pass entering. Fifth went through without any problem. Nevermind this is also unimportant.

After installing and having the same problem the above code did not solve my problem. 

This is my xrandr output before applying the above code

```
Screen 0: minimum 8 x 8, current 7360 x 2160, maximum 16384 x 16384
DVI-I-0 connected primary 1600x900+3840+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1600x900      59.82* 
   1400x900      59.88  
   1368x768      59.88    59.85  
   1360x768      59.96    59.80  
   1280x800      59.91    59.81  
   1280x720      59.86    59.74  
   1152x864      60.00  
   1024x576      59.90    59.82  
   960x540       59.82    59.63  
   864x486       59.92    59.57  
   800x600       72.19    60.32    56.25  
   800x450       59.82  
   700x450       59.88  
   684x384       59.88    59.85  
   680x384       59.96    59.80  
   640x480       59.94  
   640x400       59.98    59.88  
   640x360       59.86    59.83  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.82    59.63  
   432x243       59.92    59.57  
   400x300       72.19  
   320x240       60.05  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 3840x2160+0+0 (normal left inverted right x axis y axis) 1872mm x 1053mm
   3840x2160     30.00*+  59.94    50.00    29.97    25.00    23.98  
   4096x2160     59.94    50.00    29.97    25.00    24.00    23.98  
   1920x1080     60.00    59.94    50.00    29.97    25.00    23.98    60.00    50.04  
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1366x768      59.79  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 connected 1920x1080+5440+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
DP-1 disconnected (normal left inverted right x axis y axis)

```

```
xrandr --addmode DVI-I-0 1920x1080R
``` returns:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  43
  Current serial number in output stream:  44

```

After that code xrandr is changed, but it changes DP-1 port and not the DVI-I-0:
```
Screen 0: minimum 8 x 8, current 7360 x 2160, maximum 16384 x 16384
DVI-I-0 connected primary 1600x900+3840+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1600x900      59.82* 
   1400x900      59.88  
   1368x768      59.88    59.85  
   1360x768      59.96    59.80  
   1280x800      59.91    59.81  
   1280x720      59.86    59.74  
   1152x864      60.00  
   1024x576      59.90    59.82  
   960x540       59.82    59.63  
   864x486       59.92    59.57  
   800x600       72.19    60.32    56.25  
   800x450       59.82  
   700x450       59.88  
   684x384       59.88    59.85  
   680x384       59.96    59.80  
   640x480       59.94  
   640x400       59.98    59.88  
   640x360       59.86    59.83  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.82    59.63  
   432x243       59.92    59.57  
   400x300       72.19  
   320x240       60.05  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 3840x2160+0+0 (normal left inverted right x axis y axis) 1872mm x 1053mm
   3840x2160     30.00*+  59.94    50.00    29.97    25.00    23.98  
   4096x2160     59.94    50.00    29.97    25.00    24.00    23.98  
   1920x1080     60.00    59.94    50.00    29.97    25.00    23.98    60.00    50.04  
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1366x768      59.79  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 connected 1920x1080+5440+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
DP-1 disconnected (normal left inverted right x axis y axis)
  1920x1080R (0x3c9) 138.500MHz +HSync -VSync
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock  66.59KHz
        v: height 1080 start 1083 end 1088 total 1111           clock  59.93Hz

```

I tried a few different names, they all ended in DP-1, after that I removed the trash with:
```
xrandr --rmmode 1920x1080R
```

I autoinstalled nVidiia driver nvidia-xconfig version 390.77, nothing changed. Nowhere could I find a solution. Neither could I find is it possible to manually change the file that xrandr is pointing to. So, the question is simple, what can I do (didn't imagine the first day using Linux like this :D )?

---

### Post by saleb on 2018-12-20
If there is any data that I could make available, log file, mindump, ... tell me where it is and how to access it and I will update the info. I have written everything for which I thought that it could be important

---

### Post by CatKiller on 2018-12-20
From your description, you didn't define the new mode before you tried to add it.

If you've installed the Nvidia drivers, there's a graphical settings application that might help.

Those are the two things I can think of for now.

---

### Post by saleb on 2018-12-20
Isn't the second row of the first code segment, the one beginning with xrandr --newmode the definition that you are referring to?

I have arrived a little further with the Nvidia X. I was able to change the ViewPortIn so it sends the 1920x1080 picture to a 1600x900 screen. It's a step in right direction, but still, I would like to be able to see the screens native resolution.

---

### Post by CatKiller on 2018-12-20
> **saleb said:**
> Isn't the second row of the first code segment, the one beginning with xrandr --newmode the definition that you are referring to?

Yes. You said that you did that and it worked in the live session. You don't say that you did it after you'd installed. Maybe you did it, and didn't say.

Sometimes a monitor will give a false EDID rather than none (which seems likely to be the case here, since you're defaulting to a resolution that isn't native and isn't 1024×768). I believe that the Nvidia driver by default will only validate a mode that's included in the EDID, whereas the open drivers are more trusting of the user. The Nvidia driver has an IgnoreEDID option that might help you overcome that. That goes in xorg.conf.

---

### Post by saleb on 2018-12-21
Thank you for trying to help. I have given up yesterday and now with a digital display, everything works as it should. Instead of finding a solution I have chosen to circumvent the problem

---

