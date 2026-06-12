---
title: "xp and ubuntu loaded but now xp is recognizin only half of my new disk"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by tavati on 2008-09-28
i have two IDE harddisks.
40 GB primary master and 320 GB primary slave
i have win me and win xp on two drives of primary.
i have laoded ubuntu on logical drive of primary again with dual boot 
everything is ok but i have one problem now.

win me and xp show only one drive of 128 GB on the primary slave disk. and it does not even say that the rest ( 320 -128 = 192 GB) is unknown type etc,

i have only made seven 10 Gb ext3 logical partitions on primary slave and one 5 GB ext3 logival partition on the same disk. rest all space is fat32 and divided into one primary partition and five logical partitions. 

the win me and xp shows only one partition of 128 GB on the second disk. i used the ubuntu partitioner during installation process of ubuntu.

i read lot of threads but nothing like this! 
why is my win me and xp showing different size of disk but ubuntu shows correct and full info. i am afraid i will overwrite something because i use both xp and ubuntu equally.

---

### Post by muted1987 on 2008-09-28
fat32 this is why you will only see half of it

if i remember correctly there was something back in the day that stopped windows seeing a hdd higher than 128gb if it was in fat32 if theres nothing on that part of the drive may i suggest using ntfs to partition that part it may solve the problem

this might not even be the case hopefully someone can correct or agree with me

---

### Post by bumanie on 2008-09-28
Not sure that is quite correct. FAT32 can recognise quite large capacity hard drives, I think the issue is the limitations set in bios in days gone by. 10 years ago, hard drives of 10gb were seen as relatively large and bios were not programmed to see drives as large as 320gb, as the hard drives did not exist. The issue is most likely the limitations set in bios.

---

### Post by tavati on 2008-09-28
u may be right b'cause before all this when i was partitioning the new 320 gb disk in xp it gave me only ntfs as choice to format. but my prob is that i have at sixpartitions fat32 type on the disk one 10gb, four 50gb and one 34gb. now the 10 gb is  primary and rest logical. but no combination of adding the figures give 128gb.

so my question is how xp is combining the space on this disk to give one partition of 128gb.

---

### Post by muted1987 on 2008-09-28
the problem did occur back on 98 it was fat32 over 137gig just either wasnt recognised or corrupted whether this wqas carried forward to previous generations i do not know

---

### Post by shifty_powers on 2008-09-28
ok, do me a favour.

go to the control panel>administrative tools>drive management iirc and take a snapshot of the drives as shown and post it on here please. (this is in xp btw)

---

### Post by tavati on 2008-09-28
bumanie, i did not have this problem when i first partitioned this new disk with xp but as i said earlier xp gave me ntfs as the only option after i partitioned the new disk into smaller partitioner.

before reinstalling ubuntu with new partition sizes and mount points xp was reading the disk correctly and giving details of unused and unkown partitions on the new disk adding up to 320gb. but somewhere in this experimenting process i again reinstalled ubuntu with new partitions on the new disk,i used ubuntu partitioner at installation time to make three primary partitions and on extended partitioner. After this stage after successful installation of ubuntu 7.10 i restarted the computer and then i went to xp and verified if xp was seeing all i did in ubuntu. at that time it did.

i again reinstalled ubuntu and made some changes like size of partitions and this time i kept one primary partions on the new disk one 10 gb fat32 partition and the rest i divided in ext3 partions and a few large fat32 partions all logical. the ubuntu installer does not give option to make extended partition but gives options for choosing logical or primary. i chose logical for all these.

my boot partion was on the same disk on which the first primary partition of win xp was and this time i made the boot partition of ubuntu as primary partition.

after installing ubuntu this way i started getting a big problem. my xp and win 98 wer not loading !!. after selecting win xp from grub i got error: hal.dll missing or corrupted . and the computer would restart on its own after i pressed any key on keyboard.

i reinstalled win 98 which wiped out ubuntu but now to my surprise after successful installation win 98 would not start with same problem,

finally i loaded win me followed by win xp ( independent dual boot with win me) and followed by ubuntu with similar partitions but with the following differences

my boot drive of ubuntu was on the old disk but this time i chose it as logical partition

on my new harddisk ( 320 gb) i kept partitions similar .

now all three OS are working fine but this problem that i mentioned. why xp has stopped recognizing above 128 gb now.

---

### Post by tavati on 2008-09-28
ok by the time i typed my latest u gave this info wait a minute and i will paste it.

---

### Post by tavati on 2008-09-28
ok here is the snapshot. by the way after i took it my win xp startin shutting down immediately and gave me on minute to clean up . is it some security thing or just one more bug. anyway i am more interested in the partition thing first.

---

### Post by shifty_powers on 2008-09-28
xp spontaneously shutting down is not usually a great sign.

plus, no attachment/picture?

---

### Post by tavati on 2008-09-28
sorry here is the snap shot u wanted attached

---

### Post by shifty_powers on 2008-09-28
hmm, llok at this artice:

[http://en.wikipedia.org/wiki/Fat32#FAT32_.28VFAT.29](http://en.wikipedia.org/wiki/Fat32#FAT32_.28VFAT.29)

> On Windows 95/98, due to the version of Microsoft's SCANDISK utility included with these operating systems being a 16-bit application, the FAT structure is not allowed to grow beyond around 4.2 million (< 222) clusters, placing the volume limit at 127.53 gigabytes.[12] A limitation in original versions of Windows 98/98SE's Fdisk utility causes it to incorrectly report disk sizes over 64GB.[13] A corrected version is available from Microsoft. These limitations do not apply to Windows 2000/XP except during Setup, in which there is a 32GB limit.[14] Windows Me supports the FAT32 file system without any limits.[15] However, similarly to Windows 95/98/98SE there is no native support for 48bit LBA in Windows ME, meaning that the maximum disk size is 127.6GB

looks like that might very well be the answer?

---

### Post by tavati on 2008-09-28
thanks, but that would mean that windows will overwrite my ubuntu partitions. and also how was my xp recognizing full 320 gb initially ?

---

