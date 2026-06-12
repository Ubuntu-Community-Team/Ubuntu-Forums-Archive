---
title: "Partitioning Help"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Skeet on 2008-05-20
I have been tinkering with Ubuntu 8.04 for a while now and i've decided to run it as my main OS (over Vista).

I have 2 hard drives currently.

1 x 20GB IDE
1 x 250GB SATA2

I had Ubuntu on the 20GB hard drive to test it out. I am planning on removing this drive as its slow and noisy, and installing Ubuntu on the 250GB.

Currently I have Vista installed on the 250, with a Storage partition of around 120GB (off the top of my head). and the rest is system space.

So just to clarify (taken from Ubuntu installation partitioner)
```

/dev/sda - *(20GB Hard Drive)*
sda1 - ext3 - 19190GB Space
sda5 - swap - 880MB Space

/dev/sdb - *(250GB Hard Drive)*
sdb1 - ntfs - 83896GB Space - Windows System Partition
sdb5 - ntfs - 12567GB Space - NTFS formatted Storage Drive

```

I am wanting to;
 - Format the 20GB so I can remove it
 - Format the 83896GB partition for Ubuntu use.
 - Keep the storage drive intact for further use within Ubuntu.

How can I do all this? I know it might be a silly noob question, but I really don't want to lose any data from that Storage drive.

I presume i'll have to make a small 880MB swap partition along side the ext3?

Thanks in advance,

Skeet

---

### Post by Skeet on 2008-05-20
*Bump*

Seeking a quickish response. Needing to get this reformatted and ready asap.

---

### Post by rockerphil on 2008-05-20
well it's pretty simple, just boot from the Ubuntu live CD and mount your file systems so you can use Gparted to format the 2 drives. then just remove the 20 GB HDD and replace the primary drive with your 250 GB HDD and go with a standard install

---

### Post by tjwoosta on 2008-05-20
i dont quite understand what your question is

all you will have to do is pop in the ubuntu live cd then go to System-Administration-Partition Editor (this is gparted you can resize, delete, or create new, whatever you want to do to the partitions)

(btw the reason for using the live cd to do it is because you cant have the drive mounted while trying to change it)

and yes you would need to make a swap partition (preferably like twice the size as your ram)  so if you have 256mb ram then make the swap 512mb if you have 1024mb ram then make the swap 2046mb and so on

---

### Post by Skeet on 2008-05-20
But won't it reformat the Storage partition on the 250 as well?

---

### Post by tjwoosta on 2008-05-20
> But won't it reformat the Storage partition on the 250 as well? 

no, when you go into gparted it will show you the two partitions separatly, so you can just click on the vista one and delete only that partition

---

### Post by Skeet on 2008-05-20
Oh I see. Thanks alot, I wasn't sure because I heard that in previous versions it's known to format the whole hard drive, not just the partition you select.

:lolflag:

---

### Post by rockerphil on 2008-05-20
just remember that your storage partition is in NTFS format, and Linux tends to handle ext2/3 partitions better than NTFS, although you can manage an NTFS partition pretty decently if you've got the right programs installed

---

### Post by Skeet on 2008-05-20
I'll probably end up sorting out the crap on the Storage drive and try get the size down, copy it to another hard drive (borrow from a friend), reformat the partition in ext3 (or ext2, not sure of the difference) and put all the stuff back on. However, if I do decide to dual boot with Windoze again, I cannot access the files on there.

---

### Post by tjwoosta on 2008-05-20
> ext3 (or ext2, not sure of the difference)

there is a difference and you probably should learn it before deciding which way to go  (check out this thread)
[http://www.linuxforums.org/forum/installation/2487-ext2-ext3.html]("http://www.linuxforums.org/forum/installation/2487-ext2-ext3.html")

---

### Post by Skeet on 2008-05-20
I did as you said and all worked fine until I rebooted into Ubuntu after installation. I get to the grub menu and it comes up with

```
Error 17: Cannot mount selected partition
```

I currently have the 80GB Ubuntu reserved partition mounted at / is that correct?

What does this mean and how can I fix it?

---

### Post by tjwoosta on 2008-05-20
hmmm...  i dont know

well here is a better idea for you to install (i think it is the easiest way, also it will do all the setup automatically)


go back to gparted on the live cd

delete the newly installed ubuntu partitions (swap and ubuntu)  **leave unallocated**

after its deleted click the install icon thats on the desktop 

when it gets to the part where it asks you how you want to install just select "Guided Install: Use Largest Continuous Free Space" (this will install to the unallocated space) 

this method will automatically setup your swap partition and GRUB for you

---

