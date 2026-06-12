---
title: "Another grub error"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-09-11
Same issue as another person who posted recently about deleting the Ubuntu partition on a 14.04/W7 dual boot.  The advice was to try to boot from a live CD.  I have my USB installer that I've used on several other machines (and this one), but now this machine will not let me boot from it.  Upon starting the machine I get this:

[B]no such partition
Entering Rescue Mode
grub rescue[/B]

And a blinking cursor.  I can find no way to proceed with this.  This can't be an uncommon occurence; is there a known fix to get grub working again?  At this point, I have a brand new HD in the machine and am ready to start from scratch.  :(

Thank you!

---

### Post by grahammechanical on 2014-09-11
Did you also delete the Ubuntu partition like the other person you mentioned?

The Ubuntu live session does not use Grub. So, if you are getting a Grub rescue prompt it can only be because you are not loading the Ubuntu live session. Do you have another OS installed? If not then you will not see a Grub boot menu unless you hold down the shift key as the machine starts to load.

When we install Ubuntu each partition is given a Universally Unique Identifier (UUID). It is a long combination of alpha-numeric characters. Grub uses these UUIDs to know which partition the Linux kernel is on.

It seems that Grub is looking for a partition that does not exist. Is that the situation? If so, then indeed you need to start from scratch.

Regards.

---

### Post by riverguy99 on 2014-09-12
OK, here's where I am right now. A fresh, formatted HDD with nothing on it.  When I try to boot up, it does exactly the same thing as it did with the old drive on which I deleted the 14.04 partition. I get the same exact message when I just let it try to boot, when I change the boot sequence to the 14.04 USB install drive, or even with a Windows install disk in the CD drive.  But here's the goofy part that might be a good tip to you, since you know what the heck is going on here:  I just removed the HDD from an identical laptop that was configured the same as this one that's the problem.  I powered it up and it booted up just fine to both 14.04 and W7.

Is that any help at all?  Oh yeah, then I loaded a Macrium Image backup onto yet another old formatted HDD and installed it.  Didn't work.  Same issue as before.  It only likes the drive out of the other working machine.  So at least can we assume there's something wrong with the drive or the way it is formatted?  The fact that the working HDD works fine indicate that this is not an issue in the BIOS?  I do really need to install W7 first, since this needs to be a dual boot machine.

---

### Post by Pelvur on 2014-09-12
It sounds like it doesn't boot to your live USB. Try to boot to live USB from another machine, will it work? if not, rewrite it. 
I assume you've chosen to boot from USB first in your BIOS settings.

---

### Post by fantab on 2014-09-12
Have you checked the BIOS or UEFI settings for which 'disk' to boot first? Also, is USB boot 'enabled'?
Or f10/f12 (it could be different for you) lets you select your boot disk, should be used perhaps.

---

### Post by riverguy99 on 2014-09-12
I'm still working on this mess!  This machine works just fine if I install the HDD out of an idential unit.  But then if I install the culprit (newly formatted) HDD into the machine that was working fine, it behaves exactly like the one that's giving me fits.  I'm tempted to just use the working HDD and toss the other laptop in the recycle pile, along with its new 500 GB HDD.  I've been three very long days at this!

Stay tuned!

---

### Post by fantab on 2014-09-12
The HDD could be corrupt, have you run SMART tests on it?
You can do the tests with the utility 'Disks' which you can use from Live Ubuntu.
[http://www.hecticgeek.com/2011/11/how-to-run-hdd-smart-tests-in-ubuntu-linux/](http://www.hecticgeek.com/2011/11/how-to-run-hdd-smart-tests-in-ubuntu-linux/)

Alternatively, you can use [Smartmontools]("https://help.ubuntu.com/community/Smartmontools") from command line if you need to see more detailed results.

If the tests fail, and if the HDD/laptop is in warranty, then perhaps you can exchange it...
Or you can get a new HDD, if that is an option.

---

### Post by riverguy99 on 2014-09-13
Thanks to all who have replied to this thread.  I appreciate your efforts! So I've narrowed down the issue to not being able to boot from a USB drive with a downloaded Ubuntu ISO.  Since this is a distinct issue without all of the variables discussed above, I will start a new thread on it.  I hope that this is the right thing to do?

The new thread:  Can't boot from downloaded ISO USB.

---

