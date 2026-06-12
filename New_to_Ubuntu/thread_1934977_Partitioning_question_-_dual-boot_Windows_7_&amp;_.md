---
title: "Partitioning question - dual-boot Windows 7 &amp; Ubuntu 11"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by johnnybhai on 2012-03-03
After going through the posts in this forum (one by Richard Kempe in particular - thank you) I have come up with the following Hard Disk (280 GB) allotment scheme:
sda1: Primary 20 Gb: Windows 7 : NTFS [C:]
sda2: SWAP: 8 GB 
sda3: Primary: / (root) : 20 GB : ext3s
sda4: Extended
sda5: Ubuntu installation : 10 GB : ext3s
sda6: /home : 110 GB : ext4s
sda7: Windows Data drive : 110 GB [D drive]
 
I do not want a common drive to be shared between Linux and Windows. I will use my external drive for that purpose.
 
Does this look like an acceptable scheme? Am I allotting too much or too little space for the partitions. Am fairly new to the whole dual-boot with Linux domain. All help is hugely appreciated. Please pardon and fix my incorrect terminology where needed.
 
-thank you.

---

### Post by Lisiano on 2012-03-03
You name these 2 partitions
sda3: Primary: / (root) : 20 GB : ext3s
sda5: Ubuntu installation : 10 GB : ext3s
What do you mean by Ubuntu installation? If you mean where Ubuntu is installed then that would be / (root) in your scheme. Also the root can be placed in the Extended.

Rest looks OK to me, cept I wouldn't give Windows Data that much, maybe 20 gigs less since I personally use Linux more, your decision on this one.

As for SWAP (Also can be placed in Extended), depends on how much you have RAM and if you plan to Hibernate in Ubuntu.

---

### Post by johnnybhai on 2012-03-03
Got it, thank you Lisiano for your feedback. From what I read, I thought it was a good idea to keep the main OS files in a Primary partition. Based on that, here is the adjusted scheme:
 
sda1: Primary 20 Gb: Windows 7 : NTFS [C:]
sda2: SWAP: 8 GB 
sda3: Primary: / (root) : 20 GB : ext3s
sda4: Extended
         sda5: /home : 120 GB : ext4s
         sda6: Windows Data drive : 110 GB [D drive]
 
-thank you.

---

### Post by Lisiano on 2012-03-03
Sounds good enough now. Now that I think about itm Windows 7 requires a lot of space for a base install (Unlike Linux). Currently my install (Minus Program Files 64 and 32bit and minus Users) is taking 18GB, I don't have hibernation or a page file (swap file). So I think allotting 30GB should be better. Also the swap partition should be located after the /home partition just in case you wish to decrease/increase it. So here is a revised list.

[LIST]
[*]sda1: Primary 32 GB: NTFS - Windows 7
[*]sda2: Primary 20 GB : Ext3 - Ubuntu 11.10 /
[*]sda3: Extended
[*]sda5: Logical 110 GB: Ext4 - Ubuntu 11.10 /home
[*]sda6: Logical 8 GB: Swap - Swap
[*]sda7: Logical 110 GB: NTFS - Windows 7 Data
[/LIST]
(Note: I gave Windows 7 2 more gigs since your scheme would use up 278GB instead of the full 280GB and Windows 7 uses 2xRAM you have on a hiberfil.sys and pagefile.sys)

Remember, you should partition using either Ubuntu (As a Live CD), then install Windows, then install Ubuntu. To make it easier, you could also label the partitions (Windows, Ubuntu, Swap, Home, Data)
(Side warning, if you don't create the NTFS partitions early on, Windows will create a hidden "System" partition, it's purpose is unknown to me but it seems that it's similar to a /boot partition in Linux.)

---

### Post by audiomick on 2012-03-03
I don't know for sure, but I suspect having the Windows system partition bigger rather than smaller is a good idea.

There is no reason that I know not to have your Linux system partition / on a logical partition. Doing so might make any partition size changes that you may one day want to make a little easier. This is not critical, though.

I would put the swap partition right at the end. If you want it adjacent to your /home partition for any reason, just swap the order around. The reason for having it at the end is that I assume that it will never be altered. If it is in the middle somewhere and you want to change your other partitions, you would have to move the swap to do so. This _*may*_ cause the system to lose track of where it is, and you would have to remount it. Irritation that you can avoid if you just put it somewhere where you don't have to touch it right from the start.

Also, you may not need so much swap. If you want the sleep function to work properly, you will need about as much swap as RAM, as the computer writes the RAM contents to the swap partition when it is put into sleep mode. If you are sure that you don't want to use the sleep mode at all, you may be able to get by with as little as 1GB swap. It depends a bit on what you are doing.

I have a lot of swap, because I have 8GB of RAM on here that I bought in a moment of weakness, I have more drive space that I can poke a stick at (over 2.5 TB) and I want the sleep function to work. Otherwise, I probably wouldn't need any swap at all. The computer will run without any. I am using around a GB of RAM right now with 2 instances of Firefox open, 5 or 6 tabs in all, and Evolution and the system monitor.

Ok, I just went and started Nautilus and opened about 8 really big PDF files that I have. Now the RAM usage has gone up from 1.1GB to 1.3GB. So you see, I don't think I will ever use so much RAM that I really need any swap at all. Of course, if you are doing really intensive Video editing or something like that, it is a bit of a different story.

---

### Post by Mark Phelps on 2012-03-03
Personally, I think that 20GB for Win7 is too small.  I would go with 40GB, or if you can spare it, 50GB.  Windows needs extra space for temp files and logs. Plus, every Windows Update grows the usage in the OS partition.

---

### Post by johnnybhai on 2012-03-03
Well here's what I did. Based on the approach that I outlined above based on feedback, I tried to implement it. I have Windows 7 installed, but I want to delete it as well. So I booted up into Ubuntu, and deleted all partitions. Then I created these partitions:
sda1: Primary : Do not do anything
sda2: Primary: / (root) : ext3s
sda5: Logical : /home : ext4s
sda6: Swap
sda7: Logical : /boot : ext4s
sda8: Logical : Do not do anything (I selected Place at end for this one)

And then in "Device for boot loader installation", I picked the /boot partition (sda7). The install went through fine. But I am unable to boot up. I get a grub rescue> prompt. Do I need to make the /boot a primary partition?

Any help?

---

### Post by NikTh on 2012-03-03
> **johnnybhai said:**
> Well here's what I did. Based on the approach that I outlined above based on feedback, I tried to implement it. I have Windows 7 installed, but I want to delete it as well. So I booted up into Ubuntu, and deleted all partitions. Then I created these partitions:
sda1: Primary : Do not do anything
sda2: Primary: / (root) : ext3s
sda5: Logical : /home : ext4s
sda6: Swap
sda7: Logical : /boot : ext4s
sda8: Logical : Do not do anything

And then in "Device for boot loader installation", **I picked the /boot partition (sda7)**. The install went through fine. But I am unable to boot up. I get a grub rescue> prompt. Do I need to make the /boot a primary partition?

Any help?

No. In Device for boot loader installation you must pick . dev/sda. The /boot partition no longer needed. Partitions you must create are root and swap , and if you want /home. 
Now you can reinstall grub or you can reinstall all the system.
Here is the easy automatic way to restore grub and make your system work again --> [http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

---

### Post by johnnybhai on 2012-03-04
I went with this now ... 

sda1: Primary : Do not do anything
sda2: Primary: / (root) : ext3s
sda5: Logical : /home : ext4s
sda6: Logical : /data : ext4s 
sda7: Logical : Swap : ext4s
sda8: Logical : Do not do anything

Lets see if this works out fine.

---

