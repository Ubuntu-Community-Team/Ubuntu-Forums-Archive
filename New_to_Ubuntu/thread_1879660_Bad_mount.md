---
title: "Bad mount?"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by YOoman on 2011-11-12
I was making a bootable USB to install oneiric ocelot on my net book. Soon as it finished, I ejected it and plugged it back in to check if I had the x86 version. I think I forgot to safely remove cuz now it just says "Mount and Open 11.10 i386" in my devices. Might have a bad mount but kinda newb. Any help appreciated :D

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by -kg- on 2011-11-12
What software were you using to make the bootable USB device, and where?  Were you using Unetbootin?  Startup Disk Creator?

The reason I ask this question is, I've always used Unetbootin to make my bootable LiveUSBs.  I've also never had success selecting the distribution from the list at the top of the window (where it is downloaded before being installed).  The only way I've had success is downloading the .iso and after verifying the md5 checksum, selecting that iso in the second part.  That works every time (for me).

One way you can check if the installation took is to try and boot to the drive.  If it doesn't boot, it didn't take, and you'll have to try reinstalling it again.  Personally, I suggest Unetbootin using the method I describe.  If you're burning it using another computer with Ubuntu, Unetbootin is available in the repos.  If you're using a Windows computer, there is a [Windows version]("http://unetbootin.sourceforge.net/") available that will work, as well.

Note that if you have to reinstall it, you'll need to go in with Gparted, delete the partition that will be there, and create a new partition.  Format that partition as FAT 32.

---

