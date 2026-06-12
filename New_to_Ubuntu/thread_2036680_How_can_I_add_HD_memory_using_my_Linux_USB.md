---
title: "How can I add HD memory using my Linux USB?"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by mcimafonte on 2012-08-02
Hello,

I used Lili - LinuxLive USB creator to boot Ubuntu 12.04 off of my 2GB USB. Lili allowed me to use 1.1 GB of memory for persistent data. My goal in using Ubuntu was for mathematical programming in C and Mathematica. I want to download these software packages and save documents, as I will be using Linux quite frequently for my school work. I would also like to put my iTunes on Ubuntu. However, I realized the size of my "HD" is only the 1.1 GB on my USB. Is there a way to add more HD space and not be limited to 1.1GB? I've noticed that no cloud storage service offers substantial space without having to pay monthly fees. Is my only solution to partition my hard drive between Windows 7 and Ubuntu 12.04? I would like to avoid partitioning if possible. Thank you for your help! :D

---

### Post by Mark Phelps on 2012-08-02
> I would also like to put my iTunes on Ubuntu. 
Basically, this won't work.  If you search the forums about this, you will see folks have used alternative Linux apps.

> However, I realized the size of my "HD" is only the 1.1 GB on my USB. Is there a way to add more HD space and not be limited to 1.1GB? I've noticed that no cloud storage service offers substantial space without having to pay monthly fees. Is my only solution to partition my hard drive between Windows 7 and Ubuntu 12.04? I would like to avoid partitioning if possible. Thank you for your help! :D
If you want more "disk" space, and you only need that for data, not for applications, if you have a DATA NTFS partition on your drive, you can mount and use that.  But, if you only have SYSTEM partitions (meaning the Win7 Boot partition, Win7 OS partition, Recovery partition), then do NOT mount those -- as doing so risks corrupting the Win7 OS and rendering it unbootable.

The solution would be to create an NTFS Data partition -- but you first need to check in Win7 Disk Management utility to see if you already have 4 partitions in place -- which is the typical default these days on PCs preloaded with Win7.  If you do, you can NOT create any more partitions -- and will be faced with some difficulty having to remove one, resize the others, and create a new partition.

---

### Post by Hadaka on 2012-08-02
while you stated you dont want to partition your hardrive, a dual boot
Ubuntu/win7 is really the best way to go about doing what you want.
you can load Ubuntu 12.04 os on your harddrive and then use it ONLY
as an os,with the os and security updates, 12.04 will use aprox 5 gig.
at present with your 2gig usb...you are only using the "try ubuntu" format
not the entire os and running 12.04 from a usb is dirt slow along with extra
stress and excessive heat on the system processor as it takes more resource,
 so i suggest...dual boot..and then acquire a 16 or 32 gig usb
to run all your c language and store all your programs . your current 2 gig
stick should hold your itunes stuff. I currently am using a dual boot laptop
with a simple 40 gig internal hd, 2 gig ram, and loaded with ubuntu 11.10 and
ubuntu 12.04 dual boot. all my program applications and data i want to keep
is stored on 16 and 32 gig usb drives,which is more logical anyway..never have
to worry about backing up the hd..everything is already  stored on usb. I have
had zero problems running my system this way...and its very heavily used.
hope this helps.

---

### Post by audiomick on 2012-08-02
> **mcimafonte said:**
> Is my only solution to partition my hard drive between Windows 7 and Ubuntu 12.04?

Yes.

Well not quite. You could follow Mark Phelps' advice and just add an NTFS Data partition and keep using Ubuntu from the USB stick, but that involves partitioning work as well.

---

### Post by grahammechanical on 2012-08-02
You say this:

> I've noticed that no cloud storage service offers substantial space without having to pay monthly fees.

How much, in your opinion is "substantial?"

Have you seen this?

[https://one.ubuntu.com/]("https://one.ubuntu.com/")

Regards.

---

### Post by mcimafonte on 2012-08-02
I think I will approach the situation as prescribed by Hadaka! Thank you guys!!!!!

---

