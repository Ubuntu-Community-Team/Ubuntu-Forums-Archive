---
title: "amd radeon driver's"
date: 2022-04-08
forum: New to Ubuntu
---

### Post by jediwarrior-1902 on 2022-04-08
Hi guy's,
firstly I would like to state I am new ish to linux following disappointment's with window's, and at 68 yrs of age, looking for the idiot's guide option please,!!! :P
I have installed radeon Rx 6500 Rt graphix and struggling with screen lag due to lack of correct driver's  ( I presume,? ) I downloaded the Tar ball from amd with no clue what to do with it :(  and
not sure it would be a good idea if there is a way within ubuntu to solve this problem.....is there a repository and if so how do I add it to the repository's available,?
My OS is 20.04.4....Thank's in advance !

---

### Post by grahammechanical on 2022-04-08
Go to Activities and type "software." Click the icon "Software and Updates. Click the Additional Drivers tab. If you are connected to the internet the utility will search the Ubuntu repositories for a proprietary video driver for your card.

Regards

---

### Post by jediwarrior-1902 on 2022-04-08
I have done that Graham, the only thing that has worked is that I booted to safemode and ran DPKG to repair broken packages ....then it work's spot on, however on reboot I have to do the same again,!!
Meenwhile rightly or wrongly ? I installed latest 21.10 sadly the hoped for improvement's were not there :( :P  thought maybe lowering the resolution would help but it only has 1920m x1080 available and I don't know how to import other's,??

---

### Post by QIII on 2022-04-08
Hello!

There should be no reason to do anything further if you have AMD graphics when you install Ubuntu.  All AMD products use either the open source radeon kernel module (for older models) or the open source amdgpu kernel module.  Which is loaded is determined by the installation process.  There is nothing to do.

That said:  This is a very new card.  It is often the case that drivers for the most bleeding-edge new hardware may not be available for Linux at the moment the hardware is introduced.  It takes both the OEM and the Linux community a little while to get things in order.  AMD is extremely Linux friendly, but you still have to understand that they make their money from Windows users, not some piddly small 2% segment of the PC user population that uses Linux.  They'll get it done, but they have to make a profit in the meantime.

Your card was introduced this year.  21.10 was released last year.  It is probably simply not fully prepared for newer hardware.  21.10 is also an interim release, not a long term support (LTS) release, so there will not be as much effort in keeping it up to date -- if any.

Let's see what module is running.

Please post the results of the two following commands in a terminal emulator:

```
lsmod | grep radeon
```

and 

```
lsmod | grep amdgpu
```

These simply ask the machine if it has loaded the radeon module or the amdgpu module.  I don't expect the first to return any results, but the second should return several lines.

(PS:  I find that being in one's 60s is no detriment to learning new things!  :) )

---

### Post by TheFu on 2022-04-08
Almost never will anyone need to download drivers with Linux.  Most of the time, they are 'build-in' already except for bleeding edge stuff.
There is good news.  22.04 will be released in about 2 weeks and that might have the newer drivers for your card. I can't guarantee it, but perhaps.

With all non-MSFT OSes, we need to be extra careful in the hardware we buy.  Getting things that are too new - usually less than 1 yr old - is asking for problems. Stick with 1 generation behind core computer hardware and you'll likely avoid nearly all issues.  With external devices, do all the research you can BEFORE purchase to avoid disappointment.  For example, in the 2012-ish timeframe, some USB3 storage devices didn't work with Linux. Can you imagine that?  Buy a device from a big-box store, take it home and plug it in - nothing.  Eventually, those issues were solved, but similar issues exist for webcams, microphones, some printers, scanners, and other things like wifi and some network cards even today.

It is best to avoid the hardware issues by being cautious.

Last fall, I built a Ryzen 5600G system. The 'G' means is has an iGPU on the CPU.  I was running an 18.04 release with a 4.15 kernel. Alas, GPU support for the 5xxxG series arrived with the 5.10 kernel.  I didn't want to leave 18.04 at the time for a number of reasons.  So I did some expert level stuff ... to get a newer kernel and to manually maintain that kernel myself for the next 3 months before I was ready to move to 20.04. The iGPU did work, just not with the AMD drivers and not as seamless. For me, that system isn't really a desktop, so poor GPU performance doesn't really matter.  20.04 HWE kernel is 5.11 today, so I can use that, if I were ready.

Note that I never considered visiting the AMD video support website and getting drivers from there.  That is NOT the best solution for Linux. Usually, getting linux drivers directly from the vendor causes more problems then get solved.  As someone relatively new to Linux, stay inside the Ubuntu package management system. That will avoid all sorts of problem. Trust us.

Of course, if you know what you are doing, then you can create a Frankenstein Linux install beyond your hearts desires. Just don't expect support from the major distro forums.  We are good at solving issues with stock ubuntu stuff using Canonical's repos and a very select few other, trusted, repos (also called PPAs). Leave those repos and you've decided to allow whoever is running them full root control over your system. Beware.

---

