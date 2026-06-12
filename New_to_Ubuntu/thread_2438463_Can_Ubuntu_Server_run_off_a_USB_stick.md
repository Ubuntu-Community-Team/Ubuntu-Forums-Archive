---
title: "Can Ubuntu Server run off a USB stick?"
date: 2020-03-12
forum: New to Ubuntu
---

### Post by elsmandino2 on 2020-03-12
Hi there.

I am a long-term user of Openmediavault.

Whilst it works absolutely fine for me, I am looking at something a little bit more "hands-on" - i.e. I want to actually learn how Linux works.

I am currently running OMV off a USB stick - is this something that I can do with Ubuntu Server?

---

### Post by Tadaen_Sylvermane on 2020-03-12
Should work just fine. Don't expect amazing performance though.

Linux is linux regardless of the gui or web interface on top of it.

*EDIT* That is actually very interesting. I never considered it before. I'm wondering if I could open up a drive bay in my own server and use a flash drive for OS purposes. Something to research. Not sure I'm willing to give up my ssd though.

---

### Post by crip720 on 2020-03-12
It can be done as easy as installing to any other drive, but USB sticks are known to give up the ghost with no warning.  If you need dependably, probably should be down low on the list of drive types.

---

### Post by SeijiSensei on 2020-03-12
Most servers require more storage than a USB drive offers. So while this can work, you'd still likely need another device for data storage.

I have a 4 TB USB device.  I've not considered trying to boot from it, but if that's possible, then it might help with the problem.

Performance is another question.

---

### Post by MoebusNet on 2020-03-12
If your chassis has the capability and your BIOS can boot from it. using an SD Card or micro-SD Card for your OS is an option. Indeed, some of the newer media server distros are designed for this very scenario. I've seen SD Cards from 4Gb to micro-SD Cards of 256 Gb capacity. Another advantage is the card is inside the slot rather than sticking out from and blocking a USB port, so there is that. I am under the impression that typical media server usage isn't as read/write intensive to the OS drive as typical Desktop usage could be, once boot-up is completed. This scenario envisions  separate drives for the OS and media storage.

---

### Post by SeijiSensei on 2020-03-12
> **MoebusNet said:**
> I've seen SD Cards from 4Gb to micro-SD Cards of 256 Gb capacity.

I recently bought a 128GB Samsung micro-SD card to expand storage on a tablet; it cost less than $20 at Amazon: [https://www.amazon.com/Samsung-MicroSDXC-Adapter-MB-ME128GA-AM/dp/B06XWZWYVP/](https://www.amazon.com/Samsung-MicroSDXC-Adapter-MB-ME128GA-AM/dp/B06XWZWYVP/)

I know memory prices keep falling, but I thought 6 GB/dollar was pretty stunning.

Came with an adapter so it can fit SD ports, too.

---

### Post by elsmandino2 on 2020-03-12
Ah, sorry - I should have clarified.

My current server has 10.5TB of storage (4 HDDs merged via mergerfs).  

The storage is for backup purposes only - i.e. it resumes from sleep, to backup my main server, once a day.

I literally run the OS from the USB stick only.

Openmediavault also offers an extra plugin that limits the writes to USB and SD installations too, so they seem to last years.

Also, OMV seems to be optimised for running in RAM (so once it is up and running, it is very quick).

I am hoping I could do something similar with Ubuntu.

---

### Post by MoebusNet on 2020-03-12
Short answer: **YES**. Flash Drive, SD Cards, SSD's or HDD's shouldn't matter.

---

### Post by SeijiSensei on 2020-03-12
> **elsmandino2 said:**
> Also, OMV seems to be optimised for running in RAM (so once it is up and running, it is very quick).

I am hoping I could do something similar with Ubuntu.
All Linux kernels keep as much as possible in memory; that should be true for any distribution.

The kernel also aggressively caches disk transactions, so once you read a file from the hard drive, it is cached and any further references to the file are handled by the image in memory.

---

### Post by TheFu on 2020-03-12
The main issue would be that Linux distros are setup to log stuff to main storage, so the write counts per sector will quickly exceed the design writes for most cheap flash storage.  There are ways around that, but a noob probably shouldn't screw with those internals.  Enterprise CF storage has been used for decades in similar applications, BTW.
I have a few Raspberry Pi machines that are using microSD storage for the OS and logs, but not for any media.  They've lasted a few years, which has surprsed me.  
I've also had expensive, name-brand, USB3 flash storage fail before 1 yr of use due to large numbers of writes.
Had two SSDs in laptops fail completely before 3 yrs of use happened.

In short, expect storage failure and expect to need a cloned OS storage device when it is least convenient.

You are braver than I using mergerfs.  I've lost 80% of everything running an enterprise storage merging solution. When 1 disk failed, all the files on all the other merged disks were gone too.

---

### Post by C.S.Cameron on 2020-03-12
I've used SD cards for server duty. In both cased the cards died within six months.
I was running the last one in RAM, (toram boot). It seems to have died in a read only state.
These examples may only be a coincidence.

---

### Post by SeijiSensei on 2020-03-13
> **TheFu said:**
> The main issue would be that Linux distros are setup to log stuff to main storage, so the write counts per sector will quickly exceed the design writes for most cheap flash storage.  There are ways around that, but a noob probably shouldn't screw with those internals.
If the machine has an internal hard drive, the easiest solution would be to create a partition for /var on the hard drive and mount it from /etc/fstab. Then all the logging would happen on the hard drive.

---

