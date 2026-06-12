---
title: "is swap partition necessary after installation?"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by harimurugan on 2012-03-26
I have dual booting of win8 and ubuntu.. I have one partition for dell utilities, other for Ubuntu, one for swap and other one for windows.. now I need to separate windows drive but I can be make free space(un allocated) but I am not able to convert into drive.. 
 
wat I thinking is to delete the swap partition so that I can get one more partition to extend bcz I can able to divide the whole drive into 4 partition only.. I cant able to do in ubuntu.. when I tried in windows, it changed my drive into Dynamic one from basic and it also lead booting of windows only..
 
can any one help me how to separate my windows without changing from basic to dynamic.. if I deleted the swap I can partition my windows drive in Ubuntu itself so help me out..

---

### Post by Bucky Ball on 2012-03-26
Four primary partitions = limit for one physical drive. Once they're dynamic you have a headache. 

What you need to do is make the fourth partition an extended partition. Inside the extended partition you can put as many logical drives as your machine can handle and it is still considered to be four primary partitions on one physical hard drive.

Ubuntu will live happily on a logical drive inside an extended partition, Windows will not.

---

### Post by mastablasta on 2012-03-26
swap partition is sort of like pagefile in windows. when the computer goes to sleep and such data will be written to swap. also if you use some big programmes swap might get used.

---

### Post by harimurugan on 2012-03-26
> **Bucky Ball said:**
> Four primary partitions = limit for one physical drive. Once they're dynamic you have a headache. 
 
What you need to do is make the fourth partition an extended partition. Inside the extended partition you can put as many logical drives as your machine can handle and it is still considered to be four primary partitions on one physical hard drive.
 
Ubuntu will live happily on a logical drive inside an extended partition, Windows will not.
 
I have swap partition if I changed to extended partition ll it cause any trouble??? weather I have to again re-install OS if I changed the swap???? 
 
for swap partition I have to choose that partition as linux-swap then how can I change it to extended one???

---

### Post by harimurugan on 2012-03-26
> **mastablasta said:**
> swap partition is sort of like pagefile in windows. when the computer goes to sleep and such data will be written to swap. also if you use some big programmes swap might get used.
 
I wont use sleep or hibernate but I use matlab2010ra often.. I don't know how much physical memory it ll take.. any idea??

---

### Post by harimurugan on 2012-03-26
> **Bucky Ball said:**
> Four primary partitions = limit for one physical drive. Once they're dynamic you have a headache. 
 
What you need to do is make the fourth partition an extended partition. Inside the extended partition you can put as many logical drives as your machine can handle and it is still considered to be four primary partitions on one physical hard drive.
 
Ubuntu will live happily on a logical drive inside an extended partition, Windows will not.
 I thought doing this:
 
1.delete the swap partition (because I already have 4 partition)
2.now I ll make unallocated space(which I got from windows drive) as extended partition
3.now I again make swap partition since I have created extended partition only there wont b problem of max no partition(right???)
 
if I did like this wat ll happen.. did any data loss occur? ll I hav to install Ubuntu os windows after this.. will those steps format any drive???

---

### Post by pqwoerituytrueiwoq on 2012-03-26
you can safly delete swap just remember to update your fstab file accordingly
if you recreate  a swap partition don't forget to update [FONT=Courier New]/etc/initramfs-tools/conf.d/resume[/FONT] with the new uuid

if you have no swap parathion you will not be able to use the hibernate feature you will probably want a swap partition if you only have something like ~500mb or ram
  youcan have 3 primary partitions +1 extended partition and the extended partition can have 4 partitions in it

since you are installing windows after Ubuntu you wil nee to reinstall grub (or at least the mbr)

---

### Post by oldfred on 2012-03-26
While a second install of Windows can be in a logical partition, it will depend on booting from the first install of Windows in a primary partition. Best to have all Windows installs in primary partitions.

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

You may be able to change from primary to logical if partitions are next to the current extended. You cannot have two extended partitions. As with any major system change be sure to have good backups.

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by HermanAB on 2012-03-26
Howdy,

To fully understand how to manage the virtual memory system, you need to read the 'swapon' man page.

Theoretically, you do not need swap, if you have enough RAM.  However, the suspend system uses the swap space to save the machine state and if you do heavy internet browsing, then your machine will eventually slow down and stop if you don't have swap space.

You could however use a swap file.  Contrary to conventional wisdom, a Swap file is not any slower than a swap partition.

---

### Post by Bucky Ball on 2012-03-26
> **pqwoerituytrueiwoq said:**
> ... the extended partition can have 4 partitions in it ...



Theoretically, the extended partition can have as many logical drives in it as your hardware can handle; there is no limit ... theoretically ... ;)

---

### Post by uRock on 2012-03-26
How much RAM does your system have? If you have more than 4GB, then I'd think you wouldn't need a swap, since you do not plan to hibernate.

---

### Post by jerome1232 on 2012-03-26
> **Bucky Ball said:**
> Windows will not.
offtopic but,

I used to think this as well, turns out it can, most Win 7 installs put the boot files on a partition that is separate from the c: partition, allowing you to put c: on a logical partition.

I only know this because my netbook had 4 primary partitions and I had to work some magic to turn c: into a logical partition so I could install ubuntu without wiping out my recovery options for Win 7.

I'm not sure if this sort of thing will work on Windows 8, I've heard it's boot procedure is very different than Win7.

/offtopic

In the OP's case I would create an extended, put all Ubuntu related partitions there, then you have have up to 3 basic partitions for Windows.

---

### Post by Bucky Ball on 2012-03-27
Yes, Win will exist in an extended partition, you're right, but the screwing about, tweaking and 'working magic' is generally not worth the effort. Put it where it wants to be and will install problem free: First drive, first partition. ;)

---

