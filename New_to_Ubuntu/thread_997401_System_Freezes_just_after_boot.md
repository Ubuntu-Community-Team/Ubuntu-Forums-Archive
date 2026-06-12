---
title: "System Freezes just after boot"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by skymera on 2008-11-29
Hello!

I've just installed Ubuntu on my laptop. It has always been problematic on Ubuntu due to drivers for the graphics.

Anyway the problem. When i boot it's fine, but the system freezes shortly after the brown screen appears. I can't get to login without it freezing. I have to do a hard reboot.

Now, how do i manually change the display driver in Ubuntu 8.10 from the command line? I understand Xorg.conf is different, not sure if the driver info is still there.

Question two, i have wireless and it's supported out the box. I need to configure it from the terminal which unfortunately i forgotten how to do :(. 
I need to connect to a specific SSID using WPA-TKIP encryption. How may i go about doing this? 

When connected i can download openchrome driver and hopefully change the driver manually with the information you guys can hopefully supply.

Few more details
- Ubuntu 8.10 32bit
- VIA Unichrome Pro graphics chip (it sucks, uses OpenChrome driver)

Many thanks all. :guitar:

---

### Post by quirks on 2008-11-29
> Now, how do i manually change the display driver in Ubuntu 8.10 from the command line? I understand Xorg.conf is different, not sure if the driver info is still there.

Reboot. When GRUB counts down from three to zero, press ESC. From the boot menu, choose the upper most recovery mode. After the system has booted into text mode, it should give you an option to reconfigure your Xorg server. When asked for a driver, enter vesa.

> - VIA Unichrome Pro graphics chip (it sucks, uses OpenChrome driver)

You might want to buy a NVIDIA graphics card on eBay. You may even pick one of the older ones (e.g., Geforce4). They have become really cheap these days, and still they out-perform a crappy VIA graphics card easily.

---

### Post by skymera on 2008-11-29
> **quirks said:**
> Reboot. When GRUB counts down from three to zero, press ESC. From the boot menu, choose the upper most recovery mode. After the system has booted into text mode, it should give you an option to reconfigure your Xorg server. When asked for a driver, enter vesa.

You might want to buy a NVIDIA graphics card on eBay. You may even pick one of the older ones (e.g., Geforce4). They have become really cheap these days, and still they out-perform a crappy VIA graphics card easily.


1. It doesn't ask for a driver. 

2. This is a laptop, so i'm stuck :(

---

### Post by skymera on 2008-11-30
The resolution is booting at 1600x1200.

But my laptop is only 1024x768.
How do i boot and keep the res at 1024x768. I tried vga=792 but that only fixed the console text.

---

### Post by alienexplorers on 2008-11-30
Have you tried booting into recovery mode and at the menu selecting xfix.  Run that and then select resume normal boot.

---

### Post by linux_tech on 2008-11-30
xandr is a command that will change screen size

from- man xrandr
xrandr [-help]  [-display display] [-o orientation] [-q] [-v] [-s size]

ie
xrandr --output LVDS --mode 1024x768

```
xrandr -s 1024x768 
``` or whatever resolution

Resolution can also be set in xorg.conf
note: If you are going to edit xorg, always backup your configuration file 1st:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
more on xrandr here- [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

HOWTO: change resolution/refresh rate in Xorg
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by skymera on 2008-11-30
> **alienexplorers said:**
> Have you tried booting into recovery mode and at the menu selecting xfix.  Run that and then select resume normal boot.

Tried earlier, didn't work.

@ linux_tech - I can get it to boot on Vesa driver (OpenChrome crashes, i think it's because it boots at 1600x1200 which my laptop can't do).
Anyway Vesa works and i can try xrandr now, thanks.

i'll post update

---

### Post by skymera on 2008-11-30
I'm afraid that didn't help.

In hardy i used displayconfig-gtk which is now GONE? WTF.

I've used Ubuntu for 2 years and can't even set the resolution up, how is a new user suppose to do this!? User friendly? My ***

---

### Post by skymera on 2008-11-30
oh look. MAGIC. XP works.

Even Microsoft gets it right.

This is seriously frustrating, how do i get a simple res change?

---

