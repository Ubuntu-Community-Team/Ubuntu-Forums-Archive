---
title: "Getting rid of Windows."
date: 2015-08-01
forum: New to Ubuntu
---

### Post by Tigendo on 2015-08-01
I am new to Ubuntu and I am seriously considering just getting rid of Windows altogether. I am just wondering if my computer specs are good enough to run all of my Windows programs with a wrapper without any performance hits. My computer specs are listed below.

AMD FX-8350 Black Edition Vishera 8-Core 4.0GHz on an Asus motherboard

16GB Ram

120GB SSD

3Tb HDD

nVidia GeForce 750 Ti


If there is any additional information that is needed, please let me know and I will gladly provide it.

Thank you

---

### Post by Vladlenin5000 on 2015-08-01
Hi and welcome.

Your specs are good ti run anything you want.
However... If you need Windows apps then keep Windows. Many apps simply don't work when used with a compatibility layer and even when they do you shouldn't expect the same performance most of the times.

And no, Ubuntu isn't a free Windows clone...

---

### Post by Tigendo on 2015-08-01
Thank you for the information.

---

### Post by MartyBuntu on 2015-08-01
Your machine would certainly be able to run a virtualised Windows install... if that would take care of any needs that require Windows.

---

### Post by QIII on 2015-08-01
Virtualization does not work well for heavy graphics applications.  Games, movies, youtube, etc.

With those specs, I'd dual boot.  That way you would be able to run both Windows and Ubuntu natively -- just not at the same time.

---

### Post by Tigendo on 2015-08-01
When i try to dual boot, the Ubuntu installer will not show my SSD for a partitioning option. Will I need to use Windows Partition to create a new unformatted partition first? Any information will be very welcome.

---

### Post by Vladlenin5000 on 2015-08-01
> **jason185 said:**
> When i try to dual boot, the Ubuntu installer will not show my SSD for a partitioning option. Will I need to use Windows Partition to create a new unformatted partition first? Any information will be very welcome.

You need to disable fastboot in Windows. Otherwise it's the same as hibernation and hibernated (i.e. in use) partitions cannot be mounted.
You can (and should) use Windows tools to shrink one or more of your existing partitions - and no other tools - thus leaving unallocated _space_ to be partitioned by the installer. There's no such thing as "unformatted partitions"

---

### Post by Tigendo on 2015-08-01
Thank you for that. I will definately disable fast boot. I am pleasantly surprised by the speedy and courteous responses from this community.

---

