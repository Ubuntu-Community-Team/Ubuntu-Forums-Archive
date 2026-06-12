---
title: "Can't set resolution any higher than 1024x768. 12.04"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by PetCat on 2013-04-23
Hello! :KS

I recently installed ubuntu for the first time. 
When i go to "displays" i cant set my resolution higher than 1024x768. 
GPU: gforce gtx 680
Monitor: benQ xl2420t   (supports 1920x1080 @ 120 hz)
ubuntu 12.04

I have tried using xrander, but as you can se below i get an error using xrandr --addmode:

$ cvt 1920 1080 120
# 1920x1080 119.93 Hz (CVT) hsync: 139.12 kHz; pclk: 369.50 MHz
Modeline "1920x1080_120.00"  369.50  1920 2080 2288 2656  1080 1083 1088 1160 -hsync +vsync

$ xrandr --newmode "1920x1080_120.00"  369.50  1920 2080 2288 2656  1080 1083 1088 1160 -hsync +vsync

$ xrandr --addmode DVI-I-1 1920x1080_120.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  39
  Current serial number in output stream:  40

Does anyone know how i can get 1920x1080?

---

### Post by zero2xiii on 2013-04-23
Hay,

I suggest you install the proprietary drivers.

Go to the dash > type in "Additional Drivers" > Open tool called "Additional Drivers" > Select the "recommended drivers" and install them.

Restart and you should have the nVidia drivers loaded on boot and have access to higher resolutions.

You change resolution now with the "nvidia xserver settings" tool.

Cheers

---

### Post by PetCat on 2013-04-23
Thanks but I dont have that option in my additional drivers. It looks like this:
[IMG]http://i34.tinypic.com/2en0npd.jpg[/IMG]

I do have Nvidia x server settings on my system. But it only allows me to set 1024x768 or lower.

---

### Post by zero2xiii on 2013-04-23
Hay,

I assume it is manually installed then.

No matter. Please open up a terminal (ctrl + alt + T) and do the following:
```
sudo nvidia-xconfig
```

Then log out and log back in or reboot.

Can you please post the output of the following after the above between [CODE ] [/CODE ] tags. (the # sign at the top of the post edit view).

```
 cat /etc/X11/xorg.conf
xrandr

```

Also are you using VGA or DVI to connect your monitor?

Cheers

---

### Post by PetCat on 2013-04-23
using DVI

```

   calle@KAZE:~$ sudo nvidia-xconfig  
 [sudo] password for calle:  
 

 Using X configuration file: "/etc/X11/xorg.conf".  
 

 VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.  
                   Device section "Default Device" must have a Driver line.  
 

 Backed up file '/etc/X11/xorg.conf' as  
 '/etc/X11/xorg.conf.nvidia-xconfig-original' 
 Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'  
 New X configuration file written to '/etc/X11/xorg.conf'  

```

Then i relogged and typed.

   ```


calle@KAZE:~$ cat /etc/x11/xorg.conf 
 cat: /etc/x11/xorg.conf: No such file or directory 
 calle@KAZE:~$ xrandr 
 Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384 
 DVI-I-0 disconnected (normal left inverted right x axis y axis) 
 DVI-I-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm 
    1920x1080      60.0*+  120.0     99.9   
    1440x900      119.9   
    1280x1024     120.0     75.0     60.0   
    1024x768      120.0     75.0     60.0   
    800x600       120.0     75.0     60.3   
    640x480       120.0     75.0     59.9   
 HDMI-0 disconnected (normal left inverted right x axis y axis) 
 DP-0 disconnected (normal left inverted right x axis y axis) 
 DVI-D-0 disconnected (normal left inverted right x axis y axis) 
 DP-1 disconnected (normal left inverted right x axis y axis) 


```

So i have 1080p now!
Thx alot for the help! =D

---

### Post by PetCat on 2013-04-23
Btw, how do i mar the thread as solved? X)

---

### Post by zero2xiii on 2013-04-23
Hay,

Glad I could help :)

You need to advance edit the very first post and manualy change the "prefix" this is a bug on the website and they are aware of it lol.

Just FYI, the above output states the driver was installed but not being used (nvidia) just so you know the cause as well :)

Cheers

---

### Post by SifGrey on 2013-04-23
This way: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Edit: I think I posted this at the exact same time you did, zero2xiii. :)

---

### Post by PetCat on 2013-04-23
Allright, thanks for all the help (:

---

### Post by zero2xiii on 2013-04-24
> **SifGrey said:**
> This way: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Edit: I think I posted this at the exact same time you did, zero2xiii. :)

Lolz no worries,

I could have been wrong, more sources of information is always welcome :)

Cheers

---

