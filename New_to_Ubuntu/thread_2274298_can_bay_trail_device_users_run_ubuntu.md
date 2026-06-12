---
title: "can bay trail device users run ubuntu?"
date: 2015-04-19
forum: New to Ubuntu
---

### Post by sms2 on 2015-04-19
Hi, absolute noob here, pls bear with me

I have hp stream 7 tablet, used the ubuntu 14.10 iso image, did not install, simply booted using this image on bootable usb, results were less than stellar. I followed one of the extremely few tutorials for booting ubuntu on bay trail 

The start up screen was chock full of weird bizarre errors, took ages to start, did not detect wifi and got buggy and slow to the point that I had to do hard shutdown. Hardly an enviable first time experience. 

what can I do to properly run ubuntu on my device??? Cant stand the idea of being stuck to windows only, wanna use open source OS as well.

---

### Post by grahammechanical on 2015-04-19
Do not take me for an expert but here is the problem as far as I can tell,

Machines that have a 64 bit CPU usually have a 64 bit UEFI boot system. This does not cause problems with 64 bit Ubuntu or other Linux distributions. Now,  these Intel baytrail/Atom machines have a 64 bit CPU but also a 32 bit UEFI boot system. This does not mean we can use 32 bit Ubuntu. No, we cannot because 32 bit Ubuntu cannot easily install in UEFI mode.

> To install Ubuntu in UEFI mode: 

Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555)

[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)

[https://sturmflut.github.io/linux/ubuntu/2015/01/21/installing-ubuntu-15.04-on-baytrail-tablets/](https://sturmflut.github.io/linux/ubuntu/2015/01/21/installing-ubuntu-15.04-on-baytrail-tablets/)

[https://www.change.org/p/tablet-makers-fix-the-lack-of-64-bit-firmware-on-early-bay-trail-tablets](https://www.change.org/p/tablet-makers-fix-the-lack-of-64-bit-firmware-on-early-bay-trail-tablets)

Note the comment in the bug report, It is not a bug but a consequence. The consequence coming from manufacturers using a 32 bit UEFI code on a machine with a  64 bit CPU and not 64 bit UEFI code on 64 bit CPUs.

[http://ubuntuforums.org/showthread.php?t=2261294](http://ubuntuforums.org/showthread.php?t=2261294)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944)

[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)

Now, I have seen lots of comments from people who think that fixing stuff like this must be surely easy and they say so. Developers have an expression. It is "low hanging fruit." It means that developers like to fix easy stuff. If things like this are not quickly fixed it is because they are not an easy fix.

Here is a blog from Matthew Garret who used to work for Redhat and did a lot of work to overcome the problem of secure boot in Linux. Note this comment

> Having looked into what it'd take to implement it in Linux, I decided  that hammering rusty nails through my feet would be a preferable use of  time. Thankfully, I went drinking instead.


[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

Regards.

---

### Post by Geoffrey_Arndt on 2015-04-19
The current list of tablets that will run Ubuntu is limited.   I've read Nexus tablets are among the few compatible.   Ubuntu has so far put it's efforts into Ubuntu Phone, the Desktop/Laptop, Servers and is a leading Cloud software provider . . . tablets probably another year or two away at best . . . as Canonicals "Convegernce" coding becomes stable.   Knowing theUbuntu community, I'm sure some techies could get the install done . . . let's see if other can provide more info.

[http://askubuntu.com/questions/163755/what-are-some-tablets-that-can-run-ubuntu](http://askubuntu.com/questions/163755/what-are-some-tablets-that-can-run-ubuntu)

---

### Post by Geoffrey_Arndt on 2015-04-19
Here's a developer link re installs of Ubuntu for phone or tablet devices.   I may try this out on an older Toshiba Thrive (don't care if device bricks, it's basically an older unsupported Android POS - no more Toshiba for me).

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

---

### Post by sms2 on 2015-04-19
> **grahammechanical said:**
> 



Now, I have seen lots of comments from people who think that fixing stuff like this must be surely easy and they say so. Developers have an expression. It is "low hanging fruit." It means that developers like to fix easy stuff. If things like this are not quickly fixed it is because they are not an easy fix.

Here is a blog from Matthew Garret who used to work for Redhat and did a lot of work to overcome the problem of secure boot in Linux. Note this comment



[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

Regards.

many many thanks , but ummmmm......

I take from these ominous sounding phrases that I may probably NEVER get  problem free ubuntu up and running on my hp stream 7 because of the 32 bit uefi. mathew garret has thrown in the towel on this issue :( gulp :(

i have googled this topic a lot, hardly any success stories and one or two cases that purport to be successful, i guess they are just bluffing. shocking.

so basically i m doomed:confused::cry: right???:shock:

---

### Post by mörgæs on 2015-04-19
Have you tried 15.04?

---

### Post by cariboo on 2015-04-19
I'm using a bay trail based notebook here, I've installed Vivid (15.04) in UEFI mode, with zero problems.

---

### Post by 28362836a on 2015-09-10
> **sms2 said:**
> many many thanks , but ummmmm......

I take from these ominous sounding phrases that I may probably NEVER get  problem free ubuntu up and running on my hp stream 7 because of the 32 bit uefi. mathew garret has thrown in the towel on this issue :( gulp :(

i have googled this topic a lot, hardly any success stories and one or two cases that purport to be successful, i guess they are just bluffing. shocking.

so basically i m doomed:confused::cry: right???:shock:
Getting Ubuntu to run on Bay Trail based X86-64 tablets is NOT impossible, it is simply very difficult and involves several workarounds. I wrote a (semi) simplified guide [here]("http://askubuntu.com/questions/619872/installing-ubuntu-14-10-64-bit-on-a-windows-8-bay-trail-atom-tablet") on how to do exactly as you were asking. You indicated above that you have already tried multiple guides without success, but I can assure you that I am not bluffing. Ubuntu does not retain full functionality when installed on Bay Trail hardware (Tablet-specific, because most Bay Trail based laptops can run Ubuntu/Linux fine). For instance, some tablets have compatible WiFi hardware, while others don't... but instead have compatible touch capabilities.

If you followed my guide, and did not successfully boot/install Ubuntu, then either your tablet is simply not hardware compatible, or you accidentally missed one of the steps (I swear I'm not trying to be rude, but I've had people do that before, during the install).

---

