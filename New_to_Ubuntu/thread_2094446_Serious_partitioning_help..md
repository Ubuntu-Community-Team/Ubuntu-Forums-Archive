---
title: "Serious partitioning help."
date: 2012-12-13
forum: New to Ubuntu
---

### Post by N3XU5 on 2012-12-13
How much gigs should I allocate to these partitions /boot, /, /home, /tmp, /usr, /var and /srv

---

### Post by oldfred on 2012-12-13
0, 25, rest of drive, 0,0,0,0 Unless a server. Then it depends on use.
More explanation here:
       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

    And you did not ask about swap. Either 0, 2GB or the size of RAM in GiB not GB to match RAM size. Only larger swap if you want to hibernate. 

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

    For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by N3XU5 on 2012-12-13
Thanks

---

### Post by oldfred on 2012-12-13
If planning on multi-booting do not share /boot nor /home. Sharing leads to major problems as files may be in same location but then different versions.

If you encrypt /home then swap is encrypted. Best not to so you can share swap. But do not share swap if hibernating. 

Better to keep /home inside each install and create a shared data partition for any data you might want in each install. I have many Ubuntu's all sharing the same data partition with Music, Video, Documents etc folders linked to each install.

---

### Post by N3XU5 on 2012-12-13
So, should I have two boot partitions?

---

### Post by N3XU5 on 2012-12-13
I am trying to perfect my boot partition layout. What layout do you recommend?

---

### Post by N3XU5 on 2012-12-13
This Is the one that I use now:

/boot 2.3 gigs

/(For backtrack)

Swap 4.7 gigs

Extended: 

/(for ubuntu)

/home

---

### Post by N3XU5 on 2012-12-13
I've also been told to adjust the sizes. Can someone please answer my question. ;)

---

### Post by N3XU5 on 2012-12-13
Swapfile vs. a swap partition. isn't  a swap partition faster?

---

### Post by haqking on 2012-12-13
> **N3XU5 said:**
> I've also been told to adjust the sizes. Can someone please answer my question. ;)

1st be patient, only bump every 24 hours.

2nd, you havent said what sizes you have for all, and you also asked a similar question where you were answered quite fully, it all depends on what you add.

your other thread is here [http://ubuntuforums.org/showthread.php?t=2094446](http://ubuntuforums.org/showthread.php?t=2094446)

---

### Post by lisati on 2012-12-13
Threads merged.

Please be patient: we're all volunteers here with a variety of knowledge and skills.

---

### Post by Kirk Schnable on 2012-12-13
> **N3XU5 said:**
> This Is the one that I use now:

/boot 2.3 gigs

/(For backtrack)

Swap 4.7 gigs

Extended: 

/(for ubuntu)

/home

Better? What's wrong with this one?

> **N3XU5 said:**
> I've also been told to adjust the sizes. Can someone please answer my question. ;)

Adjust the sizes of the partitions?  Why?

I am not really sure what you want, or what prompted you to think your partition layout needs improvement. 

Could you enlighten us as to the cause of your concerns?

---

### Post by Mr. Hibba on 2012-12-13
I'd generally prefer a swap partition.  That way you can put it at the end of the disk and save the read/write head some wear and tear.  

I'm not really sure about speed differences between the two.  As for the swap file, it seems kinda like it would depend on what size the file is, where it is on the disk, and how fragmented it would get.  

Mr. Hibba

---

### Post by N3XU5 on 2012-12-13
/boot 2.3 gigs

/(home for backtrack) 145 gigs

swap 4.7 gigs

extended:

/(For ubuntu) 50 gigs

/home 45 gigs

/var 45 gigs

---

### Post by Kirk Schnable on 2012-12-13
> **lisati said:**
> Threads merged.

Please be patient: we're all volunteers here with a variety of knowledge and skills.

That was cool... I replied, and suddenly this thread was two pages long. XD

---

### Post by N3XU5 on 2012-12-13
Backtrack has problems when I install SElinux on ubuntu 12.10. What should I do?

---

### Post by Kirk Schnable on 2012-12-13
> **Mr. Hibba said:**
> I'd generally prefer a swap partition.  That way you can put it at the end of the disk and save the read/write head some wear and tear.  

I'm not really sure about speed differences between the two.  As for the swap file, it seems kinda like it would depend on what size the file is, where it is on the disk, and how fragmented it would get.  

Mr. Hibba

I also would prefer a swap partition, mostly because a swap file could cause file system fragmentation, I would think...

---

### Post by haqking on 2012-12-13
> **N3XU5 said:**
> Backtrack has problems when I install SElinux on ubuntu 12.10. What should I do?

how many questions do you want to ask before the others are answered to your satisfaction

also "problems" is a little of a broad statement.

Ubuntu 12.10 uses apparmor

---

### Post by lisati on 2012-12-13
@n3xus: I've merged your question about swap file versus swap partition into this thread, as your decision is likely to impact on how you eventually decide how to organize your partitions.

---

