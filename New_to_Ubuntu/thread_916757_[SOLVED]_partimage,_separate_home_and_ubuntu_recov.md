---
title: "[SOLVED] partimage, separate /home and ubuntu recovery"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Halibutt on 2008-09-11
Hello there! So, once again my Ubuntu HH got FUBAR. No network, no advanced gfx, nothing. Fortunately for me, the last time something went wrong I prepared three different partitions for my installation (separate /home, / and swap). I also backed up my / partition with partimage. 

Now then, sudo fdisk -l shows the following:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd315d315

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5473    43961841    7  HPFS/NTFS
/dev/sda2            5474        7296    14643247+   5  Extended
/dev/sda5            5474        5765     2345458+  82  Linux swap / Solaris
/dev/sda6            5766        6738     7815591   83  Linux
/dev/sda7            6739        7296     4482103+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)
```

My sda6 is backed up in three files located on the big fat sdb1 external drive (they're at /media/CZARNY/ubuntu-backup/backupubuntu.000, backupubuntu.001 and backupubuntu.002). 

And that's precisely where my problem starts. When I boot with LiveCD and install partimage, all fires just fine (with network and so on), but partimage does not seem to find my backup files. Any combination I tried went wrong. What exactly should I put in there to make it work?

Or is there some other way to restore Ubuntu, perhaps using the LiveCD to repair the packages that are there, while leaving all the rest untouched? Any ideas?
Cheers and thanks in advance

---

### Post by Bucky Ball on 2008-09-11
Try dropping this in a terminal:

                                       [LEFT]**sudo dpkg --configure -a**[/LEFT]
   
  
Should repair any screwed packages.

Also in a terminal, try:

**sudo mount /dev/sdb1**

... and try again. Stab in the dark but hope it helps.

---

### Post by Halibutt on 2008-09-11
> **Bucky Ball said:**
> Try dropping this in a terminal:

                                       [LEFT]**sudo dpkg --configure -a**[/LEFT]
   
  
Should repair any screwed packages.
If only I had a working Internet connection in Ubuntu... But I don't, which means that there's no way the system checks which packages are right and which are wrong. 


> **sudo mount /dev/sdb1**

... and try again. Stab in the dark but hope it helps.Not sure if I didn't try that combination already, but what the heck, why not check it again. But anyway, if that works (and why shouldn't it), what exactly do I put in the window of partimage?
Cheers

---

### Post by Bucky Ball on 2008-09-11
Partimage should then see your /dev/sdb1 without a problem. Might not be seeing it because it is not mounted. Then you can grab your backup from it (whatever you might have named it) and plop it back to where you want it. :)

---

### Post by Halibutt on 2008-09-11
> **Halibutt said:**
> Not sure if I didn't try that combination already, but what the heck, why not check it again. But anyway, if that works (and why shouldn't it), what exactly do I put in the window of partimage?
Cheers
That's what I thought, the drives mount just fine, even auto-mounting works. But what to input into the partimage - that is the question. Newbie, remember? :) 

In short, if we were talking Windows here, I'd type "/media/CZARNY/ubuntu-backup/backupubuntu.000" and it would fire just fine. But this address doesn't work in Ubuntu, even though the drive is mounted (as sdb1) and the files are there (at least in Nautilus).

EDIT:// or do you mean that "/media/CZARNY/ubuntu-backup/backupubuntu.000" and "/dev/sdb1/ubuntu-backup/backupubuntu.000" are the very same thing?

---

### Post by Bucky Ball on 2008-09-11
Now I'm with ya. Is:

**/media/CZARNY/ubuntu-backup/backupubuntu.000**

The path to the file you are trying to restore to /sda6? If so, try:

**/dev/sdb1/media/CZARNY/ubuntu-backup/backupubuntu.000**

Making sure you are restoring the file, of course. :)

If the /media bit is windoze jargon (sorry, don't remember a lot about my past life!), you could replace that with:

**/dev/sdb1/CZARNY/ubuntu-backup/backupubuntu.000**

Also, you could open a terminal and do:

**cd /dev/sdb1**

Then:

**locate backupubuntu.000**

... and that should find it for you. Also, if the drives are mounting, you could find your backup files through the desktop and get some clues from that.

---

### Post by Halibutt on 2008-09-11
> **Bucky Ball said:**
> Now I'm with ya. Is:

**/media/CZARNY/ubuntu-backup/backupubuntu.000**

The path to the file you are trying to restore to /sda6? If so, try:

**/dev/sdb1/media/CZARNY/ubuntu-backup/backupubuntu.000**

Making sure you are restoring the file, of course. :)

If the /media bit is windoze jargon (sorry, don't remember a lot about my past life!), you could replace that with:

**/dev/sdb1/CZARNY/ubuntu-backup/backupubuntu.000**

Also, you could open a terminal and do:

**cd /dev/sdb1**

Then:

**locate backupubuntu.000**

... and that should find it for you. Also, if the drives are mounting, you could find your backup files through the desktop and get some clues from that.

Hmmm, now we're getting somewhere. "/dev/sdb1/media/CZARNY/ubuntu-backup/backupubuntu.000" this time doesn't cause any errors - but it simply escapes partimage and returns back to ubuntu@ubuntu:~$. The same goes for the other command you suggested. 

Part of the problem might be that 

```
ubuntu@ubuntu:~$ cd /dev/sdb1
bash: cd: /dev/sdb1: Not a directory
```

Any ideas what to do next?
Cheers


EDIT: HA! I got it! No tutorial ever mentioned, that I need to run partimage in the directory where my backup files are located. Now that I cd'ed to /media/CZARNY/ubuntu-backup, it fired just fine. I'll keep you informed.

EDIT2: Simulation went just fine, now started the real restoration. We'll see... If all goes right, I'll mark this thread as solved from my Ubuntu installation. If not, Windows will be my only hope...

---

### Post by Halibutt on 2008-09-11
Woooohooo! :D Worked like a charm, thanks a lot. Ubuntu's up and running once again.

---

### Post by Bucky Ball on 2008-09-11
Love it when a plan comes together! Well done. Another few steps up the learning curve and what took forever this time will take 5 minutes if it ever happens again. \\:D/

---

