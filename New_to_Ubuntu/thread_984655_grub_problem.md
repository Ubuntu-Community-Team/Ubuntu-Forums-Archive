---
title: "grub problem"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by 2much4me on 2008-11-16
Think of me as a handicapped person.  I only know windows.  I tried to burn a CD and failed. Then I downloaded 8.10 to my second hard drive (the one with 30 GB of free space). After download it never asked to migrate my files. I was upset and deleted it using Add/Remove in Windows (I used WUBI). Next,I bought a live Cd with 8.04 on it. That is installed on my second drive but I get boot failures more often than half the time.  A check of my papers that came with the computer say that the second drive isn't bootable.  That isn't totally true as it does boot sometimes after I ran Super Grub Disk. This time Windows doesn't see Ubuntu as I didn't use WUBI.  For me,the terminal window is a scarry place.  Grub returns error 22(?) and I am SOL. It appears that my choices are: 1. Delete Ubuntu 2. Fix grub 3. Delete Ubuntu and move a huge amount of data to my second drive to make room for ubuntu. 4. Correct the situation with your help.

:confused:

---

### Post by olskar on 2008-11-16
Can you boot with a Windows CD?

If so, get to a commandline, type fixmbr.

---

### Post by cariboo on 2008-11-16
Use you LiveCD to boot to the desktop, and in a Applications-->Accessories-->Terminal type:

```
sudo fdisk -l
```

then mount the drive Ubuntu is installed on:

```
sudo mount /dev/sdb1 /mnt
```

This assumes you've used the entire hard drive to install Ubuntu. Next in the same terminal type:

```
cd /mnt/boot/grub
```

This should put you in the same directory that the grub menu is located. in the same terminal type:

```
cat menu.lst
```

Paste the output of the first and last commands in your next post.

Jim

---

### Post by Jesan Fafon on 2008-11-16
I've had problems with GRUB myself as a windows user.

Errors 21 and 22 from my experience indicate that your dive which Linux was installed on was not available at the time, meaning it didn't spin up before Hard Drive detection began in your BIOS. I have linux on an external disk, so its hit or miss whether my machine boots without fail. 

At the GRUB error 21 or 22, turn off the machine and turn it back on quickly, and you should be fine. If that doesn't work, then you need a MS-DOS startup disk that has the routine fdisk on it and you will need to run 
```
 fdisk /mbr 
```
which will destroy grub and you will need to reformat your Linux drive in windows.

---

### Post by 2much4me on 2008-11-17
Hi Jeson,

I have struggled to learn why I am getting error 22.  You have given me the answer!  I have two physical hard drives and Ubuntu is on the second, non-bootable, drive. Rarely, at start, I get the correct display of choices on my dual boot system.  

I don't have a DOS start disk.  I have the recovery on my H drive.  I tried the original Windows XP disk and it didn't load.

Any additional thoughts will be greatly appreciated.

Steve

> **Jesan Fafon said:**
> I've had problems with GRUB myself as a windows user.

Errors 21 and 22 from my experience indicate that your dive which Linux was installed on was not available at the time, meaning it didn't spin up before Hard Drive detection began in your BIOS. I have linux on an external disk, so its hit or miss whether my machine boots without fail. 

At the GRUB error 21 or 22, turn off the machine and turn it back on quickly, and you should be fine. If that doesn't work, then you need a MS-DOS startup disk that has the routine fdisk on it and you will need to run 
```
 fdisk /mbr 
```
which will destroy grub and you will need to reformat your Linux drive in windows.

---

### Post by 2much4me on 2008-11-17
Thank you for taking the time to help me.

Only half of the second drive is allocated to Ubuntu (30GB).  I learned, after installing Ubuntu, that the second drive is not intended to be bootable.  It works as a bootable disk about 10% of the time.

Again, Thank you for your help. Please let me know what to do with a partitioned second drive, not a drive dedicated to Ubuntu.    

> **cariboo907 said:**
> Use you LiveCD to boot to the desktop, and in a Applications-->Accessories-->Terminal type:

```
sudo fdisk -l
```

then mount the drive Ubuntu is installed on:

```
sudo mount /dev/sdb1 /mnt
```

This assumes you've used the entire hard drive to install Ubuntu. Next in the same terminal type:

```
cd /mnt/boot/grub
```

This should put you in the same directory that the grub menu is located. in the same terminal type:

```
cat menu.lst
```

Paste the output of the first and last commands in your next post.

Jim

---

### Post by 2much4me on 2008-11-17
I don't have a rescue disk.  I was relying on the recovery file in my H drive, set aside for recovery.  The second drive doesn't start at the same time as the first drive.  That's why I get error 22 (I just learned this piece of information).  I think the Master Boot Record starts after GRUB has run.  Am I right?

Thank you for your efforts on my behalf.  If you have more input I would like to hear what you think.   

> **olskar said:**
> Can you boot with a Windows CD?

If so, get to a commandline, type fixmbr.

---

### Post by Jesan Fafon on 2008-11-27
I don't know if you've given up or tried something else, but I have an ISO of CD that boots into MS-DOS and will allow you to run

```
 fdisk /mbr 
```

I don't recall where I got it from. If you need it, Private Message me with an email address I can send it to you at.

It's saved me twice since you posted originally, so I hope I can help you as well.

Also, try pressing the power button at ERROR 21/22 and pressing it again immediately after.
This should get both disks to spin up at the same time. I have to do this on one of the machines I've refurbished and added Linux to this week.

I'm sorry I was unable to reply sooner, I've been having my own issues and just remembered that I had promised to help you....

Sorry!!!

---

