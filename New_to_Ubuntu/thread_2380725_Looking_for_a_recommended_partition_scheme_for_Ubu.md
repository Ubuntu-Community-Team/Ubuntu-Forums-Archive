---
title: "Looking for a recommended partition scheme for Ubuntu 17.10"
date: 2017-12-21
forum: New to Ubuntu
---

### Post by dorian4 on 2017-12-21
Hi, I'm not really new to Ubuntu, but I'm doing a clean install on my laptop of both Windows 10 Insider Preview 17063 and Ubuntu 17.10.

I'm just looking for a more "actual" partition scheme. I've searched for some online and I've found a lot from 2010-2013, but things have changed until then. I've seen people considering /boot, /var partitions irrelevant and also people arguing over the swap size.

So, I got a UEFI setup computer, 16GB RAM DDR3 (laptop) SSD Samsung 540 EVO and I want to share the space between Windows (daily work) and Ubuntu (Android Development).

Can anyone give me some recommendations for partitions and their sizes? For now I got:

/boot - 1GB
/ - 20GB
/home -100GB
/var - 6GB
swap - 32GB

50GB Over Provisioning space for SSD

The rest is allocated to the Windows and the recovery/boot partitions.

Thanks!

---

### Post by Impavidus on 2017-12-21
You need a /boot partition if you want to use full system encryption or LVM, which is an additional layer of partitioning. That may be useful if you want to be able to change partitions later, but if your needs are simple it isn't hard to get everything right on your first attempt. So only use a /boot partition if you really need it. If so, 1GB is fine. Don't make it too small and keep it clean. The forum is full of threads of people who got a full /boot partition.

A /var partition may give some protection in the very rare event of overflowing log files or may be useful if you want a different device or partition type because of different usage pattern. For most users a /var partition doesn't make sense. My /var directory is about 750MB.

The rule to make your swap twice the size of your ram made sense back in the days when computers had 256MiB ram, but is obsolete now. If you want to hibernate (disabled by default because not very reliable, but some users use it), make swap slightly larger than ram. Else, you will probably never use swap, but to get a more graceful crash in case you do run out of memory you could make 2GB of swap anyway. This will cause slowdown when you run out of memory and give you the opportunity to close some programs of your choice, instead of seeing some programs killed at random. Ubuntu 17.10 will default to a swap file.

For the / partition 20GB is fine.

What is left can be used as /home partition or a data partition, to be mounted wherever you want. Maybe you want a data partition shared by Windows and Ubuntu.

On UEFI systems you'll get an EFI partition, shared by Windows and Ubuntu.

---

### Post by dorian4 on 2017-12-21
Thanks for the answer.

I compile a lot of stuff on my laptop (working with AOSP code) and wanted to get some of the things right.

So as I don't use hibernation or encryption I guess I can delete the /var /boot and reduce the swap to 2GB.

---

