---
title: "dual booting with windows 7 on raid drive"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by codetemplar on 2014-08-30
Hi all,

First of all apologies for yet another dual boot with windows question, you must be sick of them :) 

I have an aspire s7 ultrabook that was originally installed with windows 8. I am not very hardware savvy but decided to nuke it and install ubuntu 14.04 instead.. I had lots of fun attempting installation and lots of failures but eventually had success by disabling raid and uefi. Now I am only using 64gb of my 128gb raid drive and want to install win7 pro on the unused 64gb partition mainly as a gaming os.

As it was such a pain in the nether regions installing ubuntu I want your advice before installing win7 in case I do something wrong and have to start all over again.

First of all will win7 insist on blasting over my mbr and will I then have to manually install grub? If so is there any preparation I can do before hand to see a) where grub is currently installed and b) any config settings I can back up and just reinstall next time round? I assume it wont be an exact copy because it will also need to be able to boot win7.

Secondly is what I am planning to do with dual booting my raid drive safe? When originally trying to install ubuntu I read that the raid drive on the aspire s7 was unique in that it wasn't an actual raid drive but something similar which is why I was having suck issues. Unfortunately I didnt understand what they meant by this so I cannot elaborate. I also can no longer find that info.

Thanks for any help

---

### Post by whitesmith on 2014-08-30
> **codetemplar said:**
> Secondly is what I am planning to do with dual booting my raid drive safe? When originally trying to install ubuntu I read that the raid drive on the aspire s7 was unique in that it wasn't an actual raid drive but something similar which is why I was having suck issues. Unfortunately I didnt understand what they meant by this so I cannot elaborate. I also can no longer find that info.

You're probably thinking of fake raid. See [http://en.wikipedia.org/wiki/RAID#Firmware.2Fdriver-based_RAID](http://en.wikipedia.org/wiki/RAID#Firmware.2Fdriver-based_RAID)

---

### Post by codetemplar on 2014-08-30
Yes I believe I am referring to fake raid. Am I able to do what I am planning to do using fake raid? As I said I've disabled raid through the bios

---

