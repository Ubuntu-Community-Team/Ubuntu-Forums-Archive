---
title: "[SOLVED] not sure how to partition. i don't understand the jargon"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-11-16
hey, i have a dell mini 9. I have a 8 GB SSD.

I want to format it and install the latest ubuntu 8.10. with the help of  online guide from [www.ubuntumini.com](www.ubuntumini.com)

but i don,t understand that jargon of partition it.
back in Windows, all i do is format, pick 1 partition of FAT32 or NTFS and than just install

but, i don,t understand the steps of what root/folder/var/dir setup. and leave how much memory space for whatever partition.  its rather confusing.

I just want to install ubuntu 8.10 and leave the rest of the memory to just use for docs, and data.

can someone explain this for me?

---

### Post by SunnyRabbiera on 2008-11-16
well in ubuntu all you really need is the main root partition and the swap partition, but some guides like to add more because some folk like to have separate partitions for the home directory and such.
But on a small netbook like that you might be better off just sticking to your current install as the default ubuntu is not fine tuned for netbooks.

---

### Post by jerrynewt on 2008-11-16
Are you looking to dual boot with Windows or just install 8.10 by itself. If you just want 8.10, pop in the live cd, go to install. When the partition editor comes up, use the first choice (guided I think) and the partitions will be set up automatically for you.

---

### Post by SunnyRabbiera on 2008-11-16
> **jerrynewt said:**
> Are you looking to dual boot with Windows or just install 8.10 by itself. If you just want 8.10, pop in the live cd, go to install. When the partition editor comes up, use the first choice (guided I think) and the partitions will be set up automatically for you.

well on such a small system a dual boot is ill advised, especially if he is used to windows applications and such.
On netbooks a dual boot is kind of useless.

---

### Post by Virtualboxbuntu on 2008-11-16
Okay, from what I understand, you don't want Windows, just Ubuntu. Good, that makes it a whole lot simpler. :)

From what I've read about Dell Minis, they don't have CD drives. So I don't know how you'll install Ubuntu. But I might be wrong.

Anyway, pop it in your CD drive and restart. Click Install and go through all the stuff until you get to partitioning. Choose Manual.

1. Click the Fat32 or NTFS partition. Click Delete Partition.
2. Repeat Step 1 for any other partitions there are.
3. Click the Free Space. Click New Partition.
4. Enter these settings:
---- Primary Partition
---- Size: 1024 mb
---- Type: Swap
5. Click the remaining free space. Click New Partition.
6. Enter these settings:
---- Primary Partition
---- Size: Max
---- Type: ext3
---- Mount point: /
7. Proceed with the install!

WARNING: This will delete Windows. Only do this if you do not need Windows.

---

### Post by InfectedWithDrew on 2008-11-16
As previously mentioned, simply allow it to use the guided partitioning.

If you want a bit of explanation, on a 8GB drive, you would probably have two partitions: 7.4 GB ext2, and 512MB swap.  ext2 is a Unix filesystem (like NTFS for Windows) and swap is a special filesystem that is used as a sort of slow RAM (it saves inactive program data, letting your RAM do more important things).

That jargon is the different directories, much like Windows has C:\WINDOWS\system32 and such and such.  "root" would be like your C:\, for all intents and purposes.  "/folder/var/dir" is basically it filling in an example directory (I believe).

---

### Post by starcannon on 2008-11-16
With your current setup, you will likely want to put / on a 4gb partition, and /home on a 4gb partition, and not use swap (indeed the default ubuntu install on mini9 has no swap either, just means you can't hibernate; suspend/resume works fine though).

It might be a good investment to pick up a 16gb multimedia card as well (about $30)
I'm grabbing this one for my 16g Mini9
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820211300](http://www.newegg.com/Product/Product.aspx?Item=N82E16820211300)

Anyway, that'll get you a reasonable amount of space for everything. Then you could give / the full 8gb ssd and /home the 16gb sdhc, if you want to dual boot you may want to consider a 32gb sdhc card. Then perhaps /windows on the ssd, and set 10gb for / on the sdhc, and 22gb on the sdhc for /home, again not bothering with a /swap.

GL and keep it fun.

---

