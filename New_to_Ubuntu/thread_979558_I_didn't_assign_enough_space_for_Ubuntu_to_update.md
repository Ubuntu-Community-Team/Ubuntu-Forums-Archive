---
title: "I didn't assign enough space for Ubuntu to update"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by dixcuxx on 2008-11-12
Here is my story. I chose to install Ubuntu through Windows, then every time I choose Ubuntu at the boot up screen. Now I want to update to 8.10, then there is message saying I don't have enough space in Ubuntu to update. How can I assign more space to Ubuntu? I have a lot of space in my hard disk.

Thanks!:KS

---

### Post by Crafty Kisses on 2008-11-12
Paste this in the terminal:
```
sudo fdisk -l
```
Post the results here back at the forums and I or someone else can help you.

---

### Post by dixcuxx on 2008-11-12
> **Codename said:**
> Paste this in the terminal:
```
sudo fdisk -l
```
Post the results here back at the forums and I or someone else can help you.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x204a6e6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10129    81361161    7  HPFS/NTFS
/dev/sda2           10130       38913   231207480    f  W95 Ext'd (LBA)
/dev/sda5           10130       38913   231207448+   7  HPFS/NTFS

---

### Post by dixcuxx on 2008-11-12
Can anyone help me?

---

### Post by hyper_ch on 2008-11-12
(1) when asked to post the output of a command enclose it in [noparse]```

```[/noparse] brackets. It makes it a lot simpler to read

(2) post the output of
```

df -l

```

---

### Post by dixcuxx on 2008-11-12
> **hyper_ch said:**
> (1) when asked to post the output of a command enclose it in [noparse]```

```[/noparse] brackets. It makes it a lot simpler to read

(2) post the output of
```

df -l

```

Here it is:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x204a6e6c

Device Boot Start End Blocks Id System
/dev/sda1 * 1 10129 81361161 7 HPFS/NTFS
/dev/sda2 10130 38913 231207480 f W95 Ext'd (LBA)
/dev/sda5 10130 38913 231207448+ 7 HPFS/NTFS

---

### Post by dixcuxx on 2008-11-12
seem like know about this......

---

### Post by handydan918 on 2008-11-12
Suggest installing as dual boot ("the right way!") instead of Wubi. Read some of the partitioning and installation how-to's a nd FAQs here. It's worth doing right.

---

### Post by dixcuxx on 2008-11-12
> **handydan918 said:**
> Suggest installing as dual boot ("the right way!") instead of Wubi. Read some of the partitioning and installation how-to's a nd FAQs here. It's worth doing right.

Please don't be off-topic! You didn't answer the question at all!

---

### Post by handydan918 on 2008-11-13
> **dixcuxx said:**
> Please don't be off-topic! You didn't answer the question at all!

Oh, sorry. I thought you asked

> How can I assign more space to Ubuntu? I have a lot of space in my hard disk.

So I answered :> Suggest installing as dual boot ("the right way!") instead of Wubi.

I guess I don't understand the question. I'm kinda stupid that way. 

Hyuk!

:)

---

### Post by laurielegit on 2008-11-13
> **dixcuxx said:**
> Please don't be off-topic! You didn't answer the question at all!

As much as you may hate it, this is probably the most sensible option. Don't be scared of dual-booting as it is a very common setup. There are many easy guides to dual booting, and it is really what you want.

---

### Post by Vadi on 2008-11-14
You can accomplish this: [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

But it looks complicated. I'd second the dualboot option - if you're already comfortable with Ubuntu, this would be the sensible way to go. Ubuntu sets up dualboot for you automatically during the installation.

---

