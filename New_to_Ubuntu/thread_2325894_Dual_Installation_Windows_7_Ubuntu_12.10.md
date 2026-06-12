---
title: "Dual Installation Windows 7/ Ubuntu 12.10"
date: 2016-05-26
forum: New to Ubuntu
---

### Post by davidkyoon on 2016-05-26
I have a dual installation. When I start with Ubuntu, my wireless hardware switch key does not work. I frivolously input wireless information under VPN. So is there a way to connect to the internet despite this issue?

The installation guide mentioned that it would lead/assist in connecting to the internet. It did not.
Pressing the switch while in Ubuntu does not work. And the switch key does work in W7. 
I am a brand new user of Ubuntu and do not have a computer science background, period.

---

### Post by grahammechanical on 2016-05-26
> do not have a computer science background, period.

Neither do I. With or without a full stop. But I can tell you this. Ubuntu 12.10 reached end of life May 16th 2014. Each version of Ubuntu has its own set of software repositories. And the software repositories for Ubuntu 12.10 are now closed. You will not be able to update 12.10 to receive security fixes or install any software. Including Wireless drivers if they are needed.

If the hardware on that machine is newer than Ubuntu 12.10 (October 2010) then the OS mostly likely will not have hardware modules for the hardware. Do not expect a WiFi hardware switch to work in Ubuntu. This is because Ubuntu has not been pre-installed on that machine and the manufacturer has not cooperated with the Linux developers to make sure that all the hardware works as users would like.

If WiFi is turned off in Windows, then it will remain turned off when Ubuntu is running. This is a fact of life when dual booting with Windows on laptops.

You should install a newer version of Ubuntu. That will be either 14.04 or 16.04. If you need advice on how to install and still dual boot with Windows 7 we can give it.

Upgrading Ubuntu over the internet is possible but not so easy when the version we are using has reached end of life and there are 4 more end of life versions in between 12.10 and the next supported version of Ubuntu (14.04). It all increases the risk of something going seriously wrong and forcing a fresh install anyway.

Regards.

---

### Post by roger_1960 on 2016-05-26
Hi

So, to summarise:

Whenever you exit windows, leave the hardware switch "on".  It will still be on when you boot into Ubuntu. You can turn wifi on and off in ubuntu using network manager (software) in the panel at top right. This should work in all Ubuntu versions...and yes, you should install a new version.  The install procedure should let you replace your existing Ubuntu and leave windows.  Remember to back up everything before you do this in case it goes wrong.

---

### Post by davidkyoon on 2016-05-26
Well that was also something that I read However it is also something I tried and it did not work. Perhaps it is something that works on other versions, which I have decided to install. Thank you for your time gentlemen it has been a pleasure

---

