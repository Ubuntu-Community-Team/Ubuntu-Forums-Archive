---
title: "[SOLVED] Problem: Installing xf86-video-intel and Mesa drm"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by suncoolsu on 2008-11-07
I have downloaded libdrm version 2.4.1 from the following site
[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

i wanted to install xf86-video-intel 2.5.0 videstting drivers (as my Dell Studio laptop is still running of VESA drivers as the Intell 965 GM chipset doesnt accpet anyother driver) also I wanted to install MESA drm. But I am unable to do so ..

So my first question 
- Is this package xf86-video-intel 2.5.0 available in the repository - so that I can simply apt-get

- I am compiling and installing the file myself
this is what I have been doing: 
 - ./configure (everything went fine without errors)
 - make -- gives some errors
```
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/baba/Desktop/xf86-video-intel-2.5.0/xf86-video-intel-2.5.0/src/tfp410'
make[4]: Entering directory `/home/baba/Desktop/xf86-video-intel-2.5.0/xf86-video-intel-2.5.0/src'
../doltcompile gcc -DHAVE_CONFIG_H -I. -I..   -I/usr/include/xorg -I/usr/include/pixman-1    -I/usr/local/include -I/usr/local/include/drm   -Wall -Wpointer-arith -Wstrict-prototypes 	-Wmissing-prototypes -Wmissing-declarations 	-Wnested-externs -fno-strict-aliasing -I/usr/include/xorg -I/usr/include/pixman-1   -I/usr/local/include -I/usr/local/include/drm   -I/usr/include/X11/dri -I../uxa -DI830_XV -DI830_USE_XAA -DI830_USE_EXA -g -O2 -MT i810_accel.lo -MD -MP -MF .deps/i810_accel.Tpo -c -o i810_accel.lo i810_accel.c
In file included from i810.h:63,
                 from i810_accel.c:55:
/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory
In file included from i810.h:63,
                 from i810_accel.c:55:
/usr/include/GL/glxint.h:95: error: expected specifier-qualifier-list before ‘GLboolean’
make[4]: *** [i810_accel.lo] Error 1
make[4]: Leaving directory `/home/baba/Desktop/xf86-video-intel-2.5.0/xf86-video-intel-2.5.0/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/baba/Desktop/xf86-video-intel-2.5.0/xf86-video-intel-2.5.0/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/baba/Desktop/xf86-video-intel-2.5.0/xf86-video-intel-2.5.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/baba/Desktop/xf86-video-intel-2.5.0/xf86-video-intel-2.5.0'
make: *** [all] Error 2


```


Can anyone help? I am trying to install the latest xf86-video-intel as the present display in my laptop reaches upto only 800x600 but its capabale of reaching 1280x800. 

Pls Pls help ....

Or if u think i did wrong can yu pls post the step by step procedure of isntalling this video settinng drivers.

thx

---

### Post by Peter09 on 2008-11-07
Before doing this see if you can get the default drivers working.

Configuring your Video Driver:
1. Check that there is no driver waiting to be enabled in System->Administration->Hardware Drivers
2. Boot into recovery mode and select xfix from the menu, this may resolve it. (Check 1. after doing this as well)

also post the output of the terminal code below so that we can see which driver is active.
```
lshw -C display
```

---

### Post by suncoolsu on 2008-11-07
Peter09,
My laptop is Dell Studio 1535 with Mobile 965GM chipset and X3100 VGA. If you dont happen to know, this is the laptop which is has a cursed Hardware which doesnt allow Linux Fans (ubuntu in particular) to enjoy the OS with its full graphical/visual appearance. Which means I end up with WSoD whenever I use Driver as "intel" - so I end up with a 800x600 resolution (on a system capable of 1280x800) and with the "vesa" driver.

Thanks for the response will upload the file asap.

You are very kind.

---

### Post by suncoolsu on 2008-11-08
following is my output for lshw -C display

```

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0


```

There are no drivers - apart from already in use in System-> Administration->HardwareDrivers. There is just one driver there which is for WiFi and thats in use. xfix didnt work sir :(

Please help 

Thx
B.

---

### Post by suncoolsu on 2008-11-08
If you want to have a look at my Xorg.0.log file - the pastebinit output is here (with driver as intel - screen ends up in WSoD)

```

http://pastebin.com/f7a736818

```


following is the Xorg.o.log with VESA as the driver which atleast gives me a 800x600 resolution output
```

http://pastebin.com/f15d0f08a

```

any help would be appreciated - I am dying to use ubuntu with full graphical/visual pleasure

thanks

---

### Post by cpminga on 2008-11-18
you need to install the gl.h header file referenced in your error output. I've been getting the white screen too, and tried the install last night. Unfortunately, it didn't help. Even when setting the install path to /usr. It could very well be that I did something wrong or left something out. Any advice would be greatly appreciated.

FYI, I installed libghc6-opengl-dev to get gl.h. May not have been the most direct approach as it installed several other packages, but it at least made make run without errors

---

