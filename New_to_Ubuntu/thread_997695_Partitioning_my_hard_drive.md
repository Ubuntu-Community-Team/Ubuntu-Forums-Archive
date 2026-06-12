---
title: "Partitioning my hard drive"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Airforcefalco on 2008-11-30
I go into Partition Editor and try to partition /dev/sda1 since it is where all of my slack space is at and the option is grayed out. I try to unmount it but then it tells me that it can't unmount mount point "/"

I am trying to install windows but when i put in the windows disk all it notices is sda1 and sda2 as two separate drives and it won't let me partition them and I don't want to lose Linux. Can I make a partition for Linux and Windows and have a space that both of them can use like NTFS?

Thanks for the help.

---

### Post by adult swim on 2008-11-30
try booting from a ubuntu live cd and then partitioning.  be careful if you are going to resize your root (/) partition.  that could lead to problems.

---

### Post by Airforcefalco on 2008-11-30
I have files stored on my sda1 partition, will i lose any files?

---

### Post by Airforcefalco on 2008-11-30
Bump

---

### Post by trooperchix on 2008-11-30
Try G-parted, worked for me...

---

### Post by isa.k on 2008-11-30
I just booted off a live cd.

And now I want to install Ubuntu 8.10.

I have two HDDs, 1@300gb sata and the other @ 200 GB i think...

The 300 is partitioned into 100/200
The 200 is partitioned into 50/150

I got this screen:

[[IMG]http://img146.imageshack.us/img146/5324/screenshotgk4.th.gif[/IMG]](http://img146.imageshack.us/my.php?image=screenshotgk4.gif)

Actually, I selected the "Manual" dial

I need to know how to select the correct partition and only use that.

Any help?

The sooner the better :)

My system is hanging in limbo in the mean time...


Regards,

Isa

---

### Post by drubin on 2008-11-30
> **Airforcefalco said:**
> Bump

Please wait at least 24 hours before bumping. It is considered rather bad to bump after 3 hours.

Here this might help you
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I am quite sure you need to be using a live cd in order to re-size the current partion that the OS is running off.

---

### Post by isa.k on 2008-11-30
Is there an answer to my question in those links **drubin**?

---

### Post by drubin on 2008-11-30
> **isa.k said:**
> Is there an answer to my question in those links **drubin**?

I was posting them to the OP. Not sure why you took over this thread... But I am sure your question seems relevant then those links would help you as well..

Generally reading the links people post in replies will give you the answers you require.

---

### Post by RadiationHazard on 2008-11-30
> **trooperchix said:**
> Try G-parted, worked for me...

+1
to get gparted go here:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by drubin on 2008-11-30
> **RadiationHazard said:**
> +1
to get gparted go here:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Gparted is included in the live cd's. Please read the post about having to use a live cd when editing your partions.

You can't edit something while it is in use.

---

### Post by mapes12 on 2008-11-30
> Gparted is included in the live cd's. Please read the post about having to use a live cd when editing your partions.

But some systems (like one of mine) don't like the Live Ubu CD's so my preference is to burn a bootable GParted CD from the Gparted website (link already on this thread) and boot from that. I can personally endorse the previously posted Psychocats tutorials as well. "/" and /home on different partitions really is a must configuration.

---

### Post by drubin on 2008-11-30
> **mapes12 said:**
> But some systems(like one of mine) don't like the Live Ubu CD's so my preference is to burn a bootable GParted from the Gparted website (link already on this thread) and boot from that. I can personally endorse the previously posted Psychocats tutorials as well. "/" and /home on different partitions really is a must configuration.

I agree some systems do not like the live ubuntu cd. But they would be the ones that standard uses are most used to so I always suggest them first.

---

### Post by JohnFH on 2008-11-30
> **isa.k said:**
> I just booted off a live cd.

And now I want to install Ubuntu 8.10.

I have two HDDs, 1@300gb sata and the other @ 200 GB i think...

The 300 is partitioned into 100/200
The 200 is partitioned into 50/150

I got this screen:

[[IMG]http://img146.imageshack.us/img146/5324/screenshotgk4.th.gif[/IMG]](http://img146.imageshack.us/my.php?image=screenshotgk4.gif)

Actually, I selected the "Manual" dial

Isa

The easiest thing to do is select the first option (Guided - resize SCSI5 (0,0,0), partition 5 (sdb) and use freed space).

---

### Post by isa.k on 2008-11-30
> **JohnFH said:**
> The easiest thing to do is select the first option (Guided - resize SCSI5 (0,0,0), partition 5 (sdb) and use freed space).
Will this damage my partition (i.e. chnage the size / join the two partitions?)

---

### Post by JohnFH on 2008-11-30
> **isa.k said:**
> Will this damage my partition (i.e. chnage the size / join the two partitions?)

It won't damage the data on it, no.  However, partitioning is always risky so make sure you have a backup of important data anyway.

---

### Post by kansasnoob on 2008-11-30
> **isa.k said:**
> I just booted off a live cd.

And now I want to install Ubuntu 8.10.

I have two HDDs, 1@300gb sata and the other @ 200 GB i think...

The 300 is partitioned into 100/200
The 200 is partitioned into 50/150

I got this screen:

[[IMG]http://img146.imageshack.us/img146/5324/screenshotgk4.th.gif[/IMG]](http://img146.imageshack.us/my.php?image=screenshotgk4.gif)

Actually, I selected the "Manual" dial

I need to know how to select the correct partition and only use that.

Any help?

The sooner the better :)

My system is hanging in limbo in the mean time...


Regards,

Isa

Please start a new thread!

I'm not being "snarky". It's just hard to work on two problems at once in the same thread!

---

### Post by isa.k on 2008-11-30
**JohnFH** thank you :)

**kansasnoob** i'm outa here.

---

### Post by kansasnoob on 2008-11-30
> **Airforcefalco said:**
> I go into Partition Editor and try to partition /dev/sda1 since it is where all of my slack space is at and the option is grayed out. I try to unmount it but then it tells me that it can't unmount mount point "/"

I am trying to install windows but when i put in the windows disk all it notices is sda1 and sda2 as two separate drives and it won't let me partition them and I don't want to lose Linux. Can I make a partition for Linux and Windows and have a space that both of them can use like NTFS?

Thanks for the help.

I don't know what happened here since your thread got "hijacked" but if you're still looking for answers please post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by kansasnoob on 2008-11-30
> **isa.k said:**
> **JohnFH** thank you :)

**kansasnoob** i'm outa here.

I hope you mean you're starting a new thread!

---

### Post by isa.k on 2008-11-30
> **kansasnoob said:**
> I hope you mean you're starting a new thread!
No, it means I got what I came for.

Sorry to let your hopes down :p

---

### Post by Airforcefalco on 2008-11-30
> **kansasnoob said:**
> I don't know what happened here since your thread got "hijacked" but if you're still looking for answers please post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb159982e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29275   235151406   83  Linux
/dev/sda2           29276       30401     9044595    5  Extended
/dev/sda5           29276       30401     9044563+  82  Linux swap / Solaris

I just moved so I am not sure where to find a CD or if I did find one if I am allowed to download it on this open network since it will tie up bandwidth for a while.

Thank you all for your help, I would say more but my son is sick and crying at the moment.

---

