---
title: "HOWTO Create a Bootdisk for Ubuntu (on WinXP)"
date: 2006-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by hakre on 2006-08-29
**HOWTO Create a Bootdisk for Ubuntu (on WinXP)**

With an older computer I ran into problems booting the Xubuntu 6.06 CD directly by the Bios because the boot section of the CD was not compatible.

You can create a bootable Floppydisc which then can boot the (X)ubuntu CD to work around BIOS limitations. It is already describben in the *\install\README.sbm* file but the information is a bit out of date and has a general character.

I will show how I successfully created such a bootdisk on WinXP.

**What do you need?**
1.) *sbm.bin*
2.) *NTRawrite.exe*

**Where to get?**
1.) *sbm.bin* is located in the \install\ directory on your CD
2.) *NTRawrite.exe* can be downloaded on sourceforge: [http://prdownloads.sourceforge.net/ntrawrite/NTRawrite-1.0.1.zip?download](http://prdownloads.sourceforge.net/ntrawrite/NTRawrite-1.0.1.zip?download)

**What to do?**
Copy both files into one directory and then open a commandline (cmd) in that directory. Type in 
*ntrawrite -f sbm.bin -d a:* and insert a blank floppy into drive A: to create the bootdisk. The data will be written to the floppy and verified afterwards, then the whole thing is completed!

The Bootdiskette has been created now. You can insert it into the Computer where you want to install Ubuntu to and reset it/ switch it on. A programm called "Smart Boot Manager" will offer a list of Drives from which to boot. One Entry is label CD-ROM. Select this one.

If it does not exists, select Floppy. Then the screen will refresh and display the same list again, but this time, CD-ROM will be listed as well.

Press Enter to select the device you'd like to boot. CD-ROM is the one you're looking for.

Hope this information is usefull.

**More Info**
Well, quite the same is already in the documentation, have not found that before:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)
it's inside the very informative installation section:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by jcoleman on 2006-10-13
Have an old Toshiba 660CDT laptop with a floppy attachment and CD-ROM. RAM is about 84MB and hard drive a 1.4 GB. CD Disk would not boot from CD-ROM. **The set-up described here worked just fine.** Trying out Xubuntu-alternative. Windows 98 got knotted up again and was making me nuts.

Thanks
](*,)

---

### Post by PendragonUK on 2006-10-22
On my old IBM 560Z the CD Drive is PCMCIA, will this method detect the CD Drive??

---

### Post by jordoex on 2006-11-02
This is slightly superior to the wiki docs because you said to use NTrawrite, whereas the wiki says to use regular rawrite and in the NTrawrite readme, it describes the problems with regular rawrite.  Maybe the wiki should be updated.

---

### Post by cloakable on 2006-12-09
Tried this, didn't pick up my cdrom :(

IBM ThinkPad 240, using the IBM IDE to PC Card adaptor.

Can anyone help?

---

### Post by aysiu on 2006-12-09
Moved to the appropriate subforum.

---

### Post by cloakable on 2007-01-04
Still nothing? O.o

---

### Post by BunnyEars on 2007-02-08
[I]Tried this, didn't pick up my cdrom

IBM ThinkPad 240, using the IBM IDE to PC Card adaptor.

Can anyone help?[/I]


I am trying to revive this type too. Dont have the CD_ROM drive.
I found out u can use a freedos floppy to bootup & recognize the usb port (on the right side).
I am using a bootdisk called WAKE2PUP (which is suppose to assist the install of PUPPYLINUX). 
link - [http://www.murga-linux.com/puppy/viewtopic.php?t=7979](http://www.murga-linux.com/puppy/viewtopic.php?t=7979)
*make sure you stick the USB thumbdrive in, b4 boot up.
At this moment, i can bootup & recognize the USB Thumbdrive & transfer files from it into the HDD.

Now, i am trying to transfer an install package into the HDD (via USB thumbdrive), so i can install from there. Don't know how it will work out. - if anyone can help to suggest a distro.

Details: Celeron500, 128Mb RAM, 10GB HDD

:)

---

### Post by ChantCd on 2007-05-03
How do you create a boot floppy if you've already switched to Linux?

I'm on a Fedora Core 6 machine right now...

I'm trying to install Ubuntu on another machine.

Matthew

---

### Post by yzoldowl on 2009-02-08
The link to [http://prdownloads.sourceforge.net/n...1.zip?download](http://prdownloads.sourceforge.net/n...1.zip?download)
seems to be broken.  Anywhere else I can get this file?  I am trying to install Ubuntu on two computers that were cleaned out -- no software of any kind on them and I can't reset the BIOS so I can start from the DVD.  Many thanks!

---

