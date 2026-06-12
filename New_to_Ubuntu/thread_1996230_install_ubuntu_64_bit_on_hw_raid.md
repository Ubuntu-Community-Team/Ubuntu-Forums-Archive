---
title: "install ubuntu 64 bit on hw raid"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by Myriam Alberti on 2012-06-04
Hello,

I need some input on how to install Ubuntu server 64bit on a HP Proliant DL120 G7 using hardware raid. What I want to achieve is raid 1 (mirroring).

Thank you,
Myriam

---

### Post by sandyd on 2012-06-04
> **Myriam Alberti said:**
> Hello,

I need some input on how to install Ubuntu server 64bit on a HP Proliant DL120 G7 using hardware raid. What I want to achieve is raid 1 (mirroring).

Thank you,
Myriam

If you are using hardware raid, there is no difference in the installation. Ubuntu will see it as a single disk.

1. Set the hardware RAID

2. Install the Ubuntu Server Iso through a cdrom drive /usb drive.

---

### Post by Myriam Alberti on 2012-06-05
Thank you.
Is there any better performance of hw raid over sw raid?

Myriam

---

### Post by sandyd on 2012-06-05
> **Myriam Alberti said:**
> Thank you.
Is there any better performance of hw raid over sw raid?

Myriam

Not really.
SW raid uses higher cpu (as the raid is managed by the CPU, vs the RAID Controller), but it shouldn't be a problem.

Recovery is easier on SW raid though. It really depends on what you have on hand. If you have a spare, identical RAID controller you can swap to if the one you are using dies, I would go for HW RAID. Otherwise, just go for sw raid.

---

### Post by Myriam Alberti on 2012-06-06
Thank you SD. I think I'll go for the SW raid then. Seems easier to handle.

---

### Post by Gone fishing on 2012-06-06
I've use software raid 1 using mdadm and its been very good, very reliable and has saved thing when a hard drive has failed.

---

