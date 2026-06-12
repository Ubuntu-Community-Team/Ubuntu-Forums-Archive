---
title: "Want to try Ubuntu again - Dual Boot - 2nd drive"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by steven424 on 2013-05-31
Hi,

 I would like to install Ubuntu on a spare 38GB IDE hard drive and dual boot from my SATA windows drive.
Being new to Ubuntu is this possible or am I looking for trouble. I want to install Ubuntu 12.04 LTS as it is my understanding that it is the most stable version of Ubuntu out there especially for a new user such as myself.
I have tried Ubuntu before but had too many problems trying to get my printer installed. I am presently running windows XP and have no desire to upgrade when it is no longer supported next year and feel it's time to learn Ubuntu,

I am not sure how to do this but I am assuming that the Ubuntu loader must give me a choice as to what drive I want to install to without wrecking my windows drive.

Thanks,
Steven

---

### Post by WB0HYQ on 2013-05-31
Good luck, Stephen.  I tried it just yesterday (seems like a long time ago) and so far nothing has gone right.  I tried to install to an external USB drive of 1.5TB after partitioning it roughly in half.  The install went fine, but the dual-boot just isn't happening.  See my thread [here]("http://ubuntuforums.org/showthread.php?t=2150045").

Maybe between this thread and mine we can puzzle it out.

Bill

---

### Post by ibjsb4 on 2013-05-31
Before you make the move, what are your computer specs?  CPU, ram, video

I ask because there are different flavors of ubuntu and some are designed to work better on older equipment.

---

### Post by Mark Phelps on 2013-06-01
The first thing you should do is boot from a LiveDVD of Ubuntu and see how well it detects your hardware and installs working drivers.  Anything that does not then work is going to range from trivial to difficult to impossible to fix.

Second thing is that, when you go to install Ubuntu, have only the target drive attached.  That will prevent accidentally installing the GRUB loader to the Windows drive and causing Windows boot problems as a result.

Once that is working, reconnect the Windows drive, but continue to boot from the Ubuntu drive, open a terminal and enter "sudo update-grub".  That will regen the default GRUB config file, adding an entry for Windows Loader. When you then reboot, you will get a GRUB menu screen.

---

