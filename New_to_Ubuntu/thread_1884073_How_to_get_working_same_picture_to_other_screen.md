---
title: "How to get working same picture to other screen?"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by LolxD on 2011-11-20
Help, i got Ubuntu 11.10 and ATI HD 4250 with propieraty drivers. I have a laptop, and i want same picture like in original screen to my 23 inch screen, and if possible, the laptop's original screen should be shut down. But the problem is that, i need 1920x1080 resolution(my screen supports it) , and max is 1600x1200 in Ubuntu and i cant even use 1600x1200, i get a error. If i use "Show same picture in other screen" or whatever it is called in english, since i use finnish language, i get 1366x768 resolution. How i can get the same picture to this external screen but with 1920x1080 resolution?

---

### Post by SteveDee on 2011-11-20
> **LolxD said:**
> ...How i can get the same picture to this external screen but with 1920x1080 resolution?

With the 2nd screen plugged in, open a terminal and type:-
```

xrandr

```
The output should show you all display resolutions supported by each screen.

The laptop screen is represented by LVDS, so you can set like this:-
```

xrandr --output LVDS --mode 1280x1024

```

The other screen is probably "VGA" or "VGA-0" so set ths screen like this:-
```

xrandr --output VGA-0 --mode 1920x1080

```

---

### Post by LolxD on 2011-11-21
I tried xrandr --output VGA-0 --mode 1920x1080 but im getting "MODE NOT FOUND".
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9* 
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)

```
BTW, i forgot to say this is a new machine with currently with an Windows 7 install, and it detected maximum as 1600x1200 but with ATI CCC i was able to set that the real resolution was 1920x1080. Im not gonna install this to this machine before  i can get this resolution thing working on live system. (Funny fact: My old and new laptop has same graphics card =) )

---

### Post by LolxD on 2011-11-21
Okay, i found some instructions from internet and i got little better resolution
```
ubuntu@ubuntu:~$ xrandr --newmode "1920x1080_60.0"  106.29  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
ubuntu@ubuntu:~$ xrandr --addmode VGA-0 1920x1080_60.0
ubuntu@ubuntu:~$ xrandr --output VGA-0 --mode 1920x1080_60.0
ubuntu@ubuntu:~$ 

```
With this, i got 1600x900
Better, but not enough. So.. How to get this working?

---

### Post by LolxD on 2011-11-21
Nobody cant help?

---

