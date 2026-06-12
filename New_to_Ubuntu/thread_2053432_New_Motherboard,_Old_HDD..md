---
title: "New Motherboard, Old HDD."
date: 2012-09-05
forum: New to Ubuntu
---

### Post by spuffff on 2012-09-05
Hey,

Ive just purchased a new motherboard (asus p8h77m), i3 CPU and ram. My previous HDD was running Ubuntu 12.04. 

I have connected it all up and it seems to work in the sense that I can boot from my usb dvd drive. but when exploring the bios there is no HDD to be seen. 

This makes it a little difficult to finish the job. 

It is a SATA seagate 7200 500gb. Im not quite sure what im doing wrong if anything. 

I have tried switching the sata port which the HDD was connecting to motherboard. Initially the one of the top right. Then the bottom left (grey).

I did read something on the net about certain motherboard not running linux distro's - ?? im lost. 

Any help fellas much appreciated.

---

### Post by mikechant on 2012-09-05
I would say that if the BIOS isn't recognizing the HD, then it can't possibly be anything to do with "certain motherboards not running Linux distros"; the motherboard doesn't even know you've got Linux installed if it can't see the disc!

You've tried a different SATA port, but have you tried *all* the SATA ports, and have you tried a different SATA cable?

I think when I last added an extra internal HD to my Desktop PC, there were two different groups of SATA ports in different places on the motherboard, and one group them didn't work at all (?maybe not available on that particular model).

---

### Post by spuffff on 2012-09-05
TO be honest I read [http://www.tomshardware.com/forum/287386-32-bios-detect-hard-drives-asus-p8h77](http://www.tomshardware.com/forum/287386-32-bios-detect-hard-drives-asus-p8h77) and played around with the different SATA ports. 

Blue : Sata1 (top row on the right) - here the bios setting was set to IDE
Grey: Sata 1 (bottom row on the right ) with the bios setting to ACHI .

I also swapped the Sata cable from the old one being used to the SATA provided in the motherboard box

With no detection.

Cheers.

---

### Post by SlugSlug on 2012-09-05
make sure that sata port is enabled in the BIOS

---

### Post by lukeiamyourfather on 2012-09-05
Read the motherboard manual for a description of the ports. Some might be connected to a third party controller or disabled by default. If the disk was working previously the issue is likely the SATA cable, the motherboard, or something simple like the hard disk doesn't have power or the port is disabled in the BIOS.

---

### Post by spuffff on 2012-09-05
Yeah, It seems that SATA port is enabled. 

I can select the ports SATA3G1(blue) or SATA6G1(grey) to be enabled individually if i enable ACHI.  IDE doesn't seem to have an option.

I swapped the SATA cables back to my original thinking that it might be because my HDD's old speed is not something like 6Gb/s, and i plugged it into the 3G1 port.

---

### Post by spuffff on 2012-09-05
Yep, im certainly a noob, you were right [lukeiamyourfather]("http://ubuntuforums.org/member.php?u=774656"). no power to the HDD. But the setting of SATA3G1 enabled on ACHI works.

THanks all for your time. 
IF bitcoins were free i'd give you one. :))

---

