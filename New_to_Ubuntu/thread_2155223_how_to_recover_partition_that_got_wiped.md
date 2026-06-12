---
title: "how to recover partition that got wiped"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by vaah on 2013-06-17
Hi,
Initially my laptop was using windows 7. I had 2 partitions on my hdd one was for the windows junk namely c drive and other is d drive where I put all my doc and data stuff.

Just now i decided I wanted to install the latest ubuntu, and I chose the replace windows 7 option when installing ubuntu. I had bad feeling with my choice and I decided to stop the installation process immediately. However when I checked my hdd, those 2 partitions I had were gone and were replaced with one partition with ext4 filesystem. I believe the installation process hasn't overwrite much sectors yet..

Please someone help me recover my d drive partition(it was NTFS). Right now I'm trying to recover using testdisk but I'm a bit skeptical if this can bring back my d drive? Please someone shed some light regarding my situation.. Thanks!!

---

### Post by LocoChepe on 2013-06-17
HI,
just read your post. It usually is a good idea to create a  separate partition to isolate Ubuntu so as to have it as a dual boot  with windows, this way you are able to try both operating systems before  making a final decision with which one to stay..
You might be able to boot from your Ubuntu bootable cd as a live cd and search for your data once Ubuntu has loaded. If it doesnt work try visiting this site
[http://www.sysresccd.org/Sysresccd-manual-en_Backup_data_from_an_unbootable_windows_computer](http://www.sysresccd.org/Sysresccd-manual-en_Backup_data_from_an_unbootable_windows_computer)
note:This assumes that your data is not completley lost.

---

### Post by vaah on 2013-06-17
> **linuxtechguy said:**
> format and reinstall

after that how are you suggesting me to recover my d drive partition?

---

### Post by LocoChepe on 2013-06-17
I tried using Hiren cd once to recover a deleted partition but did not had much luck, but I did recover my data from my D: drive after my OS had been corupted. Hiren cd does not come with a guarantee but it does bring many useful tools including some to recover lost data, use with caution. I recomend taking some time to learn more about the recovery tools included on the hiren cd.

---

### Post by vaah on 2013-06-17
> **LocoChepe said:**
> HI,
just read your post. It usually is a good idea to create a  separate partition to isolate Ubuntu so as to have it as a dual boot  with windows, this way you are able to try both operating systems before  making a final decision with which one to stay..
You might be able to boot from your Ubuntu bootable cd as a live cd and search for your data once Ubuntu has loaded. If it doesnt work try visiting this site
[http://www.sysresccd.org/Sysresccd-manual-en_Backup_data_from_an_unbootable_windows_computer](http://www.sysresccd.org/Sysresccd-manual-en_Backup_data_from_an_unbootable_windows_computer)
note:This assumes that your data is not completley lost.

I wasn't planning to have a dual boot, hence the choice to replace windows 7 during the installation process. I should say this wasn't my first time installing ubuntu, and usually I choose the advance option and choose which partition for what myself. I don't know what got into me that I chose "replace windows 7 with ubuntu" option today..:(

At the moment I already boot into the laptop using livecd and running the testdisk software to analyse my hdd. It's been an hour or so and it's still at ~70%
Do you think I'm gonna be able to recover the d drive using testdisk? I don't care what happened to the c drive.

---

### Post by vaah on 2013-06-17
> **LocoChepe said:**
> I tried using Hiren cd once to recover a deleted partition but did not had much luck, but I did recover my data from my D: drive after my OS had been corupted. Hiren cd does not come with a guarantee but it does bring many useful tools including some to recover lost data, use with caution. I recomend taking some time to learn more about the recovery tools included on the hiren cd.

Alright I'll have a look at hiren cd.

What worries me is that ubuntu installation process wipe the 2 partitions, which were NTFS originally, created one new partition instead in ext4 filesystem.

---

### Post by LocoChepe on 2013-06-17
testdisk is a very useful tool to fix, recover deleted partitions as well as undelete files from FAT, exFAT, NTFS and ext2 filesystem 
it seems like it can also copy files from deleted FAT, exFAT, NTFS and ext2/ext3/ext4 partitions. so if you are an experienced user and know how to use the tool correctly it should help you.

---

### Post by Cheesemill on 2013-06-17
First of all stop using the drive, the more you use it the more data will be overwritten.

Then follow Mark Phelps' advice here...
[http://ubuntuforums.org/showthread.php?t=2149622&p=12668997&viewfull=1#post12668997](http://ubuntuforums.org/showthread.php?t=2149622&p=12668997&viewfull=1#post12668997)

---

### Post by vaah on 2013-06-17
@Locochepe: I had a luck with testdisk once when my hdd partition suddenly gone on my primary PC. However at the time the NTFS partition hadn't been overwritten or formatted into other filesystem, so It was successfully recovered. This time the partition was formatted from ntfs to ext4..and imo ext4 is a pain when it comes to recovering lost files, thats why I always avoid ext4 for data store.

Does anyone have similar situation like me?

---

### Post by user_of_gnomes on 2013-06-17
Testdisk jumps to mind here as well. NTFS stores a copy of boot sector so there's a chance you can restore it to full health. And even if you can't, maybe you can rebuild the boot sector. 

If you just want to recover files GetDataBack is half-decent: [http://www.runtime.org/data-recovery-software.htm](http://www.runtime.org/data-recovery-software.htm)

---

### Post by vaah on 2013-06-17
Guys, Just wanted to let you know. I was able to restore my partition like ubunturaptor said. I thought I would have to copy the data to external disk, but it turned out I just need to rebuild the partition in a matter of seconds, and restart the livecd. I can see the partition is back.
Thanks guys for the input!!

---

### Post by vaah on 2013-06-17
Can someone please tell me how to mark this thread as solved? Thanks..

---

### Post by user_of_gnomes on 2013-06-17
Good to hear!

---

### Post by JKyleOKC on 2013-06-17
> **vaah said:**
> Can someone please tell me how to mark this thread as solved? Thanks..go to the initial post, click to edit it, and at the box for the title pull down the list. The first item will be the solved label. Choose it, save, and you're done.

---

### Post by Mark Phelps on 2013-06-17
> **vaah said:**
> ... Does anyone have similar situation like me?

text deleted...

---

### Post by vaah on 2013-06-18
> **JKyleOKC said:**
> go to the initial post, click to edit it, and at the box for the title pull down the list. The first item will be the solved label. Choose it, save, and you're done.

Thanks I didn't know I had to go "go advanced" while editing to change the title prefix. :P

---

