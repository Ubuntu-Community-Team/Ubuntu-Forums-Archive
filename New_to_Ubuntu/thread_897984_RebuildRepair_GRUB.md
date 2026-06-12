---
title: "Rebuild/Repair GRUB?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by wide-load on 2008-08-22
I have a dual boot system with a MSI K8N MB and AMD 3500+ processor.  I have an IDE drive with Windows XP Home installed.  I have a SATA drive with Heron installed.  I needed a little bigger drive for Windows so I used Norton Ghost PE to copy Windows to a bigger drive.  When I put the new drive in, apparently the Boot Loader didn't copy correctly.  When I boot the system it starts to boot and gets to where Grub starts.  When it does the screen fills up with the word "GRUB" over and over.

Is there a way I can repair or rebuild GRUB without reloading Ubuntu?  I have some time spent setting it up and really don't want to start all over again and have to reload 257 updates and set it back up like I wanted it.

Also, when I have this system finished it will be my wife's primary computer.  She likes Windows.  Is there a way I can make Windows the default operating system, so it boots without keyboard intervention?

---

### Post by spiderbatdad on 2008-08-22
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Patb on 2008-08-23
Wide, I second Spider's link. You might also look at: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

To change the default boot OS, once you have the grub working properly, take a note of where the "Windows" boot option sits in the list. Then edit your grub menu:
```
sudo gedit /boot/grub/menu.lst
```
find the line which says 
```
default      	0
```
and change the 0 to the number for Windows. Just allow for the fact the list starts at 0 not 1 and that the separator line "Other operating systems" (or something) is counted in. 

And for one of the best spiels on Grub see [Herman's grub page]("http://users.bigpond.net.au/hermanzone/p15.htm").

Cheers, Pat.

---

### Post by wide-load on 2008-08-23
Thanks a lot.  I was able to reinstall GRUB.  That saved be a lot of effort.

---

