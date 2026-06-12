---
title: "Problem with dual boot working"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by waltd on 2013-01-26
I have Windows 7 already installed.  For a few weeks I booted Ubuntu with a LiveUSB.  I was able to save items with persistent memory.  All worked will.
 
From the LifeUSB I did a dual boot install.  I followed the default settings during the install.  Also I have a USB 2.0 hard disk drive connected to a USB 2.0 port.  By default the space partitioning and install with to the USB HDD and not to my PC's drive.  Windows 7 is able to recognize it's part of the USB HDD when I'm in Windows 7.
 
Here is the problem.  There is no automatic choice on what OS to boot up in.  So I boot into my BIOS and choose.  I choose what appears to be the USB HDD.  I get a choice to boot in Ubuntu, Ubuntu Safe Mode, and a few others.  When I boot into Ubuntu I get a blank screen for a long time.  Then I get some text messages.  It appears that the boot up can not recongnize this HDD, maybe, I'm not sure.  Here are some of the error messages:
  
"Gave up waiting for root drive
Boot args (cat/proc/cmdline)
-check roog delay= (did the system wait long enough)
-check root= (did the syttem wait for the right device).  
  
By default my PC automatically boots in Windows 7, but I can't seem to the Ubuntu boot to work. 
  
Any suggestions?  Ideas?  Fixes?  Thanks you.

---

### Post by waltd on 2013-01-26
I found an answer to my problem.  Here are the steps I took.  
1. I created another LiveUSB using UNetbootin. 
2. I clicked on the install button. 
3. The install procedure saw that my previous install was broken and gave me two choices:  "delete Ubuntu" and "Reinstall/fix Ubuntu". 
4. I choice the reinstall.  The reinstall fixed everything and all is good now.  I now have a successful dual boot.

---

### Post by frank604 on 2013-01-26
Great to hear your problems were solved.  Should edit the topic name and add [SOLVED] so that people know this is no longer an issue.  :)

Happy Ubuntu-ing

---

