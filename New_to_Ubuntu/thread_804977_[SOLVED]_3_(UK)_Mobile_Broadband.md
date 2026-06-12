---
title: "[SOLVED] 3 (UK) Mobile Broadband"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by t0p on 2008-05-23
For a while now I've been using a cellphone as GPRS modem with my computer (currently running ubuntu gutsy). But the snail-like connection speeds that I get over GPRS are rather frustrating.

So, I've been thinking of getting mobile broadband service.  Most mobile phone networks offer the 3G internet service, but I thought I'd go for 3's service as it's available on Pay As You Go.

I emailed to ask 3 if the service was compatible with Linux. Unsurprisingly, the answer was "No".  Officially, it's compatible with Windows 2000, Win XP, Vista and OSX only.  But many products aren't "officially" compatible with Linux.  "Unofficially" the story is often quite different.

So: has anyone here tried the 3 mobile broadband service with an ubuntu box?  Was it successful?  Which USB dongle did you use?

And, while I'm asking:  what about other UK networks' mobile broadband services?  Which are compatible with linux, which not?  I'm sure I'm not the only person who's tried this...?

---

### Post by neurostu on 2008-05-23
I have never tried mobile broadband on linux but a simple google search for "Mobile Broadband Linux" yields a lot of results here are a couple:
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/872886.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/872886.html)
[http://www.emperorlinux.com/hardware/cellular/](http://www.emperorlinux.com/hardware/cellular/)
[http://www.tomshardware.com/forum/236344-50-mobile-broadband-support-linux](http://www.tomshardware.com/forum/236344-50-mobile-broadband-support-linux)

Good luck and be sure to document what you do so you can share your results with others.

---

### Post by Kevbert on 2008-05-23
Probably your best bet is Sky, if you have Sky TV.  They provide a Netgear router which works fine with Ubuntu 7.10, 8.04, Kubuntu 8.04.  I'm not sure what wireless adapter it comes with as I have my own Belkin (Broadcom) wireless card.  Speed is up to 8Mb/s 15Gb/month for £60/year.
Alternatively, if you want to be mobile (very expensive), I believe it's possible to use Vodafone.

---

### Post by scorp123 on 2008-05-23
> **t0p said:**
>  So: has anyone here tried the 3 mobile broadband service with an ubuntu box?  You may wish to read this thread then :)
[http://ubuntuforums.org/showthread.php?t=609534](http://ubuntuforums.org/showthread.php?t=609534)

> **t0p said:**
>   Which USB dongle did you use?  Well, I am in Switzerland, so I am not a "3" customer. But I know 100% from first-hand that these USB dongles will work: [LIST]
[*]Novatel Ovation MC 950D (that's the one I have!)
[*]Huawei E220 [/LIST]

> **t0p said:**
>  what about other UK networks' mobile broadband services?  Which are compatible with linux, which not?   Again, I am not from the UK ... but based on my positive experience with my Novatel Ovation MC950D which I got from the Swiss provider "Sunrise" ([www.sunrise.ch](www.sunrise.ch)) a friend of mine got his from Vodafone UK. If we take a look at Vodafone UK's offers .... :
[http://online.vodafone.co.uk/dispatch/Portal/appmanager/vodafone/wrp?_nfpb=true&_pageLabel=template08&pageID=MB_0002&&WT_ref=INT-PSHOP-130208-MobBrdbnd-MBFindMore](http://online.vodafone.co.uk/dispatch/Portal/appmanager/vodafone/wrp?_nfpb=true&_pageLabel=template08&pageID=MB_0002&&WT_ref=INT-PSHOP-130208-MobBrdbnd-MBFindMore)

I am not so sure about the upper one ... might be a re-branded Novatel Ovation. But the lower picture (the oval-shaped modem) is without a doubt a  Huawei E220 and those are known to work with Linux ... Google will spit out plenty of how-to's if you search for "huawei E220 Linux" ...

---

### Post by t0p on 2008-05-24
Thanks scorp123!! A most helpful post!!  :)

---

### Post by becky232 on 2009-06-05
I've got a Novotel 950D broadband dongle-  from O2 - and I've tried it withOpenSUSE. It connects but it locks with about 250 bytes of throughput (original spec OpenSUSE 11.1)

I then tried putting Linux Mint 7 - a top of the range ubuntu deriviative - onto my laptop. A very different story. The preset configs worked just fine once I'd 'ejected' the 'ghost' disk that came with the dongle.... use 'sudo eject /dev/sr1' - and about 30 seconds later I was connected! This is good stuff - and while it's an Ubuntu deriviative, I'll be keeping it on the laptop as the standard 9.04 was problematic!

---

### Post by roaftech on 2009-06-06
I have been using the T-mobile version of the Huawei E220 dongle on Ubuntu 8.10 (wouldn't work on version 7) on both a desktop and a mobile.  Slow speed (c 200kps), but much the same as on my XP machine.
All was satisfactory until I tried installing 9.04, which has completely fouled up the whole machine.

---

