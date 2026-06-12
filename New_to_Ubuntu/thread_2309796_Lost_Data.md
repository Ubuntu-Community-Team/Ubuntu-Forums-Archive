---
title: "Lost Data"
date: 2016-01-13
forum: New to Ubuntu
---

### Post by Debbie_Garton on 2016-01-13
All, I appeal to the Linux experts to help me retrieve data that was lost on my media centre, that uses enigma2 (a variant of Linux).

I have Ubuntu installed on my laptop.

I had a 1.5tb drive, partitioned into 2 equal sizes.

My media centre, Vu+ Duo 2 was the cause of the issue. The boxes OS enigma2, is installed to flash.
I tried to install PBnigma and it installed perfectly.

The only issue was that the external hard drive was not recognised. I tried to mount the drive/s through Mount Manager but the existing data was not readable. I tried to "initialise" the drive but then realised that this started to format the drive, so I immediately stopped the process.

I reinstalled the old OS to see if the partitions had returned but alas - no such luck.

I am devastated, as the drive contained my only record/s of my deceased father. All our home videos are gone! The only reason I transferred them onto the media centre was a failing drive, which did in fact die after the migration. On reflection, I should have taken multiple copies.

I immediately took out the drive and put it into a caddy and hooked it up to my Ubuntu laptop. Again, no luck reading the files.. Or even locating them..

I work in IT (makes it more annoying) and one of my colleagues suggested using Test Disk. I did so and it reported a missing signature.

When I connected the caddy to my laptop, the drives were identified and mounted as hdd and hdd1.

Tried to locate partitions with Test Disk but no data was found. I used PhotoRec and data was found.
It found avi,mp4 and mov. I tried restoring some to the laptop but all the folders have padlocks on, I assume a permissions issue?

My ask please, is that a guru can help me rebuild the partition and hopefully access my data.

I have a working image (drive snapshot)so original drive is preserved.

I can provide any further information, if required.

Here's hoping +-)

Debbie (London)

---

### Post by yancek on 2016-01-13
You used windows to 'initialize' the drive?  Take a look at the link below which has some suggestions on recovering.  Particularly, the post labelled 'best solution' and the one two posts down from it.

 [http://www.tomshardware.com/forum/258179-32-initialize-hard-drive-formatting](http://www.tomshardware.com/forum/258179-32-initialize-hard-drive-formatting)

---

### Post by matt_symes on 2016-01-13
Hi

Welcome to the forums.

> **Debbie_Garton said:**
> I am devastated, as the drive contained my only record/s of my deceased father. All our home videos are gone! The only reason I transferred them onto the media centre was a failing drive, which did in fact die after the migration. On reflection, I should have taken multiple copies.


Ouch. 

> I immediately took out the drive and put it into a caddy and hooked it up to my Ubuntu laptop. Again, no luck reading the files.. Or even locating them..

I work in IT (makes it more annoying) and one of my colleagues suggested using Test Disk. I did so and it reported a missing signature.
 

This is a good suggestion.

> When I connected the caddy to my laptop, the drives were identified and mounted as hdd and hdd1.

That sounds promising. It looks like the partitions are still there.

> Tried to locate partitions with Test Disk but no data was found. I used PhotoRec and data was found.
It found avi,mp4 and mov. I tried restoring some to the laptop but all the folders have padlocks on, I assume a permissions issue?

Almost definitely a permissions issue.

> I have a working image (drive snapshot)so original drive is preserved.

Excellent. Work off the image only. You can mount it as a loop device.

> I can provide any further information, if required.

Here's hoping +-)

Debbie (London)

I'm cooking at the moment but I'll try at give a hand later.

Put the hard drive in a safe place and don't touch it.

Kind regards

---

### Post by haplorrhine on 2016-01-13
I imagine you could do it with Kali Linux.
[https://forums.kali.org/showthread.php?18787-Using-Kali-Linux-to-access-corrupted-external-Hard-Drive](https://forums.kali.org/showthread.php?18787-Using-Kali-Linux-to-access-corrupted-external-Hard-Drive)
You boot into Kali forensic mode after setting the corrupt (or [rootkit]("https://en.wikipedia.org/wiki/Rootkit") infected) drive to slave mode.

---

### Post by Debbie_Garton on 2016-01-14
> **yancek said:**
> You used windows to 'initialize' the drive?  Take a look at the link below which has some suggestions on recovering.  Particularly, the post labelled 'best solution' and the one two posts down from it.

 [http://www.tomshardware.com/forum/258179-32-initialize-hard-drive-formatting](http://www.tomshardware.com/forum/258179-32-initialize-hard-drive-formatting)


The drive has never been initialised in Windowa? - Only Linux

---

### Post by Debbie_Garton on 2016-01-14
[QUOTE=matt_symes;13422553]Hi


Excellent. Work off the image only. You can mount it as a loop device.


-- What is aloop device?


Would love your help - many thanks

---

