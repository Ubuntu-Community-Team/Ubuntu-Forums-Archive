---
title: "Booting from USB trouble"
date: 2016-11-15
forum: New to Ubuntu
---

### Post by goodwell on 2016-11-15
I am trying to boot Linux from a USB drive.  I have a Dell tower, Optiplex 210L, with a pentium 4 that came with Windows XP.  I get to the Boot Drive Menu, select Boot from USB and hit Enter.  The light on my thumb drive flashes a few times then stops.  And nothing else happens.  

This is an abandoned School computer that I am trying to get running again for my class.  Could something have been done in the BIOS to stop this from booting from a USB drive?  Should I try a different USB drive?

HELP

---

### Post by yancek on 2016-11-15
Since you are posting at the Ubuntu forums, are we safe in assuming you are trying to boot Ubuntu?  Which release?  Did you do an md5 checksum on the downloaded iso file to verify it's integrity?  How did you get the iso on the usb, what software did you use?  Do you have another computer (maybe newer) that you can try the usb on just to see if it boots?  Have you ever booted a usb from this computer?  When you go to the BIOS to set boot priority, do you see the name of the device (Sandisk, Toshiba, etc.) listed?

---

### Post by RobGoss on 2016-11-15
By not providing any specs this is only guessing, from the sound of it I'm thinking this is a really old machine which makes me wonder if it can even boot from this USB drive. I'm assuming you're trying to install Ubuntu and if so you might want to try a lighter distribution like [Lubuntu ]("http://lubuntu.net/")or [kubuntu]("http://kubuntu.org/")

I would try burning the ISO file to a DVD and try booting from that it might be your best option at this point. If you can try posting the specs for your machine so others may lend a helping hand

---

### Post by Autodave on 2016-11-16
You cannot simply copy the iso file to the thumb drive: it has to be put on there as an iso installation.

---

### Post by goodwell on 2016-11-16
Answers:  (1) Ubuntu Desktop 16.04.1 LTS.  (2) No md5 checksum, I didn't have time to figure it out (I'm just beginning to learn this hacker stuff). (3) I downloaded the file from an iMac and dragged it to a USB drive.  I guess that may be the problem--maybe.  (4) The computer is vintage 2005, Pentium[R] 4, 2.8 GHz CPU with 504 MB RAM.  (5) I have never booted ANY computer from a USB drive.  (6) When I booted, as it was starting, I hit the F12 key.  I highlighted the "USB Device" choice--it only shows up if the USB Drive is plugged in, and hit "Enter".  The USB Drive's LED flashes 2 or 3 times and nothing else happens.

Was I suppose to use some kind of special protocol to load the file on the USB drive?

---

### Post by sudodus on 2016-11-16
I have an old Dell Dimension 4600 desktop computer with the same CPU. But I have added RAM, so it is totally 1.5 GB, and it makes a big difference.

You need the Ubuntu flavour with the 'lightest foot-print' - Lubuntu 32-bit. I suggest that you try with the following iso file:

**lubuntu-16.04.1-desktop-i386.iso**

There might or might not be problems with the graphics card.

Check the md5sum in linux with ***md5sum*** and in Windows with for example the program ***md5summer***. 

You should use a tool to install from the iso file to the USB pendrive (or a DVD disk, if you have a DVD drive).

See this link, [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick).

See the following link for more tips about old computers, [Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640).

---

### Post by goodwell on 2016-11-16
Thank you Forum.  I am sure that I will be able to create a bootable USB drive when I get home.  (I can't load programs on my networked school computers.)  And please don't think less of me for not knowing that an iso file needs to be installed, not just copied.  I am just starting out and there is a lot to know.  I'll get there.

---

### Post by RobGoss on 2016-11-16
We're all here to learn and do not think of anyone less. The fact that you're willing to give Linux a try should be commanded

There's no such thing as a stupid guesting that's the only way to learn

---

### Post by sudodus on 2016-11-16
+1

Feel welcome and ask questions :-)

---

