---
title: "Error: attempt to read or write outside of disk 'hd0'"
date: 2014-08-03
forum: New to Ubuntu
---

### Post by lynyl on 2014-08-03
I have a Ratel Value from System 76, 64 bit, Intel Core 2 duo CPU E8600 @ 3.33 GHz x2, 3.9 GiB memory, Gallium 0.4 on AMD RV770 graphics, 153.2 GB hard drive, no partions, with Ubuntu 14.04. It is 5 years old. 

Even before the install of 14.04, I was having periodic boot up problems, so I had  all data on my external HD. Did the 14.04 install and it again booted up off and on - would have to do a hard shut down and cross my fingers and maybe . . . or not. And now the last two days, I can't boot and only get the message: 
Error: attempt to read or write outside of disk 'hd0'     Entering rescue mode . . .     grub rescue>   So I have done:

1. Fresh install (the second time) from a disk (had checked the disk per instructions so I saw I had files so assuming the disc is good)

2. Ran boot repair. Said problems corrected but could not boot correctly (ie ran bus errors on screen - lots- but booted and worked good - except wouldn't respond to the restart or shut down buttons and I had to do a hard shutdown and then got the same error message on reboot.) 
                 **                                                    My BootInfoURL is     [http://paste.ubuntu.com/7947917](http://paste.ubuntu.com/7947917)**

I have done enough reading on the forums etc to know that this can be a formidable problem.  I am actually hoping that it could be something as simple as a failed hard drive, cuz I couldn't follow much of what was suggested in these posts to others!  So, anyway, thanks in advance for any help and just remember to make directions as explicit as possible, without assuming I know much background.

---

### Post by mooreted on 2014-08-04
You might want to get the Ultimate Boot CD:

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

And run a hard drive test. Do the advanced test to scan the surface of the hard drive to see if there are any bad sectors. There are several HD tests on the UBCD, I usually use the Hitachi test.

---

### Post by lynyl on 2014-08-04
Because I have only 1 CD drive which is now running the live CD, I will go to a friend's house and burn the CD & do what you suggested and get back to you.Thanks.

---

### Post by lynyl on 2014-08-05
Today I put Ubuntu 14.04 on a pen drive and then downloaded and burned Ultimate Boot CD and ran the hard drive check -hard drive not bad! So I then booted it up normal and for the first time got this: mount failed on sys/fs/selinux;no such file or folder and then I got the sign-in page with error messages showing and acting wacky, so I shut it down and booted from the cd. I  looked at the sys/fs/ and no selinux folder - so decided to re-install 14.01 again (3rd time!) And they say the 3rd times the charm - and it was! So for now working just fine and have shut down and rebooted several times. There's still no folder selinux in sys/fs  -  BUT IT"S WORKING! Here's hoping!

---

### Post by oldfred on 2014-08-05
Are you using 64 bit version?

Usually that issue is some partition table issue, but your partition table looks ok.

Is BIOS set for AHCI, not IDE?

Your system is new enough that the old BIOS limit of 137 GB should not be an issue. But if in IDE mode and using 32 bit install it may still be an issue. About half the time, just shrinking / (root) to less than 100GB and use rest of drive as /home or /mnt/data solves the issue. 
I normally suggest / be only 20 or 25GB with (in your case) rest of drive as /home or data partition(s).

Issue can appear after an update where partition is large and then one of the grub or boot files is rewritten beyond the limit.

---

