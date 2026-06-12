---
title: "Linux portable programs and best way to do dark mode in Lubuntu 20.10"
date: 2020-10-28
forum: New to Ubuntu
---

### Post by wugubee on 2020-10-28
I just installed Lubuntu 20.10 on Lenovo E450, i5-5200u, 16GB, 1TB SSD,

Before this, I use Windows 7 with 2 partitions, OS and Data,
Data contains all portable programs, by doing that, whenever I use any (mostly) all kind of Windows OS, the portable programs are just intact and I simply run it,

1. In Linux, is it relevant/make sense to have separate partition and put portable linux [COLOR=#ff0000]_**(GUI)**_[/COLOR] programs, so whenever I install new latest Lubuntu or any other Linux distro, I simply rerun the programs?
2. What is the best way to make the theme into dark mode in this new Lubuntu 20.10? I mean not just the task bar, but also windows and so on,

Thank you,

---

### Post by ActionParsnip on 2020-10-28
Lubuntu uses Openbox so if you set a dark Openbox theme you'll get what you want. There are some dark themes selectable in the default install

---

### Post by Impavidus on 2020-10-28
For 1, no, it doesn't make much sense.

Most (99%) programs you use will come from the official repositories. They have been compiled and (dynamically) linked for your specific release of Ubuntu. If you reinstall the same version of Ubuntu, they can be reinstalled from the same repositories, if you install a new version of Ubuntu, you'll get a new version from the repositories.

There are things like portable programs in Linux. Often snaps these days on Ubuntu (you'll find many forum users who don't like them), but statically linked applications too. That's the style of application most common in the Windows world (which is one reason why Windows needs more memory and disk space than Ubuntu). You could keep them on a separate partition and run them again after a reinstall, but most people don't have any such applications, other than some home-made stuff.

A separate partition for documents however is a very good idea, and the few portable programs that you might have can be stored there too. Most commonly it's a /home partition. When you create one, all files and directories in the /home/ directory will actually be on that other partition. And for the average user it will be almost invisible that it's a separate partition.

---

### Post by wugubee on 2020-10-28
my partition is
fat32, partition 1: /boot/efi
partition 2: linuxswap
btrfs, partition 3: /
btrfs, partition 4: /home (all the rest storage space)

so I assume, I set it up good enough?

---

### Post by MartyBuntu on 2020-10-28
> **wugubee said:**
> 

1. In Linux, is it relevant/make sense to have separate partition and put portable linux [COLOR=#ff0000]_**(GUI)**_[/COLOR] programs, so whenever I install new latest Lubuntu or any other Linux distro, I simply rerun the programs?



That's a matter of preference. Not everyone dual/multi boots.

---

### Post by Impavidus on 2020-10-28
> **wugubee said:**
> my partition is
fat32, partition 1: /boot/efi
partition 2: linuxswap
brtfs, partition 3: /
brtfs, partition 4: /home (all the rest storage space)

so I assume, I set it up good enough?

If you've given them sensible sizes, it's OK. Btrfs isn't very widely used (most use ext4), but it should work.

---

### Post by grahammechanical on 2020-10-28
If you need to re-install select the mount points for those partitions but do not mark your /home partition for formatting. In this way you do not lose your documents or configuration files for the default programs and also those programs that you need to re-install because they are not part of the default installation.

Regards

---

