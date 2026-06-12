---
title: "HP Sleekbook"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by anirbanghosh on 2012-12-31
I have heard that recent HP Laptops such HP ENVY and HP Sleekbooks are not allowing dual boot with Ubuntu alongside Windows 8. Is it true?

If yes, then what should I do then? Is there any way to fix this issue? I was preferring the AMD APU versions.

---

### Post by sandyd on 2012-12-31
> **anirbanghosh said:**
> I have heard that recent HP Laptops such HP ENVY and HP Sleekbooks are not allowing dual boot with Ubuntu alongside Windows 8. Is it true?

If yes, then what should I do then? Is there any way to fix this issue? I was preferring the AMD APU versions.

Not Exactly.
Chances are your computer has Secure Boot, but it is disableable in your BIOS (at least that is what it says in the Microsoft Windows Certification Requirements)

You probably want to have a gander through
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Especially the last part.

Happy New Year!

---

### Post by fantab on 2013-01-01
Yes, at the moment, it is as simple as disabling "Secure" boot from BIOS. But still we don't know what OEM like HP  has done under the hood to keep its consumers 'locked in' into a monopoly and impress the 'dictator'.

Just in case you are unable to disable this "secure" boot or want to dual boot Linux with Windows8 then there is an option. Read [**THIS**]("http://www.geek.com/articles/news/redhat-will-pay-microsoft-to-ensure-fedora-18-runs-on-windows-8-pcs-2012061/") and [**THIS**]("http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187").

Good Luck and...

Welcome to 2013.

---

### Post by anirbanghosh on 2013-01-01
> **sandyd said:**
> Not Exactly.
Chances are your computer has Secure Boot, but it is disableable in your BIOS (at least that is what it says in the Microsoft Windows Certification Requirements)

You probably want to have a gander through
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Especially the last part.

Happy New Year!

Just had a chat with HP. They told me I cannot install Linux alongside Windows. If I want to do it, I have to keep only Linux in my system.

---

### Post by sandyd on 2013-01-01
> **anirbanghosh said:**
> Just had a chat with HP. They told me I cannot install Linux alongside Windows. If I want to do it, I have to keep only Linux in my system.

You can if you disable secure boot in your bios, and use the instructions in my previous post.

---

### Post by ivicks on 2013-01-01
You could also install Ubuntu as a VM just make sure if you are using the 64 bit version of Ubuntu to enable hardware virtualization in your bios. I go this route on my desktop computer at work. Just another option I thought I would toss out there.

---

### Post by macpointman on 2013-04-06
I have gotten Ubuntu 12.10 installed on two of my lower end HP Pavilion G6 laptops (One AMD based and One Intel Based) to install just fine.  I haven't gotten grub to start up on boot as of yet.  This should be a simple fix with the Boot Fix utility that comes with the Ubuntu 12.04 LTS version.

If I hit the escape key as soon as the laptops screen flashes it will display the boot options screen.  From there you can choose to go to the BIOS settings or the Boot Device settings.  There it will list the options to list.  I choose the Ubuntu option on the Intel machine it has it listed twice for some reason.  I choose the bottom one and Grub loads and I am able to boot into Linux just fine.  On the AMD based machine only one option is listed, choosing it allows grub to load and Ubuntu to boot.

I am considering exchanging the AMD based Laptop for the HP Envy Sleekbook 6-1111NR.  The only problem that I have besides grub not loading at startup is these laptops the intel based and the Sleekbook both have the same Ralink 3290 WIFI adapter in them.  They are not supported out of the box by Ubuntu 12.10.  I understand that 13.04 will have support for this adapter but I have not been able to confirm that.  I have never had an issue with Ubuntu Linux not supporting a WIFI adapter out of the box.  The other problem that I have is getting the AMD drivers to work easily without complication is mostly a pain and takes a bit of work to get operating smoothly.

Ubuntu has come a long way in the past few years.  I enjoy using it a lot (Not so much the new UI) but it is these little things that make it hard to recommend to newer more non computer savy people.

---

### Post by macpointman on 2013-04-06
Sorry for the repost.  Edited from last message.

---

