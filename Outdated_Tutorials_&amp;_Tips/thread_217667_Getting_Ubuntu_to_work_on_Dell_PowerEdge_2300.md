---
title: "Getting Ubuntu to work on Dell PowerEdge 2300"
date: 2006-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by rayde on 2006-07-17
I just thought I'd share a quick hint to anybody who might be having trouble installing Ubuntu on a Dell PowerEdge 2300.  I had been running into a brick wall on this for a weeks ](*,).

it seems Ubuntu doesn't recognize something about the SCSI controller that these Dell's are using.  The quick fix for me, was to unplug the cable from the controller card, and plug it directly into the SCSI adapter that's on the motherboard.  You then need to fiddle around in the BIOS to get this adapter recognized, and hopefully you'll be able to continue with the installation.

Good luck, I hope this helps somebody!:cool:

---

### Post by ebozzz on 2006-10-21
Hi there,

Could I get you to expand on this issue? I am having the same problem. :confused:

[http://www.ubuntuforums.org/showthread.php?t=281509](http://www.ubuntuforums.org/showthread.php?t=281509)

---

### Post by Kadin2048 on 2008-02-14
I know this is a pretty old thread, but it seems like it's still relevant given that 6.06 is still supported, and thus the problem still exists if someone tries to install it... (like I just did, hence why I found the thread)

I have a Poweredge 2300 also, and I think the problem being encountered here is with the RAID card that shipped as standard equipment and certain 2.6-series kernels.  The card was called a "PERC 2/SC" by Dell, but is basically an OEM version of the American Megatrends Megaraid Series 466 (sometimes aka Series 200). Information on this card is available [here]("http://support.dell.com/support/edocs/storage/RAID/PERC2SC/2781e/en/Index.htm").

This card is *theoretically* supported under Linux with the "megaraid" driver, and there's lots of stuff around to suggest that it used to work ... but some work done to the driver for kernel 2.6 or thereabouts (the one used in 6.06.1 at least, which is 2.6.12 I believe) broke support for the older cards, including the Series 466. [More Information here]("https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/32752")

A patch exists, and has been incorporated into more recent versions (7.10 will work according to some users as long as you switch from "I2O" to "Mass Storage" in the card BIOS), but 6.06.01 LTS will not install out of the box onto a RAID volume because of the kernel bug.

I'm not sure about the 6.06.02 respin discs; I may try one just for the heck of it and report back.

Anyway, hope maybe this helps someone else who's out there with one of these machines still kicking around, wondering why it's not working.

---

### Post by gnaunited on 2008-08-19
I have one of these too. I ended up just pulling the raid card because it was not worth the hassle. What was really confusing was when I was able to install Win2K server and it detected the hard drives with no problems.

In the end I pulled the backplane and just installed a SATA card along with the special backplane power to molex connector.

---

