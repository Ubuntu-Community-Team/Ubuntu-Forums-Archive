---
title: "Ubuntu, Installed ON a USB flash drive has stopped Booting"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by 55Peace on 2013-07-10
Greetings! I installed Ubuntu 13.04 on a 64 Gig USB3 Flash drive and ran it from there successfully for many months. Suddenly it will not boot! My computer is an HP ProBook 4440s, 4 gib ram, 64 bit processor. Win7 is installed on the HDD. My usual procedure for boot was: With the computer off, insert USB drive, power on the box. Then I would see the fingerprint recognition screen, after recognition the usual grub boot options and I was off and running after I selected 13.04. Now the computer powers on and nothing happens. No fingerprint recognition, nothing. The USB is a Patriot Rage. Can any body Help? This is not a dual boot - all of everything Ubuntu is on the Flash Drive. Thanks in advance!

---

### Post by dannyboy79 on 2013-07-10
did you change anything in the BIOS? is there a function key you can press so a menu appears to choose which device it boots? are you certain the usb device wasn't changed? what does the partition table look like on the usb stick? can you boot up a live cd maybe and issue a

```
sudo fdisk -l
```
to view the partitions on the usb stick?

---

### Post by farrinux on 2013-07-10
Boot into win and then insert the thumb drive in and see if it is recognized.  If it does not it could be that the thumb drive is the problem.  They can go bad.

---

### Post by oldfred on 2013-07-10
Windows may see flash drive, but not Linux partitions. It will probably offer to reformat it, so do not do that.

If you boot with your Ubuntu install media DVD or flash and plug it in what does this show?
dmesg | tail
       lsusb

---

### Post by farrinux on 2013-07-10
Actually it works just fine to plug your ubuntu thumb drive into windows. I have mine setting on my netbook booted into win xp as I type.It does show the linux files. This is because the stick is formatted in fat 32.  The way it was from the manufacturer.  It stays that way when you make a bootable ubuntu install drive.  I have several.  It should be fine to plug it into windows just to see if it is functioning.  Outside of that you will need another ubuntu or linux machine to diagnose that stick.  As mentioned above try using a live cd to get into ubuntu and check your thumb drive.

---

### Post by oldfred on 2013-07-10
It it is an installer or liveUSB then it will be FAT32, but if a full install, it will be Linux formated.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by 55Peace on 2013-07-11
The cause of the Failure was apparently the flash drive. I tried most of the suggestions prior to posting and booting a live cd did show the Flash drive - but not any more! With some fiddling I got Win 7 to see the drive, but it would not do anything with it - including offering to format it, which it had done before. Thanks for the help! Now lets see if the manufacturer honors the warranty...

---

### Post by 55Peace on 2013-07-11
It was a full install ext3 fs unknown to win 7 and again thanks all!

---

### Post by sudodus on 2013-07-11
Pendrives with flash memory are not expected to take as many writes (on a specific memory cell) as HDDs. So when you install a system on a pendrive, you should add the option ***noatime*** in /etc/fstab to decrease the writing. You should also avoid regular use of a swap partition on the pendrive (to have it available for rare occations is OK).

SSDs have a system to change memory cell locations to spread the writes, to avoid repeated writing to the same few memory cells until they break. SSDs and HDDs also have extra memory space to use instead of worn out cells. This is managed automatically. I saw a test report, that a pendrive lasts much longer than before (and expected), so *maybe* this technology is also coming to pendrives, at least high quality pendrives, *maybe* it is simply longer lasting flash memory.

---

