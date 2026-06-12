---
title: "What are your thoughts about installing Ubuntu on a new MS laptop"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by a.v.l on 2008-06-12
Having bought a new Acer laptop today with MS Windows pre-installed, I'm wondering what is considered best practice for installing Ubuntu on this machine with regards to maintaining the original manufacturers twelve month guarantee.

---

### Post by gr4nf on 2008-06-12
I dont think that you void the hardware warranty by just changing the OS. Do you know how to install ubuntu? if not, just ask.

---

### Post by philinux on 2008-06-12
> **a.v.l said:**
> Having bought a new Acer laptop today with MS Windows pre-installed, I'm wondering what is considered best practice for installing Ubuntu on this machine with regards to maintaining the original manufacturers twelve month guarantee.

1. Make sure you have recovery cd's.

2. Dual boot.

3. Wubi

4. virtualbox

Not in any preferred order. Apart from number 1.

---

### Post by aktiwers on 2008-06-12
First install Linux, then I would return Windows and get my money back for it..  :)

---

### Post by Joeb454 on 2008-06-12
Just make sure you keep the recovery partition, as the restore disk's you get nowadays don't have the full OS on.

It'll likely be a small 5 or 6GB partition :)

---

### Post by ugm6hr on 2008-06-12
> **a.v.l said:**
> Having bought a new Acer laptop today with MS Windows pre-installed, I'm wondering what is considered best practice for installing Ubuntu on this machine with regards to maintaining the original manufacturers twelve month guarantee.

Acer will essentially refuse to support the hardware unless you have the original OS on it.

So I would suggest you either dual-boot, or make sure you have a recovery CD/DVD to reinstall it if necessary.

The other option is to just take the HD out if you ever need to send the laptop back to them (quoting data security as the reason).

For your info - I kept the original Vista recovery partition on my HD, but wiped the actual installation.

---

### Post by kamitsukai on 2008-06-12
Yes almost all major PC manafacturers (even dell..to some extent) wont support your hardware or will even viod the warranty if you remove Microsh*te (if they find out :D)

---

### Post by Joeb454 on 2008-06-12
I got rid of mine :p I figured I'd just replace the HDD if it dies :)

---

### Post by a.v.l on 2008-06-12
> **philinux said:**
> 1. Make sure you have recovery cd's.

2. Dual boot.

3. Wubi

4. virtualbox

Not in any preferred order. Apart from number 1.

Thanks where do I get the recovery CD's from. Non came with the laptop.

---

### Post by Joeb454 on 2008-06-12
Call Acer and say something broke on your install, and you need the CD :) If I remember rightly, I think they're obliged to give you the disc ;)

---

### Post by philinux on 2008-06-12
> **a.v.l said:**
> Thanks where do I get the recovery CD's from. Non came with the laptop.


Usually there's an option to create one, a DVD I should have said, when you first turn on the laptop.

---

### Post by Joeb454 on 2008-06-12
> **philinux said:**
> Usually there's an option to create one, a DVD I should have said. Are you sure what you got.

Have you got an oem install disk or a recovery partition?

Even with the option to create one, it usually still requires the recovery partition to exist.

Never mind, I have Linux to fall back on :D

---

### Post by ugm6hr on 2008-06-12
> **a.v.l said:**
> Thanks where do I get the recovery CD's from. Non came with the laptop.

Acer have a function to create a recovery DVD.  It is supposed to be able to reinstall without the recovery partition.

Unfortunately, it didn't work on my laptop.  Hence I kept the recovery partition.

Good luck trying to get in touch with them about supplying a disc - I found it impossible.  Acer aren't renowned for the customer service :(

---

### Post by pastormick on 2008-06-12
I sent my Acer Aspire 5100 back to Acer Canada for a motherboard replacement with only Ubuntu installed, recovery partition wiped, and no sign of Windows. this was only three months ago, with six months left on a twelve-month warranty. No problems; all work done under warranty. When I phoned for an RMA they did ask if Vista had displayed any messages or blue screens, but after telling them that Vista had been wiped in favor of Ubuntu first thing, the only response was "ok". 

I 'forgot' to make the recovery DVD before installing Ubuntu, but I'd install XP if I had to. In a moment of uncharacteristic forward-thinking, however, I did leave a 15G NTFS partition at the beginning of the hard drive - a 'pity partition' of sorts... 

Mick

---

### Post by stalkier on 2008-06-12
> **Joeb454 said:**
> Call Acer and say something broke on your install, and you need the CD :) If I remember rightly, I think they're obliged to give you the disc ;)

Most likely. I have never had a Acer system but HP/Compaq do not come with CDs either. They DO have an option to create recovery CDs. Not sure if Acer has this option. I had to call and get mine as I f'ed up the system as soon as I bought it. (Didn't know you had to start the system for the first time with no added hardware. I had installed a slave hdd and a vid card...all non-stock) Of course I didn't tell them I did that. After recovering the system with the discs without the added hardware the system worked like a charm. As a matter of fact it is the same system I am using now. Although I had to get a new MB....loose conection between DDR and MB caused it to melt...crazy.

---

### Post by Joeb454 on 2008-06-12
I had to do something similar with Dell, though it was actually because I installed Vista Beta 2, and decided I wanted to keep XP, but I didn't have the disk.

I told them most of the truth, and they sent me the disk. The guy on the phone even asked what Vista was like...umm...

---

### Post by Ripfox on 2008-06-12
> **pastormick said:**
> I sent my Acer Aspire 5100 back to Acer Canada for a motherboard replacement with only Ubuntu installed, recovery partition wiped, and no sign of Windows. this was only three months ago, with six months left on a twelve-month warranty. No problems; all work done under warranty. When I phoned for an RMA they did ask if Vista had displayed any messages or blue screens, but after telling them that Vista had been wiped in favor of Ubuntu first thing, the only response was "ok". 

I 'forgot' to make the recovery DVD before installing Ubuntu, but I'd install XP if I had to. In a moment of uncharacteristic forward-thinking, however, I did leave a 15G NTFS partition at the beginning of the hard drive - a 'pity partition' of sorts... 

Mick

That is just awesome.

---

### Post by nhasian on 2008-06-13
I dont think anyone else mentioned this, but you dont have to remove vista, and you dont have to use wubi and take a performance hit.  You can just boot off the ubuntu CD and use gparted to edit the partition on the hard disk so you can dual boot.  

your hard disk will most likely have a small partition on it for the windows restore, so dont mess with that one.  Just shrink the windows partition to make room for linux.  you will need to create a small partition 512-1024 megs for the linux swap, and then the remainder set as /ext3 for linux.

after you've installed ubuntu then when you boot your laptop you can choose between vista or ubuntu.

---

### Post by hyper_ch on 2008-06-13
> **ugm6hr said:**
> Acer will essentially refuse to support the hardware unless you have the original OS on it.

> **kamitsukai said:**
> Yes almost all major PC manafacturers (even dell..to some extent) wont support your hardware or will even viod the warranty if you remove Microsh*te (if they find out :D)

They wouldn't be able to pull that here.

---

### Post by a.v.l on 2008-06-14
It seems that Acer might be considering Linux from this following link.


[http://news.cnet.com/8301-10784_3-9960210-7.html](http://news.cnet.com/8301-10784_3-9960210-7.html)

---

### Post by FTBPrimeEvil on 2008-06-14
I just bought a new laptop m15x from Alienware with Vista Ultimate installed, I am running a dual boot on a second partiton, actually i deleted the 8gb recovery partition and used shrink partition to get a second 16gb part. which I have Ubuntu installed on.

Happy Ubuntu'ing:)

---

### Post by flyingtiger on 2008-06-14
I I had just purchased a new laptop with MS installed on it I would wipe all renderings of MS from the hard drive and install Ubuntu. I have had dual booting PC's in the past and now favor only one OS on each PC.

---

### Post by sultanoswing on 2008-06-14
> **flyingtiger said:**
> I I had just purchased a new laptop with MS installed on it I would wipe all renderings of MS from the hard drive and install Ubuntu. I have had dual booting PC's in the past and now favor only one OS on each PC.

Agreed! You other guys are making this more complicated than it needs to be. Bite the bullet, format the sucker completely (including the evil, GB-stealing 'recovery partitions' and 'mediadirect'-crap), install your open-source O/S of choice and be at peace.

:)

---

### Post by cariboo on 2008-06-14
I belive there is something called Acer Advantage installed on you laptop. Make sure you have a couple of blank dvds and run the application. It will make a set of recovery dvds for you. That should have come up the first time you started your computer. A friend of mine just bought the recovery disk from Acer and if I remember correctly for Vista Home Premium it was about $180.00 Canadian.

Jim

---

