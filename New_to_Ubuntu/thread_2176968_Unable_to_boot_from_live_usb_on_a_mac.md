---
title: "Unable to boot from live usb on a mac"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by peterk2 on 2013-09-26
Hello,
I'm trying to dual boot ubuntu with snow leopard on a macbook. I've created a live usb(s) using the dd command and unetbootin and I have rEFIt installed. When i try to boot and choose the usb i get a black screen reading "Missing operating system". Could someone help me?

---

### Post by JonasDeMoor on 2013-09-27
Hi, I think the filesystem on the USB is corrupted: I've used the dd command in the past and sometimes, it rendered the USB drive useless; I had to reformat it and make a new partition table. Normally, if you use Unetbootin, you shouldn't have any problems. 

The problem could also be with a particular release of Ubuntu: currently two releases are supported: 
- Ubuntu 12.04.3: This is the current Long Term Support (LTS) release, it has updates untill April 2017. I always recommend using this release.
- Ubuntu 13.04: this release has newer features, but it tends to be more unstable on some machines. Also, it has only 6 months of support: you have to upgrade every six months if you choose the "regular" releases instead of the  LTS's.

I don't own a Mac, so I don't know this information will be useful for you, but I hope this is somewhat useful.

---

### Post by Jonathan Precise on 2013-09-27
> **JonasDeMoor said:**
> ... Also, it has only 6 months of support...

Actually, it has 9 months of support (3 month "grace" period if you can't upgrade).

[QUOTE=peterk2]... I have rEFIt installed. When i try to boot and choose the usb i get a black screen reading "Missing operating system"[/QUOTE]

I recommend using [rEFInd]("http://www.rodsbooks.com/refind/") instead of [rEFIt]("http://refit.sourceforge.net"), because:

> 2013-03-29: As you may have noticed, rEFIt is no longer actively maintained. Please check out [rEFInd]("http://www.rodsbooks.com/refind/"), a fork that is maintaned and under active development.

---

