---
title: "Moving from Windows to Ubuntu wihtout CD, USB"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by Scott_Page on 2013-10-14
Hello, as the title says, I am looking to transfer from Windows (7) to Ubuntu.

My reason for this is that Windows is taking up too much space. My computer is 13 years old, and has a 20GB hard drive (13 of which are alerady used by C:/Windows). I have about 1GB of files left on the computer (which took a hell of a lot of freeing up space*) outside of C:/Windows, meaning a 6GB space to work with. I know that this is enough to install Wubi and so my thinking is it should be enough for a standalone installation (not sure if 'standalone' is the right word, but I imagine you konw what I mean).


Another note about my computer is that it doesen't have a working CD drive (I sorta broke it :oops:). And, while my compute has USB1.1 ports, I cannot boot from them (don't know why, but I remeber trying and failing).

In an ideal circumstance I want to be able to completley remove Windows from my computer and only have Ubuntu.

*I  uninstalled pretty much every proram on my computer, uploaded the files to Google Drive, etc

Please help where you can,
Scott

---

### Post by Toz on 2013-10-14
Hello and welcome to the forums. 

I have removed your duplicate post.

---

### Post by Scott_Page on 2013-10-14
Thank you, I really didn't mean to. Sorry.

---

### Post by Bucky Ball on 2013-10-14
If you can install Wubi, doesn't that then have an option to install Ubuntu? Tricky one, I have little (no) idea about Wubi and not many Wubi gurus around here as not used much (and I believe it is being/has been phased out after 12.04).

---

### Post by Bucky Ball on 2013-10-14
Try this:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Apparently Unetbootin lets you create an install USB, OR do a frugal install to the hard drive. Might work ...

> UNetbootin can create a bootable Live USB drive, or *_it can make a "frugal install" on your local hard disk if you don't have a USB _*drive. It loads distributions either by downloading a ISO (CD image) files for you, or by using an ISO file you've already downloaded. 

For an old machine like yours I would advise using Xubuntu or Lubuntu (or lighter). Ubuntu will be a struggle and not a nice experience if you can actually get it to work.

---

### Post by fantab on 2013-10-15
> **Scott_Page said:**
> ...

...I know that this is enough to install Wubi and so my thinking is it should be enough for a standalone installation (not sure if 'standalone' is the right word, but I imagine you konw what I mean).
...
In an ideal circumstance I want to be able to completley remove Windows from my computer and only have Ubuntu.

Scott

With the Old machines, which in your case is 13yrs. old, the most important thing to look for is the RAM size, amongst others.
The Memory [RAM] size of 256MB is bare minimum and with this kind of memory you can only consider [minimal-Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). If the Memory is 512MB or more then consider Lubuntu or Xubuntu.
WUBI installs Ubuntu as a Windows program. So you need Windows to run Ubuntu with WUBI. This does not solve you Disk space issue. Installing only one OS is recommended. NO WUBI for this machine.

Now, to be able to boot from USB you have to set the Boot setup in BIOS to boot from USB devices. Then [follow this]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") to burn the ubuntu.iso to the USB disk. Or use the tool Bucky Ball suggests.

---

### Post by mastablasta on 2013-10-15
20 GB drive of which windows 7 (:-o) is taking most of it. if you ask me that HDD is to small for anything useful. & GB is enough to install Ubuntu but not much else and oyu will be contantly runnign out of disk space.

now assuming you have enough ram and really do run windows 7 (which means you have 512 or 1 GB ram) i would suggets you start with Xubuntu (go with 12.04 version). first we need to boot into it to see if everything on the laptop is recongised and if all works (sound, wi-fi etc).

so create a bootable USB using unetbootin, linuxliveusb installer or pendrivelinux.

if BIOS doens't have a boto from USB option (which is nothing unusual for such an old mashicne) i bet you still have floppy drive. if that one works you can create a bootable floppy using plop boot manager: [URL="http://www.plop.at/en/bootmanager/startmodes.html"]
http://www.plop.at/en/bootmanager/startmodes.html[/URL]

how to install plop boot manager on floppy disk: [http://www.plop.at/en/bootmanager/plpbt.bin.html](http://www.plop.at/en/bootmanager/plpbt.bin.html)

you can then stick the USB with propperly set ubuntu image in the laptop, set the laptop BIOS to boot from floppy first. then it will boot and open the PLOP boot manager where you can select an option to boot from usb. once the OS boots select try it to see if it all works. then if you are pleased with performance you can install it and just use the whole disk (it will remove the windows). if performance is not good you can try Lubuntu instead or Bodhi linux or... well there is plenty of them but first let's see if it all works and if you can get it to boot.

post back if you have any issues.

---

### Post by sheldon-corey on 2013-11-06
In using Penlinux I have no issues downloading or using my pre downloaded 13.10 ISO or running PenLinux, (no errors come up)  however when I attempt to boot from the USB and rid my Dell Laptop of Win XP for a pure Ubuntu install I only get "Invalid Boot.INI ----  Booting from C:\WIndows"

Can someone please help, have tried Wubi which allows 12.04.3 but wish to have 13.10 and going from 12.0.4.3 to 12.10 was a nightmare via USUM

---

### Post by mastablasta on 2013-11-06
is the iso good (md5sum check)? try a different programe such as unetbootin or linuxliveusb.

---

### Post by fantab on 2013-11-06
> **sheldon-corey said:**
> In using Penlinux I have no issues downloading or using my pre downloaded 13.10 ISO or running PenLinux, (no errors come up)  however when I attempt to boot from the USB and rid my Dell Laptop of Win XP for a pure Ubuntu install I only get "Invalid Boot.INI ----  Booting from C:\WIndows"

Can someone please help, have tried Wubi which allows 12.04.3 but wish to have 13.10 and going from 12.0.4.3 to 12.10 was a nightmare via USUM

WUBI works only from within Windows, so "no windows, no wubi". Anyway WUBI has its own problems. Forget WUBI.

Boot with Ubuntu USB/DVD and "Try Ubuntu without installing", can you do that? 
If you can, then open Gparted and from menu choose 'Device' -> 'create new partition table'. When you create a new partition table all your DATA will be permenantly Lost, So BACKUP ALL YOUR IMPORTANT DATA, first.

Then create new partition, and install Ubuntu to it. Give atleast 1-2GB for Linux SWAP partition.

---

### Post by urapain on 2013-11-06
I think you are stuck because you need a bootloader on something supported by the bios.  pretty sure pen modifies the boot loader on the harddrive.  I think that is why you can't use it to reformt the hard drive.  You might be able to do it by mounting a cd imagfile in ram disk or on network.  System rescuecd @sysresccd.org has solved a "lot" of problems for me in the past.

---

