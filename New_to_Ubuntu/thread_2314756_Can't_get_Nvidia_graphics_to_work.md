---
title: "Can't get Nvidia graphics to work"
date: 2016-02-23
forum: New to Ubuntu
---

### Post by jack169 on 2016-02-23
I have a laptop with an Nvidia GeForce 8400m GT. As of now, all of the windows lag when I drag them or scroll. The desktop resolution also doesn't match the display's. I went to "Additional Drivers" and installed the 340.96 binary, then rebooted, but everything stays the same. If I go the X Server Settings, it doesn't show any kind of display or graphics options. It just has one tab with a few other options like "Display Status Bar". I've tried to manually download a driver from the Nvidia website and and install that, but it gives me 
The kernel header file
        ```
 '/lib/modules/4.2.0-30-generic/build/include/linux/version.h' does
         not exist.  The most likely reason for this is that the kernel source files in '/lib/modules/4.2.0-30-generic/build' have not been
         configured.
```
Can anyone help me? I just want to get the drivers up and running so that the resolution is correct and the windows don't lag.

---

### Post by Geoffrey_Arndt on 2016-02-24
Am not an expert on closed source nVidia drivers (I use all Intel PC's) . . . but, if I had an nVidia or AMD machine I'd consider two changes if having chronic problems with standard "additional drivers" method:

1).   Switch to Xubuntu which may not require use of any proprietary video drivers, and/or,
2).   Use the xorg-edgers PPA (but first purge ALL nVidia drivers you installed before)

Good Luck!

---

### Post by SeijiSensei on 2016-02-24
Do not try installing drivers from NVIDIA's site.  That's just going to cause you pain.

You don't tell us what Ubuntu version you're using, but it's probably not 14.04LTS since you seem to have a 4.x kernel. 

With an 8400 card, you might want to use the older 304 driver which you can install with
```
sudo apt-get install nvidia-304
```
That driver is available for 14.04LTS; I don't know if it is still available in later Ubuntu versions.

You can see the array of drivers available to you with the command:
```
apt-cache search nvidia | grep 'binary driver'
```
For 14.04, I see the ancient 173 version, and 304, 331, 340, and 346:
```

$ apt-cache search nvidia | grep 'binary driver'
nvidia-173 - NVIDIA legacy binary driver - version 173.14.39
nvidia-304 - NVIDIA legacy binary driver - version 304.128
nvidia-304-updates - NVIDIA legacy binary driver - version 304.128
nvidia-340 - NVIDIA binary driver - version 340.93
nvidia-340-updates - NVIDIA binary driver - version 340.93
nvidia-346 - NVIDIA binary driver - version 346.96
nvidia-346-updates - NVIDIA binary driver - version 346.96

```

You will also see the "NVIDIA X Server Settings" application installed which you should use to select resolutions.

---

### Post by NikTh on 2016-02-24
I agree with **SeijiSensei**, 
but first would be better to completely uninstall any kind of Nvidia binary you have installed until now. 

```

sudo apt-get remove --purge nvidia-*
sudo rm /etc/X11/xorg.conf

```

Then follow instructions in above **SeijiSensei's** post and install the 304 driver. Also don't forget after a successful installation to run the command 

```
sudo nvidia-xconfig
```
then reboot your PC.

Regards

---

