---
title: "Dual Boot Install with 3 Partition"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by emrextreme on 2012-04-26
I have 3 partiton as below,

[IMG]http://i49.tinypic.com/20609so.jpg[/IMG]

I want to dual boot with windows 7 but when i choose to install the first option, ubuntu doesn't let me choose where to install. How can install ubuntu with dual boot with win7? Thanks in advance.

---

### Post by oldfred on 2012-04-26
Windows 7 usually has another 100MB hidden boot/repair partition.

From the Ubuntu liveCD terminal post this or a screenshot from gparted.

```
sudo fdisk -lu
```

---

### Post by emrextreme on 2012-04-26
Thanks i have one other question about grubb install.

Which part should i select to install grub below  sda;sda1;sda2 or other

[IMG]http://i46.tinypic.com/e9dvzd.png[/IMG]

---

### Post by oldfred on 2012-04-26
drive sda, not partitions like sda1 or sda2 and particularly not the Windows partition. Otherwise you leave the Windows boot loader booting system and it does not see Linux at all. Grub2's boot loader with the rest of grub2 in the Ubuntu partition will let you boot both systems.

---

### Post by emrextreme on 2012-04-26
Thanks everything working now.

---

### Post by YannBuntu on 2012-04-26
> **oldfred said:**
> particularly not the Windows partition.

+1. 
I think this should not be proposed by Ubiquity. If you too, please vote:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/813387](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/813387)

---

### Post by oldfred on 2012-04-26
@YannBuntu
kansasnoob posted a similar bug in grub2 back with Lucid. I think the link you have for fixes is to meierfra's instructions since so many were making the mistake and installing grub2 to the Windows PBR.

Posted some of old links in your new bug report. It should be something they do fix.

---

