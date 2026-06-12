---
title: "Need help: install Xubuntu on CD/USB/network-LESS laptop"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by ooounohu on 2008-12-02
I have been diligently searching for several weeks now and have not pioneered anything in regards to my situation:

I have a laptop that has no network or USB booting capabilities.  The CD drive controller is near shot (just unreliable for bootable CDs).  The HDD has NO OS on it AT ALL.  I've come across several guides/how to's that are very helpful for systems that already have an OS.  I have access to another workstation w/ XP/Xubuntu.

The best I can do is:
```
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay = (did the system wait long enough?)
   - Check root = (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda0 does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

Here is my GRUB menu.lst entry:
```
title    Xubuntu 8.10 Live ISO
kernel   (hd0,0)/boot/vmlinuz root=/dev/sda0
initrd   (hd0,0)/boot/initrd.gz
```

I admit, I am a nOOb but I'm willing to take a hint/burn/advice.

Thanks  -OOOUNoHu

---

### Post by overdrank on 2008-12-02
Moved to ABT Absolute Beginner Talk :)

---

### Post by ooounohu on 2008-12-05
OK so, I've managed to get Grub and Puppy 4.1.1 installed.  From there I managed to copy the contents of the Xubuntu Desktop ISO to a local partition using help from here:

[[COLOR="DarkRed"]https://help.ubuntu.com/community/Installation/FromLinux[/COLOR]]("https://help.ubuntu.com/community/Installation/FromLinux")

IT BOOTS!  Terrific but, when I run the installer I have failure at step 4 when the partition manager doesn't see ANYTHING.  Absolutely nothing.  The only thing I can do is right-click the area where the partitions should be displayed and "undo changes" (not exact wording but you get the point).  I tried to manually create the partitions (1 ext3 partition and 1 extended partition housing a linux-swap partition) which yields the same results.

So more digging reveals:

[[COLOR="DarkRed"]http://www.lrz-muenchen.de/~bernhard/grub-chain-cd.html[/COLOR]]("http://www.lrz-muenchen.de/~bernhard/grub-chain-cd.html")

...which works well for booting the Xubuntu Desktop CD that the BIOS just doesn't want to boot but now I don't have a display.  I get the initial splash screen with startup choices but beyond any of the choices the display is nonfunctional even with the "vga=771" option.

At this point it's late where I'm at so I will start the Alternate CD downloading and tackle this again sometime soon.

If anyone sees this and has some insight I'm still all ears.

Thanks -OOOUNoHu

---

