---
title: "Does creating a bootable usb drive wipe everything that is already on it?"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by Aftrumpet on 2012-08-21
[title]. I couldn't find anything on this, so I would like to know if I can boot Ubuntu from a USB and keep all of my other files.

---

### Post by BDNiner on 2012-08-21
I would use the entire USB drive for Ubuntu. Doing anything else would force you to create partitions on the drive and that may be more of a hassle than it is worth.

---

### Post by bodhi.zazen on 2012-08-21
No, I use a flash drive with multiple partitions all the time.

Windows (may) only recognize the first partition. So use the first partition for data, install Ubuntu into the second partition.

You will loose all data you install ubuntu into (with the exception of a separate /home partition).

---

### Post by mastablasta on 2012-08-22
> **Aftrumpet said:**
> [title]. I couldn't find anything on this, so I would like to know if I can boot Ubuntu from a USB and keep all of my other files.
 
depends what you mean here. if you install ubuntu to it and format the drive during instal, (to ext4 for exampel) then yes.
 
if however you are talking about live USB (that you create with linux live USB or unetbootin) then no. eventhough these programmes say that it will erase the data it actually doesn't (especially with linux live USb which can also "Uninstall" previous live OS).

---

