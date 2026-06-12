---
title: "Problems with resolution on Lubuntu 13.04"
date: 2014-01-13
forum: New to Ubuntu
---

### Post by Thre365ive on 2014-01-13
So I just installed an update today after not using my laptop for a while, and now my aspect ratio is stuck at a 5:4. It's likely a resolution problem, but I can't find any options in the GUI to change it and I'm not very good with the terminal really. 

Anybody got any ideas on what to do? This is highly annoying, as my PC is my only entertaiment and I've got it on a 50" TV, but I can barely see anything from the couch.

---

### Post by papibe on 2014-01-13
Hi Thre365ive.

I'm afraid we're gonna need some basic command line stuff.

Could you open a terminal, run these commands and paste back its results?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'

xrandr -q 

xrandr -q --q1

ls /etc/X11/xorg.conf
```
Regards.

---

### Post by Thre365ive on 2014-01-13
Awesome, thanks!

It's not that I'm afraid of the terminal, I just don't know it well.

```
satan@PC:~$ lspci -nnk | grep -iA2 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6250] [1002:9804]
        Subsystem: Hewlett-Packard Company Device [103c:3577]
        Kernel driver in use: radeon
satan@PC:~$ 
satan@PC:~$ lsmod | grep -iE 'nvidia|fglrx|radeon|nouveau|i9'
radeon                875304  2 
ttm                    75385  1 radeon
drm_kms_helper         47545  1 radeon
drm                   228489  4 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
satan@PC:~$ 
satan@PC:~$ xrandr -q 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
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
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
satan@PC:~$ 
satan@PC:~$ xrandr -q --q1

 SZ:    Pixels          Physical       Refresh
 0   1366 x 768    ( 344mm x 194mm )   60  
 1   1280 x 720    ( 344mm x 194mm )   60  
 2   1152 x 768    ( 344mm x 194mm )   60  
*3   1024 x 768    ( 344mm x 194mm )  *60  
 4    800 x 600    ( 344mm x 194mm )   60  
 5    848 x 480    ( 344mm x 194mm )   60  
 6    720 x 480    ( 344mm x 194mm )   60  
 7    640 x 480    ( 344mm x 194mm )   59  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis
satan@PC:~$ 
satan@PC:~$ ls /etc/X11/xorg.conf
ls: cannot access /etc/X11/xorg.conf: No such file or directory
satan@PC:~$ 5~
```

There ya go! Thanks again!

---

### Post by papibe on 2014-01-13
Thanks.

Let's try setting the resolution using xrandr:
```
xrandr --output LVDS --mode 1280x720
```
If 1280x720 does not work, try 1366x768
```
xrandr --output LVDS --mode 1366x768
```
Let us know how it goes.
Regards.

---

### Post by Thre365ive on 2014-01-13
Nope. Neither worked.

If you don't mind, could you provide links to the commands you're giving me and what they do, or an explanation yourself?
 I appreciate the help and all, but I'd really like to actually learn this stuff so next time I don't have to ask.

---

### Post by papibe on 2014-01-13
Sure thing: start here: [Ubuntu Wiki Resolution]("https://wiki.ubuntu.com/X/Config/Resolution").

---

### Post by Thre365ive on 2014-01-13
Sweet! Thanks once more. 

I would appreciate a quick fix on this one if you know one though. My eyes suck and it's awful having to either sit ridiculously close to the computer or blow everything up so I can see.

---

### Post by Thre365ive on 2014-01-14
Bump. 

Can I get some quick help on this please? I promise I'll read up later once I don't have to sit 6" from the TV to see, lol.

---

### Post by papibe on 2014-01-14
After a second look, it looks like you have your TV connected using a VGA cable, isn't it?

It has became very common getting problems trying to get the proper resolutions for both digital monitors and HDTVs over VGA cable (analog)

Using the HDMI out through an HDMI cable, would give you more chances of getting the full TV resolution.

Could you paste the content of this file?```
/var/log/Xorg.0.log

```
here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and then post back the link.

Regards,

---

