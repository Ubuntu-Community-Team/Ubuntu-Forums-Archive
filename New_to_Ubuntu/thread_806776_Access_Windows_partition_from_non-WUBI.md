---
title: "Access Windows partition from non-WUBI"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-05-25
This post is in two sections: 1. A rave about WUBI. 2. A question about accessing Windows files.

1.

For the past few years, I've been gradually moving over to Open Source, with a view to getting rid of Windows eventually.

Well, I finally took the plunge when I discovered WUBI. I can't believe that it doesn't pay a prominent role on the Ubuntu website -- it's so easy, so easy! I would still be waiting if I hadn't come across WUBI. =D> Now my son is also experimenting with Ubuntu.
(For newcomers: You can find it at (**link Removed**)

The WUBI website warns that it's slower than a native installation. Despite this, I find it like lightning compared to W98, XP and Vista (even when Vista's running on a good machine, which mine is).

2.

Well, I thought, perhaps I should lose my WUBI and go for a native installation, because WUBI does have a couple of (minor) restrictions. It's pretty easy; Vista lets me create a new partition no problem.

However, before I do, I wanted to check something.

With WUBI, it's as easy as pie to access my Windows files from Ubuntu.

**Question: If I get rid of WUBI and load Ubuntu onto a separate partition, can I still easily access my Windows files from my Ubuntu installation?**

(I use Windows Vista Home Premium.)

---

### Post by Sarah L on 2008-05-25
Yes, Ubuntu has support for the NTFS format and will recognize your Windows partition. You can, however, set it so that your Windows partition does not mount automatically. Then, if anyone wants to manually mount it in Ubuntu, they will have to provide your admin password.

---

### Post by diablo75 on 2008-05-25
Yes, and 8.04 will list your Windows partition in your Places menu by default.  No need to manually edit your fstab last I checked...  So everything should work out rather smoothly.  Something I was thinking about earlier today is the fact that Wubi installs are still rooted in FAT/NTFS partitions, so file fragmentation is likely a problem for those who isntall using this method, unlike a native install on ext3....

---

### Post by Paddy Landau on 2008-05-25
> **Sarah L said:**
> Yes, Ubuntu ... will recognize your Windows partition. You can, however, set it so that your Windows partition does not mount automatically.
I'm quite happy with automatic mounting; security isn't an issue in my location and with my data.

> **diablo75 said:**
> ... Wubi installs are still rooted in FAT/NTFS partitions, so file fragmentation is likely a problem for those who isntall using this method, unlike a native install on ext3....
Nevertheless, for a non-technical user, WUBI is a brilliantly safe and easy way to experiment. Especially for people who are unsure about making partitions.

Thanks to both Sarah and Diablo.

I shall attempt to replace WUBI with a native installation on a non-busy weekend (next weekend, I hope). \\:D/

---

