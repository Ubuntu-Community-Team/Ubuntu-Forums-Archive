---
title: "HDD Disappeared"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by Momof9Blessings on 2012-01-02
Hi all,

I am using Ubuntu 11.10 dual boot with windows Vista (manual install).

Everything seemed to be working well....  Yesterday I needed to go into windows to get some more info off of FireFox and Thunderbird.... I did have a time with starting windows.... did not want to start (must have done a check disc that failed - I tried to quit it) then it finally started.... I got my info than got back into ubuntu....

This morning, I needed to get into my hard drive (it has been available before) but it has disappeared....

I did this (from other threads)....

```
lori@Lori-PC:~$ sudo fdisk -l
[sudo] password for lori: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6dffb3fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   799055522   399527730    7  HPFS/NTFS/exFAT
/dev/sda2       956157952   976752639    10297344    7  HPFS/NTFS/exFAT
/dev/sda3       799055870   956157951    78551041    5  Extended
/dev/sda5       950394880   956157951     2881536   82  Linux swap / Solaris
/dev/sda6       799055872   944629759    72786944   83  Linux
/dev/sda7       944631808   950388735     2878464   82  Linux swap / Solaris

Partition table entries are not in disk order
```

This is my whole laptop hard drive - but I can't find it in the home folder no longer.

I even have some bookmarks for things in the hard drive (Gwenview and home folder) and they no longer work....

Any ideas???

Thank you

---

### Post by cortman on 2012-01-02
So what you're saying is that Ubuntu/Windows boots fine, but you can't access files on your HD through the file browser?

---

### Post by Mark Phelps on 2012-01-02
IF the files you want were in Windows filesystem partitions, and CHKDSK failed or was stopped (by you), that likely left those filesystems in a "dirty" (what Windows calls it) state -- and in those cases, Linux will no longer mount the partitions, to prevent further damage.

You need to boot BACK into Windows, run CHKDSK on those partitions -- and let it finish, this time.

---

### Post by Momof9Blessings on 2012-01-02
I did go in to windows (had a hard time to get it started again - had to try several times to get it to boot normally)....

Then I went to C: drive and right clicked - did disc analysis, disc check and nothing came back as wrong.....

I still do not see the drive in the home folder.... :(

---

### Post by Momof9Blessings on 2012-01-02
I am back....did do a chkdsk thru the command prompt.... it came back as error free....

but I still do NOT see my drive.... :(

---

### Post by Momof9Blessings on 2012-01-02
I guess I had not refreshed it enough times... it is showing up in Gwenview!!!

---

### Post by Mark Phelps on 2012-01-03
So, is it OK now?  If so,please use the Thread Tools at the top of the thread and mark this as SOLVED. tanks

---

### Post by Momof9Blessings on 2012-01-21
This is still an issue....  

My HDD(windows partition) shows up in Gwenview - but not in the "home folder"....  Whenever I restart my laptop, I have to open Gwenview, click on my hard drive.... Then open the Home Folder - then refresh (if I already) opened it.... then I can get to my links I have made to folders on my win HDD partition....  I cannot access C: drive on its own (I guess I might need to make a link to it) thru Home Folder....

But it is kind of a pain to have to open Gwenview just for that....  I am now using Home Folder for everything - since I know how to adjust things within it now....

When I first installed Ubuntu - Home Folder did show my HDD....

I also have an exteral - that is not showing up anywhere.... at least I am not seeing it anywhere.... It has important things I need to get to as well....  :(

Thank you for your help...

---

### Post by Momof9Blessings on 2012-01-21
ooh I am frustrated with technology right now.... LOL[COLOR="Red"]

I did just find my laptop internal HDD showing up on the left (unity bar).... I forgot that it showed up there....[/COLOR]
Strike out the above... I had an update the other day.... and I just realized that it said I needed to restart my comp....

So when I look - the above icons are NOT there when I restart...


But I still have no idea about my external usb hdd drive

---

### Post by Momof9Blessings on 2012-01-21
I thought I would do some exploring in Home Folder - GO at the top - lists places you can go - I see my drives.... 

Thought I had them all (that now opens them up to the unity bar)

but I do NOT see my external... :(

---

