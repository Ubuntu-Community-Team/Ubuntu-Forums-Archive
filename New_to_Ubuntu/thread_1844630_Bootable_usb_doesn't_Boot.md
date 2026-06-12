---
title: "Bootable usb doesn't Boot"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by setu_gomes on 2011-09-15
Hi, I was trying to use startup disk creator tool to make a usb installation. 
every process is done smoothly, but when I boot with the flash drive, it says Boot Error, and doesn't start installation.
I don't Know if there is anything wrong with the formatting the flash drive. I've tried many ways, including partitioning the flash drive as primary and set as active. (I've used bootable partition manager tool to do this.) I've also tried to use the Disk utility tool, that comes with Ubuntu, and tried different methods of partitioning and formatting. 
In the end, I couldn't make it happen. still it says Boot error.
I've also tried to use other program to create usb installer, like UNetbootin. But Couldn't make it happen.
I'm using Ubuntu 11.04 (natty, Kernel Linux 2.6.38-11-generic, GNOME 2.32.1

Thanks in advance

---

### Post by Rex Bouwense on 2011-09-15
This is odd because I have never had a problem with Startup Disk Creator.  Is the ISO that you are using a desktop edition?
Does your computer recognize the flash drive before you start?
What is the model of your flash drive?

---

### Post by daniell59 on 2011-09-15
I have the same problem with an old laptop. I tried everything to make it boot from a flash drive. I kept getting boot error. I gave up and did the following. I removed the HD and put it in my desktop. I then booted from that, then put the HD back into the laptop. I now have a working laptop with Ubuntu 11.04. Maybe there is a better solution, but I cannot think of one.

---

### Post by P05TMAN on 2011-09-15
When you try to boot from the USB, do you see a grub error?

---

### Post by setu_gomes on 2011-09-15
My ISO is desktop edition. and I can use the pen drive normally. I mean i can mount, copy file, delete file, etc. It is a 8GB kingston flash drive.

when i boot from the USB, I just see a black screen saying BOOT ERROR. and nothing else. then i've to use ctrl+alt+del to reboot.

---

### Post by candtalan on 2011-09-15
This may be useful:

I have one of my several machines which gives similar problems. I usually use unetbootin to create live USBs, and the problem machine works if  unetbootin 494 is used, but similarly it fails if a more recent unetbootin is used (549). Searching suggests that my problem machine may have a bios content which is somehow lacking, it is not an ancient machine, I replaced the mainboard a couple of years ago.

---

### Post by SirDrexl on 2011-09-15
Is the BIOS set up right?  Note that in many cases, a USB flash drive is considered a hard drive, so make sure USB HDD is selected as the primary boot device.  Try other options if that doesn't work.

---

### Post by Plumtreed on 2011-09-15
You could 'install' to the USB drive and put grub on the USB drive (when asked) during installation.

It should then boot via Grub...........suggest you format the USB drive to Fat32 before you start the install process.

---

### Post by garvinrick4 on 2011-09-15
Every once in a while after reusing flash drives for a period of time they just decide to become an
unbootable flash drive, I test dailys with USB's a lot. So then I just use them for storing data on.
Sooner or later they just wear out. If it is one you purchased recently return in original case and receipt
to store where purchased and   replace with new one. (I keep a lot of receipts and cases).

---

### Post by garvinrick4 on 2011-09-15
> My ISO is desktop edition. and I can use the pen drive normally. I mean i  can mount, copy file, delete file, etc. It is a 8GB kingston flash  drive.I believe on the 8 gig ones I used to format into two partitions of 4 gig in fat. Then install with Startup disk creator in Ubuntu in sdb1 and use the up to 4 gig space allowed for persistence. And sdb2 was then used for storing data. So as not to waste the extra 4 gig. (just a thought) 
#Hope you find out why grub will not install in that particular Kingston flash drive if you do please mark as
Solved.

---

### Post by Noniyobis on 2011-09-15
Maybe a crackgen issue. Looks like you may need to start over a usb?? Doesnt sound like a system issue unless you are not booting right because even making it 1sr boot device wont do. Youd have to change bios to make your kingston the priority boot. Again, I dont thi....

---

### Post by setu_gomes on 2011-09-16
The BIOS setup is ok. my flash drive definitely recognized as usb hdd. also boot sequence is also right.

I've tried with FAT32 format also. How to put the grub during installation? is not clear to me. it never asked me such a thing. (as it said "when asked")

I think garvinrick4 probably right. this flash drive is quite old and i've formatted and partitioned it a lot of times.

One time few months ago I boot with this flash drive, I've done something with its partitioning, but dont remember now, how I did. that's why, I think, there is something wrong with partitioning.

I've also tried to partition the flash drive into two, but it doesn't. the first partition becomes Ok, but the second doesn't, for unknown reason.

Probably Its time to buy a new Flash Drive!!! alas!

---

### Post by setu_gomes on 2011-09-16
Alright. I've used bootable disk Partition magic, and i wiped the partition of the pen drive. Which rewrite all the clusters of the pen drive, and finally worked. Thanks to all for help

---

