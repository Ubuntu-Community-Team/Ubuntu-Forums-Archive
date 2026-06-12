---
title: "Best version for old Pentium 4, 686, with a 20GB HD"
date: 2020-04-18
forum: New to Ubuntu
---

### Post by caddickj on 2020-04-18
Subject line pretty much sums it up... 

I found an old IBM ThinkPad running WinXP laying around and wanted to revive it for my daughter's sudden online school use (thanks, Coronavirus). So 90% of what she needs is Google Apps and an easy to use desktop. Currently using Ubuntu 18 on a desktop machine and liking it.

Specs are Pentium 4, 686 architecture. 20GB HD and 2GB RAM.

Any chance there's something I can do with this?

---

### Post by CelticWarrior on 2020-04-18
> **caddickj said:**
> Specs are Pentium 4, 686 architecture. 20GB HD and 2GB RAM.

The 32-bit is now the limiting factor, such architecture is a dead-end as Ubuntu and many of its flavors already ditched the 32-bit releases.

This is opinion based mostly. IMO, Ubuntu-Mate provides the best compromise: A modern(ish) desktop and workflow, highly customizable, light on resources and 18.04 release is supported until April 2021. At that point in time you'll probably need to choose something outside the Ubuntu family, maybe Debian.

---

### Post by poorguy on 2020-04-18
I use old computers and find this Linux distro to work excellent OOTB.

It's Ubuntu 18.04.4 base / LXDE desktop / 32 bit or 64 bit / low resource requirement / supported until 2023.

[https://lxle.net/](https://lxle.net/)

---

### Post by tea for one on 2020-04-18
Have a look at Peppermint OS [https://peppermintos.com/](https://peppermintos.com/)

32 Bit and 64 Bit images are available.

---

### Post by Impavidus on 2020-04-18
> **caddickj said:**
> ... Google Apps ... 686 architecture. ...

Any chance there's something I can do with this?

I don't think Google still supports 32 bit.

---

### Post by mörgæs on 2020-04-18
I use Google Apps with 32 and 64 bit Firefox, both working fine.

---

### Post by DuckHook on 2020-04-18
> **Impavidus said:**
> I don't think Google still supports 32 bit.
Good call. Indeed they don't.

@caddickj

If your daughter *must* use Google Apps, then this laptop simply won't work. I have a 32-bit machine that is still very useful as a CLI server, but that's a far cry from what you are trying to reposition this one for.

EDIT:
> **mörgæs said:**
> I use Google Apps with 32 and 64 bit Firefox, both working fine.
I stand corrected!

---

### Post by mörgæs on 2020-04-18
Well, maybe I shouldn't claim that my 32 bit computer works *fine*. Google Apps are quite heavy so it works, but slowly. 

Caddickj, I think you should give it a shot and see if you find it useful. 2 GB of memory is OK but you have not revealed your graphics processor which may or may not be a bottleneck.

---

### Post by Impavidus on 2020-04-19
> **mörgæs said:**
> I use Google Apps with 32 and 64 bit Firefox, both working fine.

Ah, right, that Google Apps. Google no longer provides applications (like Chrome) for 32 bits, but for Apps that run on your browser instead of your hardware it may work. Confusing...

---

### Post by guiverc on 2020-04-19
I used old thinkpads (pentium M i686) to test Ubuntu 18.04 flavors, and a pentium 4 (dual core) box (I can't recall when I stopped testing using a single core pentium 4 sorry).

I also used those devices to test Lubuntu 18.10, Xubuntu 18.10 & into the 19.04 cycle for both those whilst x86/i686 images were produced (including test-running 19.10 on pentium 4 box on all GTK3 XFCE & LXQt)

With the switch from GTK2 to GTK3, MATE slowed down (Ubuntu-MATE made that switch long before XFCE) and it was rather noticeable on single core pentium M machines first, XFCE switched later (it reached fully GTK3 only for 19.10 but it subjectively slowed as it progressed move to GTK3), however you are using a Pentium 4 and I noticed the slow down less on my dual core pentium 4 box than on the single core pentium M laptops

Myself, I'd recommend Lubuntu 18.04 LTS, or Xubuntu 18.04 LTS first. I'd try both in 'live' mode to see which you prefer  (Lubuntu desktop is lighter than Xubuntu, but I suspect that advantage will be lost when using chromium/chrome [I only use firefox & chromium]).  My next choice would by Ubuntu-MATE 18.04 LTS, however you didn't say if your pentium 4 was single core or double core; as I'd not opt for MATE on a single-core pentium 4.  My 2c anyway

---

### Post by MartyBuntu on 2020-04-19
Put it on a shelf.

---

### Post by Yellow Pasque on 2020-04-19
^Yeah, I think you can find much better used laptops fairly cheap.

> you didn't say if your pentium 4 was single core or double core
I don't think they put dual core Pentium 4's in laptops, or at least in Thinkpads. After disappointing thermal performance and battery life with Mobile Pentium 4 single cores, they quickly moved to Pentium M when it was available.

---

### Post by MartyBuntu on 2020-04-19
I wasn't aware that there were any dual core Pentium 4's...

---

### Post by guiverc on 2020-04-19
> **Yellow Pasque said:**
> Yeah, I think you can find much better used laptops fairly cheap.


I don't think they put dual core Pentium 4's in laptops, or at least in Thinkpads. After disappointing thermal performance and battery life with Mobile Pentium 4 single cores, they quickly moved to Pentium M when it was available.

Great point, my remaining pentium 4 (dual core) acts as a reasonable room heater! being a desktop I'd not considered what that'd do to battery life.

If that is the case, I would go use my pentium M comparisons, however please note.  I have a thinkpad r50p (pentium m) which won't use Lubuntu 18.04 LTS as it's a i586 grade cpu only. My t42p & t43 & later models are all i686 grade pentium m so run it fine, but you may find your pentium 4 is i586 only. If you try booting it and it won't run, you'll get a message telling you a i586 cpu is detected but you require a i686 cpu to boot the kernel.

FYI: My thinkpad r50p will run Debian Buster (10) fine; though it's not much fun for browsing the web (it'll do it, I just prefer other devices as it's slow).  *It could be the i586 issue was why I recycled my single core pentium 4s, but I forget being awhile ago.*

---

### Post by Yellow Pasque on 2020-04-20
> **guiverc said:**
> I have a thinkpad r50p (pentium m) which won't use Lubuntu 18.04 LTS as it's a i586 grade cpu only. My t42p & t43 & later models are all i686 grade pentium m so run it fine, but you may find your pentium 4 is i586 only. If you try booting it and it won't run, you'll get a message telling you a i586 cpu is detected but you require a i686 cpu to boot the kernel.

No, all processors after the original Pentium are i686. The problem is that the first gen of Pentium M ("Banias" core) found in your Thinkpad R50p didn't advertise its PAE support, so Ubuntu is fooled into thinking it's an older CPU. The error message is misleading.
This doesn't apply to the OP's system, so I'm going off on a tangent (again). Sorry about that..

---

### Post by caddickj on 2020-05-02
Hey, everyone - thanks for all the feedback! Sorry I was silent for a while. I appreciate all your help. I hadn't thought about the 32 vs 64 problem with Google Apps. I'm sure I could make it work with some of the suggestions you gave, but it sounds like it would be a painful experience for her anyway. Looks like I'll go on the lookout for a decent used system.

---

### Post by mörgæs on 2020-05-02
You should not trust stuff you read here, not even when it's posted by me :-)

You should take this thread and rest of the forum as encouraging you to conduct your own experiments and draw your own conclusions. 

Installing a 32 bit Debian takes 20 minutes. After that you can try Google Apps and see if you and your daughter are satisfied with the speed.

---

### Post by caddickj on 2020-05-03
ha ha... well, I had a bunch of free time today, so I did actually do a bunch more research on this now-officially lost cause. Turns out I've got 256MB, not 2GB, RAM. I have no idea how I came up with 2GB originally. That cuts out any reasonably modern OS, and then I still had time, so I looked further and found that apparently the chip I have doesn't support SSE, so even if I got it to run the OS, the web is essentially useless. So it's a museum piece.

I did run into a whole different problem where I could only get the system to even recognize 'buntu USBs created using Startup Disk Creator. Tried using dd and ddrescue for a Debian and Puppy distro (Startup Disk wouldn't even attempt those ISOs) and the old system just ignored the USB altogether. I assume I did something wrong somewhere, but that's a whole other issue.

---

### Post by jared-plus on 2020-05-04
You could still use modern distributions like Tiny Core (not based on Ubuntu). There will always be a distro that can run on even the lowest of specs.

---

### Post by Yellow Pasque on 2020-05-04
> **caddickj said:**
> the chip I have doesn't support SSE

All Pentium 4's support SSE and SSE2

---

### Post by Yellow Pasque on 2020-05-04
I missed this:
> **MartyBuntu said:**
> I wasn't aware that there were any dual core Pentium 4's...

True. The product name was Pentium D. But they literally were two Pentium 4 cores (Prescott, and later, Cedar Mill) slapped on a die, so I don't think calling them dual core P4's is totally inaccurate. Sorry if I confused anyone.
Oh, and I still don't remember any laptops with the original Pentium D's (8xx/9xx aka Smithfield/Presler), but if anyone has a link/reference, please share. It seems unlikely to me with the high TDP's.

---

### Post by mastablasta on 2020-05-05
AntiX or MX Linux are also an option.

> So what are the minimum and suggested requirements to run antiX?
antiX should run on most computers, ranging from 192MB old PII systems with pre-configured 128MB swap to the latest powerful boxes.


Also Pentium D could be used as a room heater. :)

---

### Post by ActionParsnip on 2020-05-07
Lubuntu 20.04 all the way. Leaves more resources for applications

---

### Post by MoebusNet on 2020-05-13
If worst comes to worst, Puppy Linux is always an option for antique hardware: [http://puppylinux.com/](http://puppylinux.com/)

However, Wikipedia describes the Pentium D series as 64-bit CPU's at: [https://en.wikipedia.org/wiki/Pentium_D](https://en.wikipedia.org/wiki/Pentium_D), so any 32-bit architecture end-of-life limitations previously mentioned would not seem to apply.

If you have a single-core Pentium 4, you may still be able to use 64-bit Linux. The first Pentium 4-branded processor to implement 64-bit was the Prescott (90 nm) (February 2004), but this feature was not enabled. Intel subsequently began selling 64-bit Pentium 4s using the "E0" revision of the Prescotts, being sold on the OEM market as the Pentium 4, model F. [https://en.wikipedia.org/wiki/Pentium_4](https://en.wikipedia.org/wiki/Pentium_4)

---

### Post by kurt18947 on 2020-05-16
> **caddickj said:**
> ha ha... well, I had a bunch of free time today, so I did actually do a bunch more research on this now-officially lost cause. Turns out I've got 256MB, not 2GB, RAM. I have no idea how I came up with 2GB originally. That cuts out any reasonably modern OS, and then I still had time, so I looked further and found that apparently the chip I have doesn't support SSE, so even if I got it to run the OS, the web is essentially useless. So it's a museum piece.

I did run into a whole different problem where I could only get the system to even recognize 'buntu USBs created using Startup Disk Creator. Tried using dd and ddrescue for a Debian and Puppy distro (Startup Disk wouldn't even attempt those ISOs) and the old system just ignored the USB altogether. I assume I did something wrong somewhere, but that's a whole other issue.

If you really do have 256 MB. RAM it is IMO a tinker piece, not a user piece. I'm a ThinkPad fan, like their keyboards and pointing devices better than most notebooks. I've bought a few off Ebay when I spot what I perceive to be a bargain. I have 2 T series, T410 & T430. Both less than $100 on Ebay and both work as expected. I did upgrade the memory to 8 GB. with used SO-DIMMs. Both run Ubuntu 20.04 just fine. One thing to be aware of with notebooks - non Intel WiFi can be a challenge with Linux. Some non-Intel wifi chips work fine, others are a challenge. Thinkpads used to whitelist WiFi adapters. That means you can only use the listed WiFi chips if you want to install internally and use the integral antenna(s). I don't know if they still whitelist or not. USB WiFi is an alternative.

---

### Post by MoebusNet on 2020-05-27
If you have the time to devote to resurrecting your boat anchor, you might be surprised at what it can do. For example, your failure with Puppy was probably caused by your BIOS's inability to boot from USB. It may be that a BIOS update would fix that, but at any rate it should be possible to burn Puppy to a CD/DVD as a boot medium (if I recall correctly). At worst, you could wind up with a backup system for your photos, music and documents (not video - file sizes too big).

---

### Post by DuckHook on 2020-05-27
I'm fulfilling my role as the Forums broken record, but the best use I've found for really old stuff is as command line servers. It's surprising what some of these old laptops can still do, although I also concur with mastablasta that Pentium Ds are like little Plutonium heaters. Morgæs has mentioned before that sometimes, it really is time to give such HW their honourable burial because, if one adds up the electrical costs, they're not really that much of a bargain. Barring that, CLI server use is the most trouble-free because it makes the least demands on HW where it is obsolete, yet leverages those strengths that still shine.

---

