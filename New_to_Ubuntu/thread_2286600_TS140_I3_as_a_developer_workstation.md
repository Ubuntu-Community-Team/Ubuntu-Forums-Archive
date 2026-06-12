---
title: "TS140 I3 as a developer workstation"
date: 2015-07-13
forum: New to Ubuntu
---

### Post by ross_hunter on 2015-07-13
Hi all,  

My employer wants me to recommend a workstation to buy from PC World (only this shop allowed) that will be good for me to develop PHP based apps/run Virtualbox etc.  I will want to use the Ubuntu GUI desktop, and I want as little issues with setup as possible - such as device drivers etc.

The budget is around £500
I am thinking of buying this: [http://www.pcworldbusiness.co.uk/catalogue/item/P190011P?from=category&heat=title](http://www.pcworldbusiness.co.uk/catalogue/item/P190011P?from=category&heat=title)
Leonovo Ts140.

Can you confirm:
- this is the one of the best, economical options for minimum fuss setting up drivers etc, post install of latest ubuntu LTS?
- this machine will run Ubuntu desktop GUI

Thanks in advance!

---

### Post by grahammechanical on 2015-07-13
It is not the newest of hardware is it? But from a certain view point that is a good thing. It means that there is a high probability that the Linux developers have caught up and provided drivers for that hardware.

With very new video hardware I would be concerned that there were no drivers for it. Drivers for Intel graphics usually come as Linux modules. Here is a test report showing how well Intel HD Graphics 4600 performs using Ubuntu 14.04 as the OS. The CPU used is more powerful and an Intel driver from a PPA is being used But this report is more than a year old. And Ubuntu 14.04.2 now has Kernel 3.16 and mesa drivers version 10.1. So, I do not think that you will need to install any video drivers. It should all be done as part of the installing of Ubuntu.

[http://www.phoronix.com/scan.php?page=article&item=intel_hd4600_mesa101t&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_hd4600_mesa101t&num=1)

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

> By default, the 14.04.2 point release will ship with a newer [3.16]("https://launchpad.net/ubuntu/+source/linux-lts-utopic") Linux kernel from Ubuntu 14.10, and a matching X.org stack.

> The Xorg display server and drivers have been updated to the 15.0.1 release and mesa has been updated to 10.1. 



By the way, at the end of July we will be getting 14.04.3 with an even newer kernel (3.19).

Regards.

 




[URL="https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes"]
[/URL]

---

