---
title: "error 30 and all kernels corrupted"
date: 2016-10-07
forum: New to Ubuntu
---

### Post by mercenarycor on 2016-10-07
So I've been wrestling all night with a crashed computer, and am now resorting to a complete reinstall of Ubuntu 16.04.  Yesterday I installed a large group of updates, including the .38 kernel.  Today, I went to turn on the computer and do my schoolwork, and after the encryption key screen, the screen went black.  After a significant amount of googling and forum surfing, I managed to figure out how to get into the command line (shift only works sometimes, why is that?) and the advanced boot menu so I could boot from the previous kernels.  Unfortunately, the problem continued across all the kernels I had, .31, .34, .36, and .38.  I then went into the command line and attempted sudo apt-get update, upgrade, dist-upgrade, --fix -missing, and a few more forum gems, before I realized that it kept giving me the message that the error 30, filesystem is read only.  I then proceeded to attempt the mount -o remount type commands, to no avail.  The system kept telling me that my hard drives were unmounted, and couldn't be mounted.  After deciding my attempts to repair what appeared to be a corrupted filesystem failed, I booted from my usb drive, and attempted to fix it from there.  The drives were shown as not having a /boot on them, and couldn't be opened.  At this point I decided something had gone terribly, terribly wrong and I needed a fresh install.

This brings me to my question: What possible causes are there for this series of unfortunate events?  I just finished building this computer about 3 months ago, everything on it is fantastic, and has been running great.  The system specs are:

AMD FX-8370 processor
AMD CAYMAN Raydeon HD 6970
240 GB SSD
2 TB HD
24 GB DDR3 RAM

The boot is installed on the SSD.  I'm running the 64 bit 16.04.  I've had some minor problems with the Raydeon built in support, but nothing that everyone else who plays Steam hasn't run into.  I recently was trying to hook up a HDD Docking station to pull files off some old hard drives, but I haven't even figured out how to get it to open, so I doubt that I could have corrupted it with that. I can't think of any other information that might be helpful.  I would like to figure out what went wrong so I don't end up having to wipe all my files again.  Thank you!

---

### Post by oldos2er on 2016-10-07
Have you run a S.M.A.R.T. check on your hard drive? 

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by mercenarycor on 2017-08-08
i apologize for never responding,  no I didn't.  If it happens again I shall, but it's been ticking along smoothly since this incident.  I guess it was just a fluke!

---

### Post by oldos2er on 2017-08-08
Better late than never! 

You should run smartctl once in awhile, even on healthy disks. It's not perfect, but it may provide a heads-up if a disk is on its way out.

---

