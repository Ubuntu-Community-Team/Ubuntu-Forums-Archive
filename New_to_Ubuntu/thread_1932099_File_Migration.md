---
title: "File Migration?"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by Mister Fox on 2012-02-26
I just downloaded Ubuntu alongside Windows 7 and I love it! It's faster, easier to interface with, and it has a wonderful forum dedicated to it (seriously, windows windows doesn't!). I have a lot of files in windows 7 that I would like to transfer over to Ubuntu, but I'm not sure how to do that. Is there some option on either OS, or is there something I should download? Or do I have to make a bunch of copies onto a flash drive and manually place the files?

Also, DIS IS MAH FIRST POST!! YAY ME!

---

### Post by sudodus on 2012-02-26
Welcome to the Ubuntu Forums :-)

Ubuntu can read and write an NTFS file system. It is a good idea to have a common ***data*** partition with NTFS, if you want to keep Windows and have dual boot. You should not tamper too much with the Windows system partition, normally C:, from Ubuntu (reading is OK).

---

### Post by Lisiano on 2012-02-26
Hello and welcome to Ubuntu Forums, your one stop place to get help!
Anyway, you can easily see all the files you have on Windows when you are in Ubuntu, look at the left panel (Or Launcher) and at the bottom you will notice an icon that looks like a hard-drive, just click it and you will see your Windows partition (Or C: Drive)

EDIT: Ninja'd by sudodus

---

### Post by Mister Fox on 2012-02-26
All I want is my files that I made in windows to be on Ubuntu. I'm a total noob, so could someone **explain** the simplest way to do this?

edit- saw Lisiano's post...

---

### Post by sudodus on 2012-02-26
Use your file browser (similar to Windows Explorer). You can drag and drop or copy and paste between two browser windows.

Come back if you need more details!

---

### Post by Paqman on 2012-02-26
All you files are still sitting on the Windows side of your system. You can access that part of your hard drive to get to the files. Click on the folder icon on the launcher and look in the pane on the left for something that looks like a drive. It may be called something like XXGB Volume. Click on it to mount it and you should see the normal Windows file structure. You can navigate to your files just like you would in Windows. You could either leave them there or you could move them over to the Ubuntu side of your system.

---

### Post by Mister Fox on 2012-02-26
> **Paqman said:**
> All you files are still sitting on the Windows side of your system. You can access that part of your hard drive to get to the files. Click on the folder icon on the launcher and look in the pane on the left for something that looks like a drive. It may be called something like XXGB Volume. Click on it to mount it and you should see the normal Windows file structure. You can navigate to your files just like you would in Windows. You could either leave them there or you could move them over to the Ubuntu side of your system.


I clicked the folder icon, but there's nothing even close to XXBG there. I have SYSTEM and HP_TOOLS under the Devices section, and under Computer I have Home, Desktop, Documents, Downloads, Music, Pictures, Public, Templates, Videos and Examples.
There's 1 more section called Network. in Network is Browse Network, and in that is Windows Network. When I click on Windows Network it says "Unable to mount location- filaed to retrieve share list from server"

---

### Post by Miljet on 2012-02-26
"SYSTEM" would be what you are looking for.

---

### Post by sudodus on 2012-02-26
> **miljet said:**
> "system" would be what you are looking for.
+1

---

### Post by Mister Fox on 2012-02-26
> **Miljet said:**
> "SYSTEM" would be what you are looking for.

In SYSTEM there is Boot, $RECYCLE.BIN, System Value Information, bootmgr and a text file called SYSTEM which shows the partition size.

---

### Post by sudodus on 2012-02-26
Now it is time for some terminal window commands. Press
***ctrl + alt + t***
to get the terminal, and type the following commands (finish with the Enter key)
```
sudo fdisk -lu
``` and
```
df
```
Please cut and paste the output of those commands into a reply in this thread! That will help us understand what is where on your HDD.

---

### Post by Mister Fox on 2012-02-26
Result of:   sudo fdisk -lu
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4166d6a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      616447      307200    7  HPFS/NTFS/exFAT
/dev/sda2          616448   579414015   289398784    7  HPFS/NTFS/exFAT
/dev/sda3       579414016   614649855    17617920    7  HPFS/NTFS/exFAT
/dev/sda4       614649856   625125375     5237760    c  W95 FAT32 (LBA)

Result of:   df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0            17596475   2139493  15456982  13% /
udev                   1987940         4   1987936   1% /dev
tmpfs                   798336       860    797476   1% /run
none                      5120         0      5120   0% /run/lock
none                   1995840       124   1995716   1% /run/shm
/dev/sda2            289398780 100695468 188703312  35% /host

---

### Post by Paqman on 2012-02-26
Ah, you installed using Wubi. In that case all your files are located at /host. OPen up your file browser and either navigate to /host or hit CTRL-L and type /host in the bar that appears.

Wubi is a slightly different setup from a normal dual boot, but your files will still be accessible.

---

### Post by sudodus on 2012-02-27
> **Paqman said:**
> Ah, you installed using Wubi. In that case all your files are located at /host. OPen up your file browser and either navigate to /host or hit CTRL-L and type /host in the bar that appears.

Wubi is a slightly different setup from a normal dual boot, but your files will still be accessible.
+1
I'm glad Paqman posted this answer to your latest post, that came after I logged out. The last line in the output of ***df*** gave us the final clue, where to find your windows file system.
```
/dev/sda2 289398780 100695468 188703312 35% /host
```
If this solves your problem and if you have no further questions, please mark this thread SOLVED (click on [COLOR="Red"]**_Thread Tools_**[/COLOR] at the top of this page)

---

### Post by bcbc on 2012-02-27
> **Mister Fox said:**
> ...I have a lot of files in windows 7 that I would like to transfer over to Ubuntu...

I would recommend leaving your data on /host where it's easily accessible from both Windows and Ubuntu. I also wouldn't use a virtual disk (that wubi uses) as my primary data storage (unless you're excellent at maintaining backups).

---

