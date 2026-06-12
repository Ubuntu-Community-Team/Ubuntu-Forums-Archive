---
title: "[SOLVED] help my files are stuck in HUBackup"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by cliffm on 2008-11-29
Help! All my files are here. Just upgraded to Ubuntu 8.10
I have followed several answers to this problem and can not get any of them to work.
What am I doing wrong? The HUBackup file is 518.7MB, and was saved to a CD. These are some of my attempts to restore and there responses.


~$ dar -l /media/sdb1/backup/cliffm-master-archive
/media/sdb1/backup/cliffm-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]

:~$ sudo dar -x /cdrom0/backup/cliffm-master-archive -R /home/cliffm -wa -v
[sudo] password for cliffm:
/cdrom0/backup/cliffm-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]

m:~$ dar -x.hubackup-data/cliffm-master-archive -R TARGET_DIR
File ownership will not be restored as dar is not run as root. to avoid this message use -O option [return = OK | Esc = cancel]
Escaping...
Aborting program. User refused to continue while asking: File ownership will not be restored as dar is not run as root. to avoid this message use -O option
cliffm@cliffm:~$ sudo dar -x.hubackup-data/cliffm-master-archive -R TARGET_DIR
[sudo] password for cliffm:
.hubackup-data/cliffm-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]
Escaping...
Aborting program. User refused to continue while asking: .hubackup-data/cliffm-master-archive.1.dar is required for further operation, please provide the file.

---

### Post by cmnorton on 2008-11-29
Is the CDROM mounted?

What went wrong that is causing you to back everything up? Is it because you did a clean install including reformatting the drive?

---

### Post by cliffm on 2008-11-29
I was using 8.04 and decided to upgrade to 8.10. Just to learn. The first thing was to back up my data so I would not lose it. HUBackup seemed to be the easiest to use, and readily available. I downloaded 8.10 and had a bad download, only the terminal. was not able find what was wrong. Still had windows as dual boot. Re-downloaded 8.10 this changed all of my partitions. I have tried to  re-install my backup but no joy.
Is the cd mounted? I think so. when it is inserted in the drive it starts in the browser and the only question of this type is 'unmount'.

---

### Post by cmnorton on 2008-11-29
Using your error messages, specifically the missing files, see if you can find them on the CD.

---

### Post by cliffm on 2008-11-29
> **cmnorton said:**
> Is the CDROM mounted?

What went wrong that is causing you to back everything up? Is it because you did a clean install including reformatting the drive?

 Re: help my files are stuck in HUBackup
I was using 8.04 and decided to upgrade to 8.10. Just to learn. The first thing was to back up my data so I would not lose it. HUBackup seemed to be the easiest to use, and readily available. I downloaded 8.10 and had a bad download, only the terminal. was not able find what was wrong. Still had windows as dual boot. Re-downloaded 8.10 this changed all of my partitions. I have tried to re-install my backup but no joy.
Is the cd mounted? I think so. when it is inserted in the drive it starts in the browser and the only question of this type is 'unmount'.

---

### Post by cliffm on 2008-11-30
I have followed several threads to try to solve this problems and they all used HUBackup from the terminal. I had no joy.

---

### Post by bapoumba on 2008-11-30
Threads merged.

---

### Post by cliffm on 2008-11-30
I agree. Please do not blindly run commands. this has been true since eatly DOS
I backed up my /home files in prep to upgrade from 8.04 to 8.10. I chose to use the backup system offered by ubuntu under system-admin-hubackup. This seemed to work and indicated down load varified. So I proceeded to upgrade to 8.10, wiped out partitions,
then to re-install my backup using hurestore, no joy.
since I have tried to use this procedure in 8.10 and the backup has run for up to 10 min and has not completed forming the backup file.
My question now is does HUbackup and hurestoe work in 8.10. If I go back to 8.04 will I be able to retrieve my lost files?
cliffm

---

### Post by cmnorton on 2008-11-30
I'm still curious as to what you can see or not see on the backup media? Basically, your original log is saying it cannot see files on the media. What can you see, if you mount the media and poke around on it?

---

### Post by cliffm on 2008-11-30
There are 2 files on the cd 'cliffm-master-archive.1.dar' and TRANS.TBL. I tried to open with simple backup restore it can see the files but cannot open. HURestore does not see the cd in cdrm0. cdrm0 is mounted.

---

### Post by cmnorton on 2008-11-30
Do you have a programmer's editor of some kind, like emacs, perhaps vi (vim)? If you do, see if you can open up the TRANS.TBL file to see what's in it. Perhaps you have to pull these files off into a directory you have previously created just for those files, and try your backup program.

Who makes HUBackup? Is it open source? It sounds like you are going to need an expert.

---

### Post by cliffm on 2008-11-30
contents of TRANS.TBL
F CLIFFM_M.DAR;1                                                                                                                                                                                                  	cliffm-master-archive.1.dar
As to who makes HUBackup and HURestore they come standard with Ubuntu. System/Administration/HUBackup or HURestore
I have no idea who the author is. As it comes with Ubuntu and seemed to backup and varifed the file thought it would be good.

---

### Post by cmnorton on 2008-11-30
It looks like your problem is HUBackup seeing what's on the CD, and I'm lost at that point. If you can get HUBackup to recognize the files in a directory on the disk that would be your next step.

---

