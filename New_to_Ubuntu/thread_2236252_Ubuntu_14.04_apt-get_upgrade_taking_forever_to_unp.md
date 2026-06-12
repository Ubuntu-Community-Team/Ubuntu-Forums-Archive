---
title: "Ubuntu 14.04 apt-get upgrade taking forever to unpack"
date: 2014-07-25
forum: New to Ubuntu
---

### Post by katelyn2 on 2014-07-25
I have been running Ubuntu 12.04 (dual boot with Windows 7) on my Dell Inspiron Laptop for 2 years.  Two weeks ago I did updates (that may not have completed?) and upon reboot, got "no such partition" and "grub rescue".  After trying everything I could find online, I was able to get it to boot into Ubuntu once again, but extremely slow.  I backed everything up to an external hard drive(which took forever, like 40Kb/sec), tried to install updates again, and again no boot.  I then tried upgrading to 14.04 from a live USB, but it hung overnight at some point, so I quit it.  I then tried deleting the ubuntu partition with gparted from a live USB and recreating the partition and fresh installing either 12.04 or 14.04 and every time it hung at copying files (it didn't exactly stop but went super slow and looked like it was giving errors, I'm talking hours).  Finally I tried using boot-repair from a live USB and restoring MBR, which successfully repaired the windows boot (so I could boot into Windows).  Then a fresh install of 14.04 went fine (20 minutes).  I selected not to install updates or 3rd party software at the time.  However, when restarting, I still got "Operating System not Found".  I did boot repair again (on grub this time).  It didn't boot the first 2 times after this, but it did boot the third time.  I ran sudo apt-get update (worked fine) and sudo apt-get upgrade, but now it has been (very slowly) unpacking packages in the upgrade since last night (12 hours?).  I'm not sure what the problem is.

I also did a diagnostic test and everything in my hardware passed except the battery (expected this).

I could just hard shut down, wipe 14.04, and do the process over with 12.04, perhaps that would help?

Thanks!

---

### Post by katelyn2 on 2014-07-25
I decided waiting was not going anywhere, so I restarted using Alt+PrntScr+r+e+i+s+u+b. As expected, it didn't boot, so I booted a Live USB and deleted the partition and remade a blank one again. I then tried to again fix the windows boot, but after three tries, it still won't boot into windows. These are the urls from the boot repair:

[paste.ubuntu.com/7857843/]("http://paste.ubuntu.com/7857843/")
[paste.ubuntu.com/7858194/]("http://paste.ubuntu.com/7858194/")
[paste.ubuntu.com/7859151/]("http://paste.ubuntu.com/7859151/")

Still when I try to boot from the hard drive, it says "Operation System not found".

Not sure what to do.

---

