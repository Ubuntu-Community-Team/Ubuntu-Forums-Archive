---
title: "partitioning for upgrade"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by tjefferson on 2008-04-25
Hi,
I'm trying to upgrade my Gutsy to Hardy, and I want to completely erase my old partition containing Gutsy and replace it with Hardy. How do I do this? I would upgrade through the update manager, but that's giving me some issues.

---

### Post by Drone4four on 2008-04-25
Burn a fresh 8.04 iso to a disk, but it in your drive and reboot.  Install Hardy just like you did Gutsy or Fiesty.

---

### Post by forestpixie on 2008-04-25
To overwrite your old gutsy installation when you get to the partitioning part of the install choose manual and pick that partition - edit it pick a mountpoint of / and close - tick the format box and it will do what you want. 
Make sure you pick the correct partition - be aware that if you don't have a separate /home partition all your data from there will go as well. Backup what you can't lose.

---

### Post by tjefferson on 2008-04-25
Yes, sorry, I should have said that I already did that. When I did it for Gutsy, I could just choose the partition I wanted to replace. Now I have to do it manually by editing existing partitions and I don't know what to do from there.

---

### Post by tjefferson on 2008-04-25
When it says use as (swap, Ext3, FAT16, etc.) which do I want?

---

### Post by Drone4four on 2008-04-25
> **tjefferson said:**
> When it says use as (swap, Ext3, FAT16, etc.) which do I want?

You want 1 partition at about 2GB as swap.  You want a second partition as ext3 as the rest of the disk.  Avoid FAT16 at all costs.

---

### Post by aachen on 2008-04-25
I also want to do similar thing. I have a dual boot system with Ubuntu gutsy and windows XP. Now I want to d0 a fresh install of new KDE 4 remix in place of gutsy and want to keep the XP partitions same as before without any change. When I try to install, It only shows me /dev/sda partition when I select manual mode. and says your partition #1 and #5 will be formatted. now I dont know what is this partition #1 and #5 and in which partition is my ubuntu and which partition is windows. I just know that my C drive is windows and partitions E, F and G are also NTFS. D drive is DVD drive. I was afraid that it would format windows so I quit the setup. can someone explain in simple termiinology ? and what is this mount point ?

---

