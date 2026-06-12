---
title: "Ubuntu won't boot. &quot;Kernal panic - not syncing: VFS: Unable to mount root fs on..&quot;"
date: 2014-01-13
forum: New to Ubuntu
---

### Post by natepwatson on 2014-01-13
I'm a complete noob to Linux and Ubuntu. I've mounted windows and installed with cd's and dvds before but only with windows. 

I wrote the Ubuntu iso to a 64 gb usb stick as directed on Ubuntu.com. Once I boot from the usb drive I get this message:



[     1.067488]  Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)



I have no idea what that means. Any one know how to get it started up so I can try this out? Thanks


[IMG]http://imagizer.imageshack.us/v2/800x600q90/5/ol5b.jpg[/IMG]

[IMG]http://imagizer.imageshack.us/v2/800x600q90/835/3sy3.jpg[/IMG]

---

### Post by sandyd on 2014-01-13
Hi, have you checked the MD5sum of your iso - instructions at [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

---

### Post by joachim_altmann on 2014-01-14
HI, i had the same problem with an external USB-Harddisk trying to install "Linux from Scratch" on it. The kernel is not able to prepare or access the linux-root-directory, presumely on the USB-stick. There are several possible reasons for this behaviour, either a faulty configuration of the bootloader of a lacking module to access the USB-Stick. From my point of view it became quite complicated to fix this error, so I took a workaround and used an older USB-stick to install Linux. This worked fine.
If you are new to Linux, I would recommend the same. Take an older (you do not need 64 GB) stick and try to install Linux on it. This is enough for having just a look on it and if you stick to it, you will probably install it on HD anyway and this works for sure. I am running a dual boot with Win7 and Ubunt and do not have any problems, though I do not use Win7 that much any more.
Btw, it does not have anything to do with your PC.

---

### Post by joachim_altmann on 2014-01-14
... here is an afterthought: If you are really interested, just search for "not syncing root fs block" or the like, Quite a lot of stuff and despair out there and very instructive .... :-)

---

### Post by hoopia on 2014-01-14
I ran into this error about 2 days ago.

I had used UNetbootin to create an Ubuntu installer from my USB stick, but the installer was corrupted. You can confirm by booting up to the "Live CD" off of the USB stick and running the Check Disk option (forgot the exact wording, something related to checking the integrity of the disk). It found about 16 errors. 

I re-created the Ubuntu Live CD on the USB stick and 2nd time around everything was fine.

---

### Post by oldfred on 2014-01-14
There are some systems that will not boot installer from very large flash drives. Those need 4GB or smaller. Probably something to do with FAT32 sizes which normally should not be an issue.

Other have issues with USB2 or USB3 ports where only some work.
Others have issues with certain flash drives. 
 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

And some seem to have better success with a different installer.
      
 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

