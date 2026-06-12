---
title: "Resizing linux partition"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by AlexEttels on 2013-05-11
Hello!

I have Ubuntu 13.04 installed on my (almost) my whole hard drive..and I would like to resize the main partition so I could install Windows 7 as well 

The problem is..when using GParted (haven't tried anything else) I can't resize it. I tried to swapoff the swap partition and I still couldn't resize it.

Here's a screenshot of my current partition:

[IMG]http://img515.imageshack.us/img515/4715/screenshotfrom201305111.png[/IMG]

Thank you!

---

### Post by pootan on 2013-05-11
You have to run GParted off a Live CD or USB because it can't resize a mounted Partition. That little key symbol in the Partition section shows if the drive is mounted or not.

---

### Post by Impavidus on 2013-05-11
+1 to the live cd.

Also, have you read [this]("https://help.ubuntu.com/community/WindowsDualBoot#line-67")?

---

### Post by AlexEttels on 2013-05-11
I managed to resize the *sda1* partition, should I move the swap and extended partition? 
I tried expanding the extended partition and then moving the swap partitionbut it gave me a weird error on resizing extended partition :
"Unable to satisfy all constraints on the partition"

---

### Post by pootan on 2013-05-11
Ubuntu will find the swap file from that location. Make sure you read what Impavadus linked to and write some info down if you are relying on that machine for internet access in case you have problems at boot.

---

### Post by AlexEttels on 2013-05-11
How can I backup the MBR?

---

### Post by pootan on 2013-05-11
You shouldn't need to backup the MBR.

You can use a Live CD/DVD and use the program called boot-repair to repair grub (which is the Ubuntu boot loader) after Windows has over written it.


[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Impavidus on 2013-05-11
Just as it says:> 
2. Backup the MBR e.g. **dd if=/dev/sda of=/mbr.bin bs=446 count=1 **

In other words, open a terminal and use that command.

But pootan's option may be saver.

---

