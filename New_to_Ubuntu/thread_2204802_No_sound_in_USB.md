---
title: "No sound in USB"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by j60dnl on 2014-02-10
Hello all, I am the very definition of AbsoluteBeginner and am in need of some baby-steps help!

Have recently swapped from Windows7 (which was killing my Netbook) over to Xubuntu. 
It runs great, smoothly and am delighted with the swap. 

My only problem is that I'm at a loss of how to get my USB headphones to work (or, more accurately, my usb jack)
All my other USB things (mouse, ext hard-drive etc) are recognised and work as they should but my headphone just, when plugged in, makes its usual connected sound (a millisecond of a "hiss") but the sound only ever comes out of the PC speakers and I'm struggling to find the right commands / options to figure out my problem.

As I say, total newbie, so barely understand this Terminal malarky but am absolutely here to learn and answer anything that I've missed out to get me on my merry way.

**Some details :**
Packard Bell Dot-S running Xbuntu 13.10 "Saucy Salamander" 
USB Jack : "Yoga AD-100 USB Soundcard"

MANY THANKS in advance!

---

### Post by pqwoerituytrueiwoq on 2014-02-10
[IMG]http://i.imgur.com/LasL9J9.png[/IMG]
go to the "Output Devices" tab, you may need to change the port or default device (to change default click on the green check mark on the right side of the device)

---

### Post by joshrules001 on 2014-02-10
I haven't used xubuntu in a while but I think the volume is turned off by default.  Check the above post. If that don't work you'll need to find the drivers.  Ubuntu comes with most drivers already installed but sometimes there's some that it don't

---

### Post by Vladlenin5000 on 2014-02-10
Generic USB audio devices are supported since a long time ago. I never had any issue in any Ubuntu or variants but yes, whenever there are two or more sound cards - the USB devices are are external sound "cards" - it must be explicitly selected. Most apps will just grab the system default, ie, the device already selected for the output, whereas others like Skype might think differently. Anyway, it's just a matter of configuration.

---

### Post by j60dnl on 2014-02-10
OK, thanks for all the tips - to work I go! Will report back

---

### Post by j60dnl on 2014-02-10
Fixed! MANY thanks!! 
Like you say, was just a case of using Pulse to adjust the output / volume.
Delighted :D THANKS all

---

