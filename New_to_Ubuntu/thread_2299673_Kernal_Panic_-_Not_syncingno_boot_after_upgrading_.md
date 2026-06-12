---
title: "Kernal Panic - Not syncing/no boot after upgrading to 15.05"
date: 2015-10-20
forum: New to Ubuntu
---

### Post by w9jbl on 2015-10-20
I'm an Ubuntu beginner.  I had been using 14.04LTS for several months  because it had been promoted as a no-cost alternative to upgrading to a  version of Windows from XP. During that time, all my personal files,  including my T-bird emails were stored on Ubuntu.
  Recently during an update, Ubuntu suggested that I may want to  upgrade to 15.05, which I did.  Immediately after that, I tried to  re-boot into Ubuntu, only to find: "Kernal Panic - not syncing:  attempted to kill init!  exitcode =  0x0007f00" and the computer quit responding.
  I got as far as booting off of a Live CD, and trying the "Grub-repair", but it didn't work.  I got the same error screen.
  I'm afraid that if I re-install Ubuntu it will over-write all my stored data, documents, emails, etc.
  Please help me.  This Ubuntu/Linux thing is proving to be too  complicated for someone who tried to follow the suggestions from Ubuntu.   If I can't get this fixed, I'll be forced to abandon Ubuntu and get a  new version of Windows.
  My boot screen can be found at [http://paste.ubuntu.com/12875715](http://paste.ubuntu.com/12875715).
  My email address is <*snipped*>, which I can only access from  the Live CD by going to Comcast's web page and signing into their web  mail.
  Thank you.
  john leonard

---

### Post by ian-weisser on 2015-10-21
Boot from your LiveCD, go into 'Try Ubuntu', and backup all your data to some other disk or media before doing anything else.
Let us know after that is complete.
Fixing your problem is usually not difficult...after your data is backed up.
[EDIT] Skaperen's suggestions below are wise.

---

### Post by Skaperen on 2015-10-21
my suggestion ... after you backup all your data .. TWICE to 2 different places ... is to re-install 14.04 and just stay with it until 18.04 comes out.  this is my own plan.  during this time you can learn slick ways to make regular backups of your data and files (many tools to do this).  after you boot the live CD mount your main partition ... **[FONT=courier new]sudo mount -r /dev/sda1 /mnt[/FONT]** and look around in /mnt. find a storage device (or 2) big enough for your data, such as a USB memory stick or other external hard drive.  my laptop supports SD cards so i have two 32GB ones and make incremental backups to both.  USB memory sticks can be had WAY bigger if you need that.  if you have online backup space see if you can get on there from the live CD system.

---

