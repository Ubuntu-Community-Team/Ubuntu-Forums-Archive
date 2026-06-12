---
title: "New distro gnome?"
date: 2007-01-13
forum: Other OS Talk
---

### Post by haxer on 2007-01-13
Hello im looking for a new distro i thought about linux backtrack but how to make an hard drive install? Is it possible to get gnome on it? ;) :-k

---

### Post by bruenig on 2007-01-13
BackTrack is live cd only and it is also fluxbox and kde only, although I am sure that you could get gnome on it if you could install it. But all of that is moot since it can't be installed in the first place.

---

### Post by kerry_s on 2007-01-13
Back in the day i started from #1 and worked my way down the list-> [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by haxer on 2007-01-13
So its not possible to install backtrack from the live cd or any other way?;)

---

### Post by haxer on 2007-01-14
anyone? ;)

---

### Post by RAV TUX on 2007-01-14
don't know I have never tried BackTrack

---

### Post by RAV TUX on 2007-01-14
If you are looking for a new distro I suggest you start here:

[http://linuxtracker.org/](http://linuxtracker.org/)

---

### Post by Sef on 2007-01-14
> So its not possible to install backtrack from the live cd or any other way?

If it is a Live CD only, then there is no way to install it on your computer, unless you implement a install feature.

---

### Post by haxer on 2007-01-14
> **Sef said:**
> If it is a Live CD only, then there is no way to install it on your computer, unless you implement a install feature.

Ok what but will it ever be possible to do a hdd install of it?:-k

BTW im haxer at linuxtracker to :) been member since they started :D

---

### Post by xiaoxin on 2007-04-08
It is possible to install BackTrack to the HD 
[http://backtrack.offensive-security.com/index.php?title=Howto:Install_GUI]("http://backtrack.offensive-security.com/index.php?title=Howto:Install_GUI")

---

### Post by AsatruarHack on 2008-05-30
Hey dude. Don't believe these guys in here. BackTrack is completely and 100% hard drive-installable. As a matter of fact, I have it installed on the machine that I'm typing this on. It's not as simple as the Ubuntu installer, however. You have to fdisk it and write the changes to disk. Then, you go to the K Menu(in BackTrack live) and click on System, then BackTrack Installer. After you get here, specify what directory you'd like to install to. Here's a good tutorial I read that follows these steps in detail. 

 1) Boot the live CD 
 2) In the terminal, login as root (password is toor) 
 3) type cfdisk and hit enter 
 4) delete any partitions on the drive 
 5) create a new primary partition that is 512MB and set the type to 82 ( Linux Swap) 
 6) Create a second primary partition for the rest of the disk, and set it as bootable. 
 7) Write the new partitions to disk, then quit 
 8) Type umount /dev/hda2 (or sda2 depending on computer) then enter (Just in case)
9) Type mkswap /dev/hda1 then enter
10) Type mkfs.ext3 /dev/hda2 then enter. If this fails, you may need to reboot and do it again.
 11) Type mkdir /tmp/backtrack then press enter 
 12) Type mount /dev/hda2 /tmp/backtack 
 13) Type startx and press enter 
 14) After KDE starts, browse to K > System >Backtrack Installer 
 15) Leave the first box blank (Under source) 
 16) Type /tmp/backtrack for the install to box 
 17)  Write MBR box should be autofilled, if not type /dev/hda (or /dev/sda depending on hardware) 
 18) Click the "real (2700...) " radio button. 
 19) Click install.

Done! 
Think about it; if the creators of BackTrack didn't want you to install it to your hard drive, then why is there a BackTrack installer link in the K Menu?

If you need help with it or you're in a bind with installing it(which there are some errors that could occur in this process), send me a message. Later, bro.

---

