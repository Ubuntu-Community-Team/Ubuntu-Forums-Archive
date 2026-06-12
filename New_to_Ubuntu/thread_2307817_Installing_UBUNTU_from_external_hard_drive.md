---
title: "Installing UBUNTU from external hard drive"
date: 2015-12-28
forum: New to Ubuntu
---

### Post by Vonn_Ishee on 2015-12-28
I do not have a flash drive, or a DVD disk. But I do have a 250gb external hard drive that connects to the computer the same as a flash. Is there any reason that I could not or should not install UBUNTU to the hard drive and boot that way? Also what is the best UBUNTU type to use for a student. This laptop is old and slow with wondows vista, and I know from past experience that UBUNTU is very smooth and fast. Are there any types that can play youtube videos, GIFS, flash, and all those things right out of the box without doing all kinds of fancy computer work? I need youtube because I watch allot of college lectures on there. And of course everyone needs GIFS for reddit. 

Anyway the most important question is can I boot from  250 GIG external drive? And which one works with the best right out of the box, thanks you guys.

---

### Post by Dennis N on 2015-12-28
You mean installing Ubuntu **on** an external hard drive?

If possible, I would install on the internal hard drive. Old laptops that originally ran Win XP seem to do well with Xubuntu or Lubuntu. Take your pick. Any Ubuntu-based distro can handle all the multimedia tasks* you mention provided you elect to install the multimedia codecs when installing (or it can be done after as well).

If installing on a portable sometimes connected, sometimes not connected external drive (flash or hd), I install GRUB bootloader to the MBR of the external drive and select that drive from BIOS to boot it (one-time boot, or change boot order).

*also depends on your processor and graphics system.

---

### Post by yancek on 2015-12-28
Not enough information.  You can easily put an Ubuntu iso on your hard drive, boot the iso file and install to another drive/partition.  You can do this by booting from Grub2 with a correct entry in the grub.cfg file.  You don't indicate what operating system(s) you have so if all you have is vista, then  no as there would be no way to boot it the iso.  You might check the minimum hardware requirements for the different Ubuntu distributions and compare that to the hardware you have.  Any Linux system should be able to do the things you list.

---

### Post by Vonn_Ishee on 2015-12-28
I do have vista installed now. I have a windows 8.1 pro and windows 7 pro install disk. I have a 2.0ghz dual core processor pentium T4200, 3gb of RAM. I am not shy of not dual booting, I have another system with windows, I am willing to just format this whole computer and making it an UBUNTU only system.

---

