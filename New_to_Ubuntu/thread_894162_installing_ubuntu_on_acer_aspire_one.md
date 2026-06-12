---
title: "installing ubuntu on acer aspire one"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Num1Deluxe on 2008-08-19
Hi,
I just recieved an Acer Aspire One 120Gg Windows XP Version and would like to install ubuntu on I found some threads on how to do this with a usb drive and to use the newer version 8.04.1. Well I downloaded the iso and burned a disk. I would like to install from the disk and not from the live usb but have no theads on this way of installing ubuntu. So I went and tried to install it from the disk and ran to numerous problems. The big thing that I am having a problem with is the patitioning part in which I have no clue on.
I would like to keep the partition with xp and douel boot, but When I tried to do this with The install cd I have not been able to understand how this proccess works I have tried Manual mode and the first option where it guides you through the partition proccess. I have had no success at this. I have seen different messages such as to small to problems with setting up a swap file. Would it be possible to get some help with this.

Help and Thanks,

---

### Post by jualin on 2008-08-19
If you want the "easy way out" then you can use Ubuntu's Wubi installer (which doesn't require partitioning), now for the hard way ...
Linux requires 2 partitions to run, a SWAP partition (twice your RAM size) and a root or "/" partition. This partition need to have the Ext3 file system or some file system compatible with Linux (NTFS file system is only for Windows). You will need to basically resize the XP partition, create a SWAP partition (twice the size of your RAM) and the root partition (main Ubuntu partition which should have the mount point "/") If you need a further tutorial check out the guide on my signature on how to Dual Boot Windows and Ubuntu. Good luck!

---

### Post by jualin on 2008-08-19
I forgot to mention that for the Wubi installer, you need to insert the latest Ubuntu Live CD when using Windows and then just follow the instructions on the screen. Make sure you select the "Install within Windows" option. Feel free to ask anything else you may need.

---

### Post by Num1Deluxe on 2008-08-19
Thanks jualin,
I will try that tonight. I did not know about the a SWAP partition (twice your RAM size),  I was trying with ext2 on the main part. and a / mount point and did creat another part. with ext3 and a / moint point as well so I created 2 partitions the tried to procced when it the told me that I did not create a swap file. So maybe I am confused on where I create the swap file in the proccess.
I will give the tutorial a try tonight. Plus I have partition magic in which I created a second partition before I started the install. Can I do that?
I did use about 10 Ggs of space. I checked out the tutorial and I am still not sure where to create the swap part. where am I going wrong here?

---

### Post by Num1Deluxe on 2008-08-19
Well Just about given up on this I keep getting stuck on 4 of 7 on the manual mode a new partition option is not available and I am not sure what to do next. Help

---

### Post by Num1Deluxe on 2008-08-20
I got this to install finally. I believe my problem was I had to create a patition 12 Ggs in size then part 4 of 7 I had to delete the partition to free up space on that partition I resized it to 10 Ggs by making a new part. (that option was available at this point) Then I created a new part. to the remaining free space which was 2 Ggs and when selecting to create new part. the option to make it a swap file was there which I selected and now it is installing.

---

### Post by jualin on 2008-08-22
Sorry for taking so long to respond. Did you get everything to work?

---

