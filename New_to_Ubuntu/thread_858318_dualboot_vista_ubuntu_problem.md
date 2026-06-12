---
title: "dualboot vista ubuntu problem"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by bauer on 2008-07-13
I installed ubuntu while having vista in another partition on my hard disk. The bootloader worked properly until i choose to load vista for the first time after installing ubuntu. Then vista didnt load but the recovery choice from my hp pc launched. After that everytime i begin my system windows loads automatically and prompts me to a recovery. Now im online from the live cd of ubuntu , i typed at the terminal sudo fdisk -lu (as seen on other topics) and the results are :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26d683ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   289073609   144536773+   5  Extended
/dev/sda2   *   290893824   305305599     7205888    7  HPFS/NTFS
/dev/sda3       305305600   309317631     2006016    7  HPFS/NTFS
/dev/sda4       309325824   312578047     1626112    7  HPFS/NTFS
/dev/sda5             126   175783229    87891552   83  Linux
/dev/sda6       175783293   234372284    29294496   83  Linux
/dev/sda7       234372348   244139804     4883728+  82  Linux swap / Solaris
/dev/sda8       244139868   273442364    14651248+  83  Linux
/dev/sda9       273442428   279306089     2931831   83  Linux
/dev/sda10      279306153   283209884     1951866   83  Linux
/dev/sda11      283209948   288093644     2441848+  83  Linux
/dev/sda12      288093708   289073609      489951   83  Linux



whats the problem? thxn a lot in advance!!

---

### Post by bumanie on 2008-07-13
Before trying anything, can you tell me how come you have 3 ntfs partitions; + 6  ext3 partitions; + 1 swap partition all enclosed in 1 logical partition - making 12 partitions in all? It seems rather excessive on a 160gb drive - did you mean to have this many partitions? I assume the nfts paratitions = recovery partition; vista installation; data partition - is this correct?
The first problem is that you have vista trying to boot from within a logical partition, windows generally won't from a logical partition, that's most likely why you can't boot at present and get asked to go into recovery mode. Do you have data that is important to save?
Could you answer the above and also go to Applications --> Accessories --> Terminal and type > sudo apt-get install gpartedand hit enter. Once gparted has downloaded, go to System --> Administration --> Partition Editor. Click on partition editor and when it has opened take a screenshot (Applications --> Accessories --> Screenshot) and post it please.
I think you may have to save your important data and invoke recovery, doing anything else is going to be difficult as getting rid of a logical partition, gets rid of the partitions within - as everything is in the logical partition - I'm sure you can put 2+2 together. Sorry for the unpleasant news.

---

### Post by appi2012 on 2008-07-13
I have the exact same problem with my xp /ubuntu dual boot on my hp pc

Its something to do with the recovery partition.

What I would do is just backup all your windows files you need, and then use the windows installer to install windows over your old windows install. Then you can use Super Grub Disk to set up grub again.

see here:

[http://ubuntuforums.org/showthread.php?t=844598](http://ubuntuforums.org/showthread.php?t=844598)

---

### Post by bumanie on 2008-07-13
> **appi2012 said:**
> I have the exact same problem with my xp /ubuntu dual boot on my hp pc

Its something to do with the recovery partition.

What I would do is just backup all your windows files you need, and then use the windows installer to install windows over your old windows install. Then you can use Super Grub Disk to set up grub again.

see here:

[http://ubuntuforums.org/showthread.php?t=844598](http://ubuntuforums.org/showthread.php?t=844598)

What you say is true, but I would advise against trying to reinstall grub. I think your ubuntu installation needs to be done again (once you have resurrected vista). If you only have one linux on the computer, you should not need more than two partitions plus a swap for the linux installation - you certainly don't need 6 partitions plus a swap.

---

### Post by bauer on 2008-07-13
thnx a lot for your help both of you! actually i have many partitions because i made the mistake to have diferent partitions for srv, opt and all of them when installing ubuntu. What im gonna do is the whole thing from the beginning(vista recovery and ubuntu installation from scratch), fortunately i had saved any important stuff.Anyway heres a screenshot of what've i have done...a lot of mess actually...:(



About windows partitions is exactly bumanie said.

---

### Post by jimi_hendrix on 2008-07-13
when u installed ubuntu and you had to select where to install it where did you pick
(i said use the largest ammount of continual free space)

---

### Post by bumanie on 2008-07-13
> **bauer said:**
> thnx a lot for your help both of you! actually i have many partitions because i made the mistake to have diferent partitions for srv, opt and all of them when installing ubuntu. What im gonna do is the whole thing from the beginning(vista recovery and ubuntu installation from scratch), fortunately i had saved any important stuff.Anyway heres a screenshot of what've i have done...a lot of mess actually...:(



About windows partitions is exactly bumanie said.

I'm glad you have saved important data already, that makes a recovery much more palatable. Suggest choosing manual at partitioning and having 8-10gb / a 1-2 gb swap and /home as large as you like. Good luck.

---

### Post by bauer on 2008-07-13
@jimi_hendrix

i selected manual then used all the remaining partition of vista and did the linux partitions, but as i understanded i made too many of them

@bumanie

thnx again u help me a lot

---

