---
title: "Cannot install Ubuntu or get past Grub"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by Lao_Ding on 2014-06-15
I am a COMPLETE newbie to Linux (switching from Mac). I bought a 2011 Samsung R428, downloaded 32 bit Ubuntu 14.04 .iso and burned away. The software did install a boot choice and GRUB functionality but the disk won't mount (some Casper error). I'd like to give more information but I don't even know what to look for. TIA. : )

---

### Post by Odyssey1942 on 2014-06-15
This may be the blind leading the blind, but it might be helpful to know a bit more about your setup. 

What is a "Samsung R428"? I assume a computer, if so what O/S did it have installed?

How did you download 14.04 (to the Samsung R428 or another computer)?

Once d/l'd, what did you do with it.? (D/l'd file needs to be burned as an ISO to a DVD, so if you just tried to run the d/l straight from a hard disk, I think this will not work.)

From what you posted, I assume that this will be a 14.04 installation only, not a dual boot, but please advise if otherwise.

With this info, I might be able to shed a little light, but most certainly others will be able to help out.

---

### Post by yancek on 2014-06-15
I'm not sure what you did to get the error you got.  casper is the name of a directory on the Ubuntu Live CD/DVD which contains the kernel and initrd files.  When you install Ubuntu to a hard drive, there is no casper directory.  I'm not sure what you mean by 'the disk won't mount'.  What disk?  Are you actually able to boot Ubuntu?  Do you see a Grub boot menu with options to boot Ubuntu?

The steps involve first downloading the iso image.  Before you burn it to a DVD (it's too large for a CD), you should do an md5check.  Instructions should be on the download page.  When you burn it to the DVD, make sure you select the option in the burning software to "burn as an image".  You then put the DVD in the drive and set your system boot priority to boot from the DVD.  I would suggest you review the link below at the Ubuntu site which gives some brief instructions on installing:

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---

### Post by sandyd on 2014-06-15
> **Lao_Ding said:**
> I am a COMPLETE newbie to Linux (switching from Mac). I bought a 2011 Samsung R428, downloaded 32 bit Ubuntu 14.04 .iso and burned away. The software did install a boot choice and GRUB functionality but the disk won't mount (some Casper error). I'd like to give more information but I don't even know what to look for. TIA. : )

Hi, have you checked the md5sum of the iso? See instructions at [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

If you want to make sure that your ubuntu iso is downloaded without being corrupted, try downloading using torrents instead.

---

