---
title: "ubuntu 11.10 vs 11.04 issues"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-11-17
I've been running ubuntu 11.04 from a DVD and also from a USB boot drive for a month or two on my windows 7 Acer Aspire laptop and also on my Compaq Presario XP desktop.   Tried 32 bit and 64 bit versions, both seemed to work on both PCs.

The desktop forces to the classic version with 11.04

The laptop has the following issues with 11.04
- touchpad vertical scroll doesn't work and cursor seems to jump around
- crystal eye built in webcam is poor quality compared to webcam with windows 7

All in all, pretty successful running ubuntu 11.04 with FireFox, Thunderbird and several addons on both laptop and desktop.  Didn't notice any difference between 32 bit and 64 bit.

= = = = = =

Experience with 11.10 somewhat different

- with laptop and USB drive, can't write to NTFS drives [solved], but can write to NTFS drives with Boot DVD - 64 bit
[http://ubuntuforums.org/showthread.php?t=1881701](http://ubuntuforums.org/showthread.php?t=1881701)

- on Compaq XP presario desktop, 11.10 USB will not boot and DVD tries to boot, screen looks fine and then border of the screen turns to stripes.   Basically my desktop runs 11.04 in classic mode, but not 11.10.  

Will try setting USB to 2 D on laptop and try on desktop.

= = = = 

2D didn't help - desktop makes it through the grub, but hangs after "checking fro running unattended upgrades"

= = = =
rebooted into 11.04 USB drive - loads to classic and writing this now on desktop.

Seems strange that from 11.04 to 11.10 that my desktop now longer works with ubuntu.  I liked ubuntu because it seemed to work on a lot of PCs.  Will wait and try next version for desktop and stay with 11.04 there.   For laptop will use 11.10 if can solve read-only file issue - if not stay with 11.04 there also until next version or fix found.

Anyone else having similar experience?

---

### Post by Mark Phelps on 2011-11-17
I've been using Ubuntu daily since the 7.04 days and every new version breaks things that worked previously -- at least, that is my experience.

As to why?

Because underlying stuff changes from version to version.  The kernel versions are always different. The X-server versions are nearly always different.

In this case, Ubuntu went from Gnome v2 to Gnome v3.  That has cause stuff to not work anymore.

In addition, since restricted video drivers are kernel version specific, those drivers often will not work when a new Ubuntu version comes out, and that continues until the driver developers catch up.

Which is why I (and most other seasoned veterans of Ubuntu here) advise strongly AGAINST in-place upgrades.

---

### Post by Denver Dave on 2011-11-18
Thanks for the post.  I have one USB stick with 11.04 and one with 11.10, so for now, I'm OK, but would like to sometime get back to only having to maintain 1.

I'll keep doing updates to the 11.10, maybe the desktop issue will get fixed.  Seems like there should be a lot of Compaq XP Presarios out there.

I'll report back if something changes.  Helpful if others with similar problem would post here.

Dave

---

### Post by Denver Dave on 2011-11-22
I had the touchpad issue in both 11.04 and 11.10.  This solved it for me with my Acer Aspire Windows 7 laptop running 11.10 from a USB stick:

= = = = = = 

Found this which added vertical scroll to my touch pad.  Amazing worked after all the configuration and term commands I tried:
[https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Natty](https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Natty)

> Keyboard and Touchpad

Basic features of the keyboard and touchpad work out of the box. However, the scroll function does not work out of the box at most recent check. If you have this problem, it is possible to fix using the following command:

echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse

This will tell Linux to treat the touchpad as a generic PS/2 mouse with a scroll wheel. Scrolling on the right-hand side of the touchpad should now work. However, horizontal scrolling does not work. 

The approach above to add vertical scroll removes the touchpad tab from the mouse properties.  Worth the trade for me, but does seem like a "bug" work-around.

---

### Post by cariboo on 2011-11-22
As Mark Phelps said, much depends on the graphics adapter your systems are using, I run Precis (12.04) on two systems, at the moment, there isn't much difference from 11.10, one system runs a GeForce 210, and the other uses the intel 945 graphics chipset, both run without any problems, and even Plymouth works properly. There are problems with AMD/ATI proprietory drivers, but many users are having no problems with the open source driver.

---

