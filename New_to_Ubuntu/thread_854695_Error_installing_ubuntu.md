---
title: "Error installing ubuntu"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by zomglolcats on 2008-07-09
Well, I've been trying to install the latest release of ubuntu and have not been successful. I've tried both the desktop and alternate installation but neither work. With the desktop installation it dumped me to the initramfs command line. Trying the alternate installation produced this error:

usb 2-1: device not accepting address 2 error -71

I don't understand this error, as I'm installing from CD, not a USB drive.

I currently have 32bit Vista Ultimate installed. I'm trying to install ubuntu to do a dual boot. I've installed a previous version of ubuntu on this very same computer once before, but I think I may have had XP installed at the time.

Any ideas?

---

### Post by lisati on 2008-07-09
The best I can come up with at the moment is that it's not the CD that's causing the errror:  Many  installers do some kind of check of what you have in your system, so they fine-tune their list of what to install, there is something about one of your USB devices is causing difficulty for the installer you are using.

---

### Post by zomglolcats on 2008-07-10
Well the only USB devices currently installed are my logitech quickcam, keyboard, and mouse. Also, these same devices were hooked up last time I had installed Ubuntu, so I have no clue what would have changed.

---

### Post by kansasnoob on 2008-07-10
OK, I have questions:

#1. Is there a "free" partition on the drive (for that matter do you have more than one hard drive)?

#2. If the answer to #1 is NO how are you trying to shrink Vista Ultimate?

If you're trying to resize Vista with Gparted, which is what the Ubuntu installer uses, it's GOOD you've failed!

You need to resize Vista with Vista's own tools!

[http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm](http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm)

---

### Post by kansasnoob on 2008-07-10
Oh ............... retro question: Does the Live CD run OK?

Not as an installer, just as "running the Live CD"?

---

### Post by zomglolcats on 2008-07-10
I have two hard drives. Vista on one, and was going to put Ubuntu on the other but it doesn't even let me get that far.

I couldn't get the Live CD to work, but maybe I was doing something wrong.

---

