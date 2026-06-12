---
title: "Windows install works but not Ubuntu"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by hammodi2 on 2013-10-21
i've been trying to install ubuntu 13.10 for a day and i finally managed to sucessfully install it. but when i tried to boot the system. nothing happened. i checked the hdd's with xp boot and apparently all the hard drives were clean and empty. so i went back and installed the 12.04 LTS. same problem. i install it sucessfully but hard drive is clean. i ended up installing XP and this is the computer i was using, this proves that its not the PC problem. why is this happening? how can i fix it? i really want to  try ubuntu!

---

### Post by coldraven on 2013-10-21
> i checked the hdd's with xp boot
AFAIK you will not see a Linux install using XP, it does not recognise the disk format.
If you had booted with the Ubuntu Live CD "Try" option and run gparted it will have shown you the space used in the disc partitions.
It's quite likely that Ubuntu had installed but had booted to a black screen. Search for "nomodeset" and boot problems.
It should only take about half an hour to do an installation. I use Unetbootin to create a bootable SD card, it is faster than a CD and fits on a 1GB card.
Unetbootin will run on Mac/Windows/Linux [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by hammodi2 on 2013-10-21
GParted wont  work. it freezes at the cmd code installation. some sorta DOS thingy. idk when i click run GPARTED through standard version it loads for a while till it stops. had several porblems with other linux stuff too

---

### Post by deadflowr on 2013-10-21
Gparted wouldn't open when you ran it from the livecd?

It's an app like other apps, so it shouldn't be showing you any command line jargon.
Like coldraven stated, use the Try Ubuntu option, when you get the ubuntu home screen, click on the ubuntu icon in the top of the launchers, then type gparted and enter.

Also stated earlier, the file system type that Ubuntu uses cannot by read by Windows systems, by default(though, I have read that there are tools you can install to do so). Meaning the disk will always show as empty in Windows.

My best bet on this is that GRUB wasn't installed properly, or was installed in the wrong place.
Try this
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
It can happen quite often and more so in a dual-boot scenario.

---

### Post by mörgæs on 2013-10-21
Please use a more informative thread title. 
Changed.

---

