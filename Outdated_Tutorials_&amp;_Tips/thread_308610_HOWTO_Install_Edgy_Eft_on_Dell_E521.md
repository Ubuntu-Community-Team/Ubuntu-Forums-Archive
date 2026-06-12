---
title: "HOWTO: Install Edgy Eft on Dell E521"
date: 2006-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by madhadron on 2006-11-28
Like many others, I bought an E521 in hopes of a good Linux machine.  There were many problems.  Then I found [this]("http://forums.gentoo.org/viewtopic-t-519130.html?sid=9b51afcf70f00b3be59b2735704fc7d1") howto for Gentoo.

Some particulars: I have an NVidia video card, one of those glorious 27" flatscreen, and my mouse and keyboard are plugged into the USB ports on it.  Some people in the forums have reported trouble when their mouse and keyboard are plugged into the box itself.

Get the AMD64 desktop install CD for Edgy Eft, and boot from it.  When the initial screen to set boot options comes up, hit F6, and add the following to the end of the line (after the --):

noapic pci=nomsi

Then boot.  You will get the Ubuntu splash screen.  The progress bar going back and forth is a little messed up, but it works fine.  This stage persists for a couple minutes, so don't get edgy.

Install Ubuntu as normal.  The install automatically added those options to my grub configuration as well, so I didn't have to change anything.  Then you'll probably want to go install envy from [here]("http://albertomilone.com/nvidia_scripts1.html") to get your NVidia card running at top speed.

Everything appears to work: monitor, sound, networking.

---

