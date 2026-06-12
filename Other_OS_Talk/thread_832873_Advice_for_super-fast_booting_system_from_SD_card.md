---
title: "Advice for super-fast booting system from SD card?"
date: 2008-06-18
forum: Other OS Talk
---

### Post by BrendanM on 2008-06-18
So I have a laptop (WinBook TL30 - the hardware is Asus) and as far as I can tell, the BIOS supports booting from the SD card slot. I was wondering if it would be possible to set up some sort of extremely minimalist, very fast-booting system that would load from this memory without even spinning up the HDD?

I'm thinking of something along the lines of [splashtop]("http://www.splashtop.com/"), with just wireless support, a browser, and maybe IM and/or VLC for videos. I was looking at OSes like KolibriOS, Damn Small Linux, DeLi Linux, etc., but most of them seem to be optimized for small size, so they use a lot of compression tricks that would probably slow down booting. Also, a Live distro is going to be slow doing hardware detection.

What would people recommend? Has anyone done something like this?

---

### Post by kerry_s on 2008-06-18
i would say try it first, grab DSL and do a frugal install to the sd card, see if it can do what you want first before you build a custom install.

---

### Post by gregology on 2008-06-30
I am also interested in getting a fast boot from my sd slot on my HP Compaz nc4400. Let me know how you go :o)

---

### Post by tinny on 2008-07-01
I cant fully answer this question but I have had great success running [xubuntu]("http://www.xubuntu.org/") on my eee PC using SD memory. It boots < 20sec.

Xubuntu uses Xfce instead of Gnome. Xfce is much lighter than Gnome.

---

### Post by tinny on 2008-07-01
BTW

If you install your OS (some flavor of Ubuntu???) to SD flash memory be sure to have no swap and use the ext2 file system (less writes to disk, disk writes slowly kill flash memory). Also use the noatime attribute in your fstab and you can also move all temp files to RAM instead of the flash disk drive to save on disk writes.

E.g.

In my /etc/fstab I have two flash drives, one is "/" and one is /home

Also notice that my tmp / log files are in RAM (tmpfs)

```

# /dev/sda1
UUID=4ffb4c02-860f-45a3-98b6-bc83101854e7 /               ext2    defaults,noatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=efec23b1-2ed7-4180-9a87-6f6702408886 /home           ext2    defaults,noatime,errors=remount-ro 0       0
#Temp fs for og etc
tmpfs      /var/log        tmpfs        defaults           0    0
tmpfs      /tmp            tmpfs        defaults           0    0
tmpfs      /var/tmp        tmpfs        defaults           0    0

```

---

