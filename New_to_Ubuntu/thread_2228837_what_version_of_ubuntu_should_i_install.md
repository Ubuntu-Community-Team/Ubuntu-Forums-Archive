---
title: "what version of ubuntu should i install"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by Matthew_Zepess on 2014-06-09
im new to linux, but want to give it a try. but i noticed the 32bit version is up to 2gb of ram. while my pc has about 3 and a quarter gigabytes. this pc is a older 32bit windows xp with what i think is a pentium 4. so should i install 32 and lose 1 and a quarter gigs or get 64. is there any problems or slowdowns with 64 bit linux on a older 32bit machine?

---

### Post by Matthew_Zepess on 2014-06-09
[COLOR=#000000]im new to linux, but want to give it a try. but i noticed the 32bit version is up to 2gb of ram. while my pc has about 3 and a quarter gigabytes. this pc is a older 32bit windows xp with what i think is a pentium 4. so should i install 32 and lose 1 and a quarter gigs or get 64. is there any problems or slowdowns with 64 bit linux on a older 32bit machine?[/COLOR]

---

### Post by Dale_Whitnall on 2014-06-09
32bit version will be fine with up to 4gb of memory, but 64bit will not run on a system that dosn't have a 64bit processor.
I would give the 32bit a try first.  Burn it to a disk or put it on a usb drive if you can boot from there, it will run without you having to install it gives you the option to try before you buy :)
Hope that helps

---

### Post by Paulgirardin on 2014-06-09
I'm using 1.8 GB of ram at the moment  with 14.04 64 bit on a Core2 duo system 4GB ram,with chromium browser open (6 tabs).
I would download the isos for Ubuntu,lubuntu and xubuntu and create bootable usb drives and test them on your system to check compatibility/speed.

---

### Post by sammiev on 2014-06-09
It really sounds like your computer is 32 bit. With that said I would likely try Lubuntu or Xubuntu. Try either or both of these on a USB stick live and see what works for you after a day or so of each. :)

---

### Post by LastDino on 2014-06-09
Some P4's are x64. Let us know the exact model number. And unlike windows, on linux 4GB works fine. With x32, however, you might not be able to use that much RAM for any single process, that's the advantage x64 has. But I doubt you will be using anything to use RAM beyond 1-2GB on that box, so worry not.

---

### Post by Vladlenin5000 on 2014-06-09
If you have at least 2GB RAM in a 64-bit capable CPU/chipset use 64-bit version.
If RAM is <2GB prefer 32-bit even if the hardware supports 64-bit.

The usable RAM limitation for a 32-bit OS is a Windows problem, not Linux. You won't 'loose' RAM in a 32-bit Ubuntu.
What Windows version it has now is irrelevant. OK, The machine CURRENTLY **has **a 32-bit XP; it tells us **nothing** about whether it supports a 64-bit OS or not. 

Anyway,
A full hardware specs list is a must. Nobody can (or should) suggest one or the other without knowing what's inside. Nevertheless, as a rule of thumb, if it has 2GB or more RAM -and- it did at some time run a 64-bit version then choose that one also for Linux. It usually performs better but not so much in older hardware as I suspect yours is.

---

### Post by 3rdalbum on 2014-06-09
Some Pentium 4s and other CPUs of that vintage are 64-bit compatible. Look up your CPU model number and find out if it is 64-bit. If it is, run 64-bit Ubuntu; there is virtually no reason for you not to.

If your CPU is 32-bit you need to stick to the 32-bit edition. 64-bit won't run on a 32-bit CPU.

A 32-bit OS can work with up to 4GB of RAM, not 2GB.

---

### Post by robin7 on 2014-06-09
My old fossil, with only 1/2 GB of RAM, runs Xubuntu beautifully and fast. Even on much more powerful machines it's gorgeous, polished, and sensible.

---

### Post by cariboo on 2014-06-09
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Matthew_Zepess on 2014-06-09
dont really know the specs. but i have about 50 more blank dvds, should i download both and see if i get a error.if i dont like 64 i can do a clean wipe to 32????

---

### Post by sammiev on 2014-06-09
> **Matthew_Zepess said:**
> dont really know the specs. but i have about 50 more blank dvds, should i download both and see if i get a error.if i dont like 64 i can do a clean wipe to 32????

When you try a live edition you do not install you just test or try. What works for you and what your happy with is what you can use.

---

### Post by Matthew_Zepess on 2014-06-09
just looked and the desktop is a[TABLE="width: 100%"]
[TR]
[TD][HP Compaq dc5100 Base Model SFF PC]("http://h20180.www2.hp.com/apps/Nav?h_product=473256&h_client=S-A-r163-3&h_lang=en&h_cc=us&h_pagetype=s-001&ssf=1") [/TD]
[/TR]
[/TABLE]

according to the hp scan, i got it used, and have put more ram/ new hard drive/ and a dvd drive

---

### Post by Matthew_Zepess on 2014-06-09
> **sammiev said:**
> When you try a live edition you do not install you just test or try. What works for you and what your happy with is what you can use.
look up the specs of the pc and give a opinion on what i should install

---

### Post by sammiev on 2014-06-09
> **Matthew_Zepess said:**
> look up the specs of the pc and give a opinion on what i should install

This is what I see with your info.

---

### Post by Vladlenin5000 on 2014-06-09
> **Matthew_Zepess said:**
> just looked and the desktop is a[TABLE="width: 100%"]
[TR]
[TD][HP Compaq dc5100 Base Model SFF PC]("http://h20180.www2.hp.com/apps/Nav?h_product=473256&h_client=S-A-r163-3&h_lang=en&h_cc=us&h_pagetype=s-001&ssf=1")[/TD]
[/TR]
[/TABLE]

according to the hp scan, i got it used, and have put more ram/ new hard drive/ and a dvd drive

Thank you for posting the details. So... We already know HP never supported 64-bit OSs for that model but that doesn't mean the machine itself isn't capable of supporting it. The CPU may support it but you also need a compatible mainboard's chipset. Yours should be a Intel something circa 2004/5. Definitely NOT looking good for a 64-bit experience, I'm sorry :cry:

---

### Post by DuckHook on 2014-06-10
> **Matthew_Zepess said:**
> look up the specs of the pc and give a opinion on what i should installYour biggest decision is not 32 vs 64 bit. This can easily be settled by just trying a 64-bit LiveDVD. If it doesn't run, it doesn't run, and you have your answer.

The bigger decision is what flavour of 'buntu is best, and whether you should even be considering any of the 'buntu flavours at all.

I'm an old HW hound and have revived many a glorified doorstop back to a functioning and usable machine. In my experience, a P4 is simply too underpowered for you to be happy with anything but Lubuntu or Bodhi, and maybe not even then. It doesn't matter how much RAM you have or how big your HD is. The bottleneck will be the processor. You may be better off with CrunchBang, Tiny Core or Slitaz. These distros are not as "full featured" as the 'buntus, but they still have amazing little apps that make old boxes young again. Most of all, they have been stripped down to very tiny and efficient kernels that won't overly tax your CPU. The other option is to run your box as a command-line-only server of some sort, but this is usually not practical with ordinary users. However, it's a viable option to keep in mind if you need nothing more than a file- print- torrent- time-server. Without the tremendous bloat and burden of a graphical overhead, your P4 could probably perform all four aforementioned functions concurrently.

I would recommend that you try CrunchBang, Tiny Core and Slitaz and see if you like them. If you really prefer to stick with the 'buntu family, try either the officially supported Lubuntu, or the unofficial but really cool (and even more lightweight) Bodhi.

---

### Post by LastDino on 2014-06-10
To add to above, that is to for anything below P4 2Ghz. I've P4 3.0Ghz on this very machine and I can run every flavor of Ubuntu and do the tasks mentioned quite easily, biggest problem generally seems to be on board graphics which are way too outdated to use Ubuntu Unity and Gnome 3. Of course, I've 4Gigs of RAM, so that also helps.

Your SFF has better processor than mine.
[http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12132708-12132884-12132884-12132884-12133128-12133130-64704643.html?dnr=2](http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12132708-12132884-12132884-12132884-12133128-12133130-64704643.html?dnr=2)

If this is correct, then feel free to install Xubuntu if you've more than 1GB RAM, if it is less, then Lubuntu is the way to go. But I would pick Bodhi over Lubuntu if I had to go down that road.

---

### Post by LastDino on 2014-06-10
Please post your exact model no. as there are lower CPU models too.

---

### Post by Matthew_Zepess on 2014-06-10
cant say the type of processor, but its a 2.8ghz. and this is my first time getting serious with linux, so is ubuntu the best for noobs???. will install 64 ubuntu and reply back later

---

### Post by DuckHook on 2014-06-10
> **Matthew_Zepess said:**
> ...so is ubuntu the best for noobs?A number of members have already pointed out that your video subsystem likely is very underpowered for Ubuntu. You will find that Xubuntu will perform acceptably and Lubuntu even better. And if you are coming to Linux from Windows, these two flavours have the added advantage of a menu structure that is more familiar to Windows users. But Linux is all about choice. Why not try out Ubuntu, as you are planning? It costs you nothing but some time and electrons to download, and then you can try as many distros and flavours as you want. You will quickly find the one that is the most comfortable and responsive for your needs.

---

### Post by DuckHook on 2014-06-10
I have the almost identical dc7600 w/ P4 HT @ 3GHz maxed to 4 GB and found the experience with Xubuntu limiting. My admittedly very unscientific test with processors of this type is to see if I can run a WinXP VM inside the box. With Xubuntu, the VM was noticeably sluggish and jittery. With Lubuntu, the VM ran more smoothly and responsively. A more critical measure was that lm-sensors reported higher temps under Xubuntu than Lubuntu. (A CrunchBang VM runs very nicely with either flavour, but for the average user, there's not much point to running a Linux guest inside a Linux host. As a further curiosity, running an XP guest inside a CrunchBang host gave the snappiest performance of all, but I'm digressing).

Of course, your experiences may be different. There's really no absolute right or wrong here. Lots of ways to skin this cat and Linux is the embodiment of choice. Ergo, my suggestion that the OP try all of these different distros.

---

### Post by loneTiger on 2014-06-10
Try the Lubuntu version - its specifically built for older systems with a nice GUI  easy to use especially if you are moving from a windows Os experience/knowledge base.

You can get General info here :  [http://lubuntu.net/](http://lubuntu.net/)     and also here  : [http://en.wikipedia.org/wiki/Lubuntu](http://en.wikipedia.org/wiki/Lubuntu)

the Latest version Release notes (ubuntu 14.04 LTS based) :[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/Lubuntu](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/Lubuntu)

And download it from here: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
also if you are having a really low end system with even less than 700 MB RAM the this is for you : (Alternate ISOs are for low-RAM PCs. Computers with less than 700 MB of RAM are considered low-RAM computers) : [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

I personally refurbished an old laptop for my church use with lubuntu (alternate install iso)( Dell satellite from 2004 specs: P4, 512 MB Ram, 30Gb HDD, previously running windows XP home - its now working beautifully with Lubuntu).

by the way if your system is 32 bit it will not install the 64 bit version.
and 32 bit is recommended version for older systems.
If your hardware is working "ok" (not even fine like for e.g.: some subsystems e.g. audio chip failed ) it will still work good & smooth. 

Hope this helps.

---

### Post by 3rdalbum on 2014-06-10
Ubuntu is a good general purpose choice, and good for new users. A very good place to start and maybe to stay on.

It's not particularly lightweight and it does pretty much need 3D acceleration, which may make it run a bit slowly on your computer. Something like Lubuntu would be a better bet if so.

Also, be aware that Ubuntu changes very quickly. If you don't like things to change much from one version to another, then Ubuntu may not be for you. If the thought interests and excites you then welcome!

---

### Post by piotrasbl on 2014-06-10
32 bit Lubuntu would be fine.
Got that one running on  my old Toshiba Satellite: P4 2.8GHz, 512 DDR RAM and 40GB HDD.
It's not going smoothly on YouTube, but it sure can work as a type writer or web-browser.
Not to mention minidlna :)

---

### Post by Matthew_Zepess on 2014-06-10
I tried 64 bit and 32bit Ubuntu and there both slow, so Im downloading lubuntu and Bodhi, I will install Bodhi first.

---

### Post by DuckHook on 2014-06-10
> **Matthew_Zepess said:**
> I tried 64 bit and 32bit Ubuntu and there both slow, so Im downloading lubuntu and Bodhi, I will install Bodhi first....in which case, you have established that your P4 will work with 64-bit. I would therefore recommend that you stick with 64-bit distros from now on, irrespective of your actual choice of distros.

Be warned that Bodhi is a stripped-down bare-bones distro, the idea of which is to allow you to highly customize your choice of apps to your own desires. You can do so by either individually downloading apps or collections of preselected apps. It tends to be more popular with seasoned users, although I know some new users who are very happy with it. It also uses the enlightenment window manager instead of a more fully featured desktop environment, so some people find this too strange. If you prefer a distro that installs a default set of apps that the majority of people would expect to use on a regular basis, then Lubuntu is designed in that way.

You are already planning to try out both, so let us know which you prefer.

---

### Post by LastDino on 2014-06-10
> **DuckHook said:**
> I have the almost identical dc7600 w/ P4 HT @ 3GHz maxed to 4 GB and found the experience with Xubuntu limiting. My admittedly very unscientific test with processors of this type is to see if I can run a WinXP VM inside the box. With Xubuntu, the VM was noticeably sluggish and jittery. With Lubuntu, the VM ran more smoothly and responsively. A more critical measure was that lm-sensors reported higher temps under Xubuntu than Lubuntu. (A CrunchBang VM runs very nicely with either flavour, but for the average user, there's not much point to running a Linux guest inside a Linux host. As a further curiosity, running an XP guest inside a CrunchBang host gave the snappiest performance of all, but I'm digressing).

Of course, your experiences may be different. There's really no absolute right or wrong here. Lots of ways to skin this cat and Linux is the embodiment of choice. Ergo, my suggestion that the OP try all of these different distros.

Your observation has been on mark. P43.0Ghz does slow down VM in Ubuntu Gnome compared to Xubu. I also tested that on Fedora XFCE and result was same. 

XP VM runs reasonably fine on Manjaro OB though, I haven't tried Lubu or similar version in Debian yet. So yeah. 

I just located someone who is willing to sale used C2D e8400 for about $ 27 and I plan to get that to extend my machines life till I get good enough budget going to go streamline again. 


I think OP should be fine on Bodhi, its good to get old hardware working but you really shouldn't expect it to be perform like new with newer OS and other stuff.

---

### Post by sammiev on 2014-06-10
> **Matthew_Zepess said:**
> I tried 64 bit and 32bit Ubuntu and there both slow, so Im downloading lubuntu and Bodhi, I will install Bodhi first.

If you are running them live from USB/DVD it will run slower than it would off a HDD. Live just lets you know if it works or not.

---

### Post by Mike_Walsh on 2014-06-10
I agree with what other people on here have said.

I have a 10-yr old PC, which was fitted with the AMD Athlon64, yet for all that time it was running the 32-bit version of XP. I have 4 Gb of RAM installed; under XP, it would only recognise 3 and a bit. Since I knew for an absolute certainty that I had a 64-bit CPU, I chose the 64-bit version of Ubuntu 14.04, and now all 4 Gb is accessible.

But it IS a fact that you cannot lose any RAM under Linux. The 32-bit limitation is PURELY a Windows problem...

I installed Ubuntu because it's the distro that I most like...and the old girl now flies like never before. If you're unsure about your machine's specs, go for the 32-bit version of Xubuntu, Lubuntu...or even Puppy Linux. They're ALL fairly light on requirements, and shouldn't tax even an older machine.

As Duckhook has said, Linux is all about choice; you don't even need to stick to the more well-known distros, as there are literally dozens & dozens of different ones to try from. Although relatively new to Linux, I know this through over 30-odd years of messing around with 'puters in general; I have several friends who've tried Linux over the years, and without exception, they have ALL found a distro that they like. So don't be in too much of a hurry to rush into one or the other version; take your time, browse, and look for what appeals to you personally...I am convinced you will find something that works for you.

Mike.

---

### Post by Matthew_Zepess on 2014-06-10
I installed Bodhi, and will try lubuntu later, I used a 32bit Bodhi, but should I go 64bit when I go to lubuntu? and im having trouble using my wnda3100v2 usb wireless card, I found a post that had a good tutorial, but it said get the windows xp drivers, any way to see what is for xp and what is newer/older its a netgear and I think I lost the disk to go with it

---

### Post by DuckHook on 2014-06-10
> **Matthew_Zepess said:**
> ...im having trouble using my wnda3100v2 usb wireless card......not good. According to prior posts, that is a notoriously balky card that has no native Linux drivers and must use XP drivers shoehorned into your Linux install using *ndiswrapper*. Moreover, if running 64-bit Linux, you must use 64-bit XP driver whilst 32-bit OS requires 32-bit driver. I avoid *ndiswrapper* like the plague because I find results to be very uneven and often unworkable, though some have reported success with it. But my philosophy is still that it is best to use Linux drivers with Linux OSes.

Can you lay your hands on a Linux compliant network dongle? D-link makes some good ones. So does Realtek. e-bay is selling them for less than $5 a card, or a friend can give you an unused one for the price of a beer. In my opinion, it isn't remotely worth it to wrestle for hours with your current NIC when a compliant card is so cheap.

If you are a masochist intent on flagellating yourself, then [here]("http://ubuntuforums.org/showthread.php?t=1964173&highlight=NetGear+WNDA3100v2") is a 209-posting thread detailing the ways you can try to get this card working on your box. Don't say I didn't warn you.

---

### Post by Matthew_Zepess on 2014-06-10
yeah, from what ive reasearched its a pain :mad: I don't got a lot of money at the moment, being only 14 and trying to build a gaming pc, so can you point me to a cheap but reliable Linux usb dongle, maybe one good for downloads. maybe even on amazon or ebay.

---

### Post by Matthew_Zepess on 2014-06-10
maybe if you cant find a good one, then ill take my old xp desktop and install it on there, and then do a network bridge. but that's more of a pain than a 5 dollar dongle is worth

---

### Post by DuckHook on 2014-06-11
> **Matthew_Zepess said:**
> ...can you point me to a cheap but reliable Linux usb dongle, maybe one good for downloads. maybe even on amazon or ebay.You should realize that this is an impossible request because it has to be your purchase decision; not mine. However, I would advise that you approach this issue in two simple steps.

1. Look up what WIFI dongles are available on e-bay. I was able to do so by simply typing in "WIFI Dongles" under the e-bay search function. Some hits were as low as $3. If even this is too troublesome, or shipping puts the cost over your budget, then another strategy would be to visit a computer repair shop or a recycling depot. They may be suitably enough impressed with a 14 yr-old computer enthusiast that they will just give you a handful of the dongles that are turned in with recycled computers every day.

2. Compare those dongles to what has been tested and is compatible. [Here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") is the old page for a list of WIFI chipsets that have passed muster for Ubuntu. It is no longer supported, but it is undoubtedly still valid, and will continue to be for at least some time to come.

Last but not least, though it is not my purpose to discourage you, you mention that you are trying to build a gaming PC. I must tell you that, if this is your only goal, you are bound to be disappointed with your current box. It is not remotely powerful enough to act as a gaming machine. Both the P4 CPU and the graphics subsystem is not up to the task and you probably won't be able to even launch any modern games, much less play them. If you are into ancient 2D games that are as old as you are, then your box may be able to handle these, but even these are almost all Windows-based and you could only run them with WINE, which is another can of worms in itself.

A bicycle cannot break the sound barrier and an ancient box cannot play Call of Duty no matter what OS you install on it.

---

### Post by QIII on 2014-06-11
I am with DuckHook -- we can't recommend a purchase to you because it's your money.

However, I would suggest having a look at thinkpenguin.com, which sells hardware specifically designed to work with Linux without significant emotional events.

In particular, this might be of interest.  Weigh it against what else is out there, how much it costs and how much trouble it would be to set up.

[https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-usb-adapter-gnu-linux-tpe-n150usb](https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-usb-adapter-gnu-linux-tpe-n150usb)

---

### Post by DuckHook on 2014-06-11
> **QIII said:**
> ...look at thinkpenguin.com...!!!

I had completely forgotten about that website. Thanks for reminding me of its existence again. I especially love the little penguin sticker that one can buy to cover that unbearable window logo on ones keyboard (it's how I discovered the site originally)8-).

---

