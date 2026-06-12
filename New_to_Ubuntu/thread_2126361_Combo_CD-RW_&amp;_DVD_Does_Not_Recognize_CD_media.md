---
title: "Combo CD-RW &amp; DVD Does Not Recognize CD media"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by ac5jw on 2013-03-16
I want to solve my CD reader problem.  I am a Linux user for a few years now, but I am not very skilled on CLI Terminal yet.  I am learning a little about navigation and editing in CLI from readings.

I have a SONY DVD RW DRU-800A that will only detect and read and boot from DVDs.  I want to permanently configure it to detect, read, and boot from both CD and DVD media.

I seem to remember it performing this function in the past, but I have had problems with it since about January 2013, a time when I got click happy and removed a lot of Ubuntu software I did not want.  I noticed then that install/live CDs would not work on this computer, but it is possible that the problem existed already.

My SysInfo summary associates scsi0 with my DVD device, and also gives Linux OS with GCC version 4.6 (i686-linux-gnu).  The SONY DVD RW DRU-800A is also described in a 2004 sales document as CD-RW52D16B, 52x24x52+16 Black IDE Combo CD-RW & DVD.

I use Ubuntu 12.04.2 LTS installed from DVD.

What should I do to restore the CD read function?

---

### Post by ac5jw on 2013-03-18
I have been investigating a little about this problem.  It appears that I am seeing sg0 and sr0 device markers.  My Internet reading suggests that one is a character marker and the other is a block marker.  I also found a driver update for the device but it was not usable when I downloaded it.  I continue to investigate more about udisks and related commands.

---

### Post by ac5jw on 2013-03-29
I still have the same problem.  I did notice that my PC will not detect CD media nor floppy disk media when inserted into the drives.  So, the problem is now two drives for removable media.  I can use USB thumb drives with no problem.  I can also detect and read DVD media on the combo CD/DVD drive.

R

---

