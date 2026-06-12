---
title: "Compaq CQ40-328TU --- Monitor Brightness"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by czgirb on 2012-10-07
Dear all.
I'm a newbie to Ubuntu. Currently I used 12.04 on my Compaq CQ40 lappie.
Everything is work out of the box. Internet, WiFi, Bluetooth, and etc.
and I able to comfirmed that ubuntu is a good OS and I like it ... love it.
But one thing that I faced is ... in every re-boot, my Monitor Brightness is always in default setting. No matter what setting that I used. Even the lowest/lesser setting.
Is there a clue?
Please guide me ...

---

### Post by bart.a on 2012-10-17
Have you set the brightness in the System Settings > Hardware > Power Management?

I don't know if there are power saving settings regarding your screen in the BIOS of your machine, but ther might be.. please check..

---

### Post by bart.a on 2012-10-20
I found something on the net that may suit your needs..
Check [this]("http://www.noobslab.com/2012/05/some-more-tweaks-for-ubuntu-1204.html") out..

2: Save Screen Brightness of Laptop in Ubuntu
Ubuntu doesn't save screen brightness due to hardware compatibility, At every login you have to change brightness. So here is tweak to save screen brightness in Ubuntu.

To Save Screen Brightness in Ubuntu open Terminal (Press Ctrl+Alt+T) and copy the following commands in the Terminal:

```
sudo gedit /etc/rc.local
```

Add this before the last line "exit 0":

```
echo 4 > /sys/class/backlight/acpi_video0/brightness
```

---

