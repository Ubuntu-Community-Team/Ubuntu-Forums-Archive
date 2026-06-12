---
title: "Problem booting into Xubuntu 12.04"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by hockeyfighter09 on 2012-05-04
Hey all, I recently installed Xubuntu 12.04 on my desktop alongside Windows 7, problem is I can't boot into Xubuntu at all.  No grub menu appears when I boot up the computer to pick which OS I want to boot into, it just automatically loads into Windows 7.  

There is a screen that flashes on for a brief second before the Windows 7 loading screen appears. From what I've seen it says something along the lines of "no hard disk detected" or something of that nature. 

 Xubuntu installed fine and I can see it on my hard drive space but cannot boot into it.  Any ideas how I can fix this issue? Thanks!

---

### Post by malefika on 2012-05-04
Did you install W7 and U12.04 on different partitions or in different hard disks? Did you install grub on bootable drive's MBR? Your problem may be easier to solve than it seems:lolflag:

---

### Post by hockeyfighter09 on 2012-05-04
> **malefika said:**
> Did you install W7 and U12.04 on different partitions or in different hard disks? Did you install grub on bootable drive's MBR? Your problem may be easier to solve than it seems:lolflag:

I did install it on the same hard disk.  In fact I've reinstalled it multiple times to the same problem.  I did the "custom" option in the install process for partitions and choose grub to be installed on "sda" portion of the hard disk. But the same situation happens.

---

### Post by 2ta8gdfte on 2012-05-04
Post the output of the bootinfo script it is a results.txt file that will be in home if you run this. 

wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

---

### Post by hockeyfighter09 on 2012-05-04
> **2ta8gdfte said:**
> Post the output of the bootinfo script it is a results.txt file that will be in home if you run this. 

wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

Do I do this in a Xubuntu live environment? When I try the first command it tells me the connection has a bad request and fails to download.

---

### Post by 2ta8gdfte on 2012-05-04
> **hockeyfighter09 said:**
> Do I do this in a Xubuntu live environment? When I try the first command it tells me the connection has a bad request and fails to download.

Download this script extract it to your desktop and run this command and pastebin the results text 

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

sudo bash ~/Desktop/bootinfoscript

The results text will show on the desktop this way.

Sorry about that the script to download does not render to the terminal as a copy and paste of the whole original script posted this will be a little easier.

I have to get back in shape in how to post in code boxs.

---

### Post by timzak on 2012-05-04
Did you ever get your system to boot into Xubuntu...even once?  Not counting the LiveCD.

---

### Post by hockeyfighter09 on 2012-05-04
> **timzak said:**
> Did you ever get your system to boot into Xubuntu...even once?  Not counting the LiveCD.

Nope, not even once since I've installed it.

---

