---
title: "Distro for a iMac G3 with a 433 Mhz CPU and 128 RAM"
date: 2008-03-04
forum: Other OS Talk
---

### Post by Majin Zero on 2008-03-04
I wish I could find DSL or the PPC, but looks like it's x86 only...

I'd love to run Ubuntu but no way it would run well on this rig. It currently has OS 9.2

Any suggestions?

---

### Post by moephan on 2008-03-05
I think Yellow Dog is specifically designed for this scenario:
[http://www.terrasoftsolutions.com/products/ydl/](http://www.terrasoftsolutions.com/products/ydl/)

Cheers, Rick

---

### Post by stream303 on 2008-03-05
> **Majin Zero said:**
> I'd love to run Ubuntu but no way it would run well on this rig.

Come on over to the Apple PPC forum and we'll turn your G3 into something very useful - Xubuntu recommended.

Grab an **ALTERNATE** Power-PC install disk of Dapper 6.06.1 from one of the mirrors here and ring us up!

[http://www.xubuntu.org/get#dapper](http://www.xubuntu.org/get#dapper)

Burn the disk as an iso at a very low speed.

If you want to run a more up to date version of Xubuntu, but with less long-term support, you can get Feisty or Gutsy here:

[http://cdimage.ubuntu.com/xubuntu/ports/releases/](http://cdimage.ubuntu.com/xubuntu/ports/releases/)

You may have to manually edit your /etc/X11/xorg.conf file and change your Horizontal freq to 58-62, and your Vertical freq to 43-117.  You may have to disable DRI.  Not hard to do and we can walk you through it if it comes to that.

See you there!

---

### Post by Majin Zero on 2008-03-05
I did find the Xubuntu 6.04 for the PPC

I also found a Debian "business card" release

I'm going to try both of those.

To be honest, I'm lazy and I don't much feel like manually editing the xorg for the newer releases. But I thank you for the suggestions.

---

### Post by 3rdalbum on 2008-03-05
If you don't mind a bit of fiddling and a bit of learning, you could run NetBSD on it. Nice and lightweight.

I haven't tried it unfortunately; my G3 is still being used for production work by another family member :-(

---

### Post by Majin Zero on 2008-03-05
I considered it, but I'm partial to the whole linux scene for desktops.

I do like my BSD router and Server though.

---

### Post by stream303 on 2008-03-07
Good thing you have mac-os still on the hard drive.  You may be facing the issue of upgrading the firmware on ppc no matter what, although I haven't verified the need on Ubuntu.  I know you need it if you plan to run OSX 10.2+

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

NetBSD is great, although it still looks like they don't support G5's yet.

OpenBSD is another option.  Neither of these is immediately friendly to a new *nix user, although if you print out the docs and take it slowly with a cup of coffee, it is possible. :)  Great docs for sure with either one.

I'm not sure if either of these support smp yet either - best to check if you plan on BSD.

---

### Post by SunnyRabbiera on 2008-03-07
Debian is usually a good bet for all chipsets

---

### Post by stream303 on 2008-03-07
Debian is also a great alternative.

[http://ubuntuforums.org/showthread.php?t=701875](http://ubuntuforums.org/showthread.php?t=701875)

You can easily start with either Debian or Ubuntu and bounce back and forth with the skills you pick up.

It would be interesting to see if the need to manually edit your xorg.conf file for G3's exists in Debian as well - this would indicate that the real issue is coming even further upstream from xorg

---

### Post by khensucat on 2008-03-09
I actually have 7.04 running on an iMac 233 with only very slightly more RAM than yours, and it runs quite fine. As snappy as a freind of mine's Gutsy on a 2.0 Ghz P4 with 256MBram.

I'd say go for it. You may be pleasantly surprised ;-)

---

