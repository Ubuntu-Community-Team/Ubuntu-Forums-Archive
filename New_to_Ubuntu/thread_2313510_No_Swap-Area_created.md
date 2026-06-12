---
title: "No Swap-Area created"
date: 2016-02-13
forum: New to Ubuntu
---

### Post by SnuKies on 2016-02-13
Hello guys,

I've just installed Ubuntu 14.04 on my laptop. But I made a dualboot alongside Windows 7. Now, on windows I have 2 partitions (C: for system and D: for files). But there is also that partition that windows has created on its install.

As far as I know, I am allowed to create maximum 4 partition. With 3 partitions taken by windows, I only had 1 left, on which is my '/ ' . As I read on the internet, it'd be good to create a swap partition as well.

My primary partition for Ubuntu has 138GB, which I'll never used them all. In this case, is the swap area still important? Even though my computer will go sometimes in sleep/hibernate?

---

### Post by sudodus on 2016-02-13
Welcome to the Ubuntu Forums :-)

I suggest that you boot into a live session with the Ubuntu DVD or USB drive. Start ***gparted*** from dash and remove the primary partition with Ubuntu. Instead you use that drive space to create an ***extended partition***. Inside that extended partition you can create a big logical partition for Ubuntu's root file system, and a small logical partition for swap.

If you intend to hibernate, you need at least as much swap as RAM (in Gibibytes), so if you have 4 GiB RAM, I suggest at least 4.4 GB swap. (1 GiB = 2^30 = 1024*1024*1024 bytes approx 1.074 GB). Otherwise it is probably enough with 1 or 2 GB swap.

---

### Post by SnuKies on 2016-02-13
Oh, thanks! I'll try that right away. But now another problem :

This is my first dualboot ever. But whenever I start my laptop, it does not let my choose to boot from W7 and ubuntu. It loads directly windows 7. Any more help, please?;)

---

### Post by Rocky_Bennett on 2016-02-13
How much RAM does your system have? If your system has 4 GB of RAM or more, you really do not need a swap partition. But if you feel that you want a swap partition, then you can follow sudodus's recommendation that he outlined. While you are at it, if you create an extended partition then you can create a separate partition within that for your /home as well as for /boot and /swap. It is all up to you how you want to set up and maintain your partition set up.

On a side note. I have 16 GB of DDR3 RAM and I still have a swap partition set up, just for the heck of it.

---

### Post by SnuKies on 2016-02-13
I have 8 GB of DDR3 RAM.:)

Now, replying to sudodus' comment, Gparted does not allow me to delete my partition with ubuntu.

---

### Post by sudodus on 2016-02-13
1. You must boot from another drive, and I suggest that you boot from the DVD or USB drive, that you used to install Ubuntu.

2. If the partition is mounted, it is locked (a lock symbol) and you must unmount it (with gparted). After that you can delete it (or edit in general).

While you are booted into the live system 'Try Ubuntu' from the DVD or USB drive, you can do some other things.

- Check if you are running in BIOS or UEFI mode. From a terminal window, run the following command line:

```
test -d /sys/firmware/efi && echo efi || echo bios
```

- Display the partition table with the following command lines:

```
sudo parted -ls  # ... space minus ell ess

sudo lsblk -fm
```

- Show which version of Ubuntu you are running

```
lsb_release -a
uname -a
```

Please [copy and paste and] post the output of these commands into a reply and put it within [noparse]```
tags
```[/noparse].

---

### Post by grahammechanical on 2016-02-13
All will be revealed when you supply the above requested information. This is what interests me:

> Now, on windows I have 2 partitions (C: for system and D: for files).  But there is also that partition that windows has created on its  install.

If you have MBR partitioning with its 4 primary partition limit, you may find that Windows has used up 3 of 4 allowed primary partitions and the Ubuntu installer has made use of the 4th allocation by creating an Extended partition and then inside the extended partition the installer may have created 2 logical partitions. One for Ubuntu and one for swap.

It is unusual for the installer not to create a swap partition. If we have MBR partitioning and a blank hard disk and we use the Erase disk and install Ubuntu option the installer will create 2 primary partitions. One for Ubuntu and one as an extended partition and inside the extended partition there will be a logical partition for swap.

Regards.

---

### Post by oldos2er on 2016-02-13
> **SnuKies said:**
> I have 8 GB of DDR3 RAM.:)

Now, replying to sudodus' comment, Gparted does not allow me to delete my partition with ubuntu.

If you just delete your Ubuntu partition, you will break grub and your system will be unable to boot. If you want to remove Ubuntu, first restore Windows' boot loader, then you can safely delete the Ubuntu partition from Windows.

---

### Post by SnuKies on 2016-02-13
I want to thank you all, sudodus, Rocky_Bennett, grahammechanical and oldos2er. I did it :D

I've delted my ubuntu partition from Gparted, made 3 partition ( / , swap and /boot ), installed ubuntu and done it! :D 

And both work!

Thank you guys, I greatly appreciate you all.

---

### Post by Rocky_Bennett on 2016-02-14
I'm glad that you have it all set up. If you monitor your system using the system monitor that is built into Ubuntu, I bet that you will see that you never use any of your newly created swap area. It is nice to have anyway, just because.

---

### Post by Rocky_Bennett on 2016-02-14
I wanted to revisit this thread to ask the OP if the drive in question is an old fashioned hard drive or a SSD? If it is an SSD, you might want to reconsider having a swap partition.

---

