---
title: "absolute beginner install problem"
date: 2016-07-23
forum: New to Ubuntu
---

### Post by dougwhitesides on 2016-07-23
I have a HP stream 7 that I tried to upgrade from Windows 8.1 to 10.  It failed and I am now caught in a maintenance loop.  I do not have the product key and have tried everything possible to no avail.

I downloaded Ubuntu on a flash drive and tried to install it on the PC with no success.  It says no drive available but I can get into the BIOS.  Please help

---

### Post by yancek on 2016-07-23
Your problem is with your upgrading windows and I'm quite sure you would have better luck doing a search at the microsoft or some windows forum.
Why do you not have the product key?  It's stored in the registry on your windows machine and is difficult but not impossible to get.  Your circumstances now, being unable to boot windows make it impossible, at least to my knowledge.
 
Are you able to boot Ubuntu and select the "Try Ubuntu" option?  If you can do that, open a terminal and enter the following command and post the output here:

```
sudo fdisk -l
```That's a Lower Case Letter L in the command.

What are your intentions?  Do you also want to install Ubuntu to the hard drive or are you just wanting to use it to recover your windows?  Also, most times when you get an upgrade failure, there will be some message indicating the reason although it may not be easily understandable for most users.  If you remember what it was , posting it would be helpful.

---

### Post by grahammechanical on 2016-07-23
It is a tablet. What version of Ubuntu are you trying to install? Standard desktop Ubuntu may not have drivers for the proximity sensor, the ambient light sensor or the Accelerometer. It may not have drivers for the WiFi or even the video adapter. Do not expect things to "work out of the box, " as people say.

The CPU is an Intel Atom but the big question mark is over the UEFI settings utility. Is it a 32 bit or 64 bit UEFI. You might also find that the 32 GB internal storage is actually 2 x eMMC cards in a RAID array.

If you succeed you will not be an absolute beginner anymore. This might help

[http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188](http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188)

As a complete an utter guess I would say that if Windows is broken then the files system might be trashed and in that state the Ubuntu installer cannot see a working disk drive. We know that both Windows 8 and 10 use hibernation to give fast boot times but with Windows hibernated the Ubuntu installer will see the drive in an unsafe state.

[https://ubuntuforums.org/showthread.php?t=2261294](https://ubuntuforums.org/showthread.php?t=2261294)

[http://askubuntu.com/questions/666285/installing-ubuntu-on-win-8-tablet](http://askubuntu.com/questions/666285/installing-ubuntu-on-win-8-tablet)

[https://www.youtube.com/watch?v=6WM4EfqcBQQ](https://www.youtube.com/watch?v=6WM4EfqcBQQ)

Regards.

---

