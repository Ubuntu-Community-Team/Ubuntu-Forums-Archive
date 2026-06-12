---
title: "How to backup a mounted Windows drive on laptop"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by jdallara on 2012-09-29
Hello:

  Have HP laptop that will not boot from its internal hard drive.  Booted using Ubuntu 12.04 ISO CD that I made and can mount the windows drive with no problem.  I also have an external USB drive mounted.  How do I backup the windows drive to the USB drive to: a. Save the applications and data that I have on the "dead" windows drive; b. Hopefully make a bootable USB hard drive that has all the original files from the windows drive so that I can boot off the external hard drive and use the windows applications that I have on the "dead" drive.  I can't seem to locate any applications on the Ubuntu desktop even though the Software Center says the programs are installed.  I can see the programs on /usr/bin but can't run them from there.  I've been away from Linux for around 10 years now and like the improvements that I see.  Previous to that I was a Un*x sys admin for 20+ years so I still do know my way around a little bit.

Thanks,  Jon.

---

### Post by slooksterpsv on 2012-09-29
Hmmm you could dd the data but youll have to do a checkdisk after booting from the new drive.

e.g.: 

sudo dd if=/dev/sda1 of=/dev/sdb1

where sda1 is the windows drive and sdb1 is the backup drive. This can vary though. Otherwise you may find something in the repos.

I used dd to copy my tools partition on my hp then restored it when I needed it. Maybe someone has some better input

Oh the check disk will mark what free space there is as dd will consider the whole drive as used on whatever output you use. I believe it does a block by block copy

---

### Post by jdallara on 2012-09-29
Good idea, forgot about dd.  How do I open a term window?  I've got a row of icons down the left side of the screen but none that say "open application" or give a list of those available.  I'm an old command line user...

---

### Post by jdallara on 2012-09-29
Found gnome_terminal in /usr/bin after a bit of poking around, have command line now!  What was that command?  rm -rf *?

---

### Post by mips on 2012-09-30
Be VERY careful when using dd. If you have exiting data/partitions on the external drive of=/dev/sdb1 is gonna cause you a lot of grief & lost data.

What's wrong with the internal drive, describe the symptons in detail, behaviour, error messages etc etc

---

### Post by jdallara on 2012-09-30
Internal drive will not boot.  BIOS returns an error message #1 -07 fail on hard drive test (Phoenix BIOS).  Laptop will boot until it stops with a message saying the /windows/system32/.../system (or something close to that, I'm doing it from memory right now) is missing or corrupt.  I can mount the drive using Ubuntu and can see the file system.  The external drive has nothing on it so I can play with it without worry (already had dd reformat it to 60GB from 500GB on first try, oops) but dd fails with an input file error after copying 1800 or so blocks.  I'm going to partition the external drive so I can install Ubuntu on it so I can boot from it instead of the CD and then I'll try messing with the internal hard drive on the laptop using the NTFS utilities.

---

### Post by mips on 2012-09-30
> **jdallara said:**
> Internal drive will not boot.  BIOS returns an error message #1 -07 fail on hard drive test (Phoenix BIOS).  Laptop will boot until it stops with a message saying the /windows/system32/.../system (or something close to that, I'm doing it from memory right now) is missing or corrupt.  I can mount the drive using Ubuntu and can see the file system.  The external drive has nothing on it so I can play with it without worry (already had dd reformat it to 60GB from 500GB on first try, oops) but dd fails with an input file error after copying 1800 or so blocks.  I'm going to partition the external drive so I can install Ubuntu on it so I can boot from it instead of the CD and then I'll try messing with the internal hard drive on the laptop using the NTFS utilities.

Imaging the partition across is not going to help you unless you want to recover the data and even this might not be successful.

Sounds like that drive has either file system corruption or hardware issues (maybe bad sectors). Open disk utility from ubuntu and check what SMART values are reported.

If the disk has bad sectors you are better off imaging it with gnu ddrescue instead of dd as it was designed to work with bad drives.

Good luck.

---

### Post by jdallara on 2012-09-30
Thanks for the pointers.  Didn't know about ddrescue.  I've got the installation ready to go to put Ubuntu on my external drive and then I'll try it.

---

