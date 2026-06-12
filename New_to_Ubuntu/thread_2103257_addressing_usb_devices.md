---
title: "addressing usb devices"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by Wray on 2013-01-09
How do find the name of a usb device in xtrm?  I plug in a 16 bg usb "thumbdrive" and wait for it to load, then it shows on the GUI, but i can' identify it in xterm.
I want to do a copy from the usb to home directory.

---

### Post by steeldriver on 2013-01-09
pluggable devices should mount by default in /media/<label> , or /media/<user>/<label> from 12.10 I think

```
$ ls /media
7062-065B

```

---

### Post by Wray on 2013-01-09
when i do cd /media it returns [COLOR=Blue]wray  [/COLOR](me)

---

### Post by Cheesemill on 2013-01-09
There are a lot of different commands you can use to list information on all mounted filesystems. For example here I'm using 'lsblk -f'.
```
rob@arch:~$ lsblk -f
NAME   FSTYPE LABEL     UUID                                 MOUNTPOINT
sda                                                          
&#9500;&#9472;sda1                                                       
&#9500;&#9472;sda2 ext4   arch-root d750d77a-f9f8-4b88-86ea-7e1648482339 /
&#9492;&#9472;sda3 ext4   arch-home 770ecba1-aa95-4033-b96b-54c75138d938 /home
sdb                                                          
&#9492;&#9472;sdb1 ext4   data      af1162b3-ebf6-4681-8908-a6bc1ddd39de /mnt/data
sdc                                                          
&#9500;&#9472;sdc1 ext4   emulation c190cf99-1749-4f7b-878d-de20914d3c57 /mnt/emulation
&#9492;&#9472;sdc2 swap   swap      e6cd40fe-acbc-4667-975b-162298028119 [SWAP]
sdd    vfat             2CEE-983B                            
&#9492;&#9472;sdd1 vfat             38CE-31E0                            /run/media/rob/38CE-31E0

```You can see from the last line that my flash drive /dev/sdd1 is mounted on the /run/media/rob/38CE-31E0 directory and is a vfat (FAT32) partition. Running the command on your machine will show something similar (it wont be in /run/media on Ubuntu, I'm on my Arch machine at the minute).

---

### Post by alphacrucis2 on 2013-01-09
> **Wray said:**
> when i do cd /media it returns [COLOR=Blue]wray  [/COLOR](me)

The newer versions of Ubuntu mount usb drives under /media/<your usercode> 

Try 

```
ls /media/wray
```

---

### Post by dannyboy79 on 2013-01-09
you can use the "mount" command to show mounted filesystems. just type in mount on the command line and hit enter, it'll show each device mounted and where it's mounted

---

### Post by Wray on 2013-01-09
Thanks 
Ceesemill that did it for me... identified my usb stick as CRUZER...command for me is:
[COLOR=Blue]cd /media/wray/CRUZER/'Removable Disk'[/COLOR]...capital letters and spaces  continue to throw me.
I finally remembered the single quote thing for spaces.  I have done only a tiny bit of coding and that was DOS and some machine coding about 35 yrs ago, so progress is slow...

If i try your patience, it is not wilful, but from abysmal ignorance

---

### Post by dannyboy79 on 2013-01-10
when using the command line, you can use the tab key to auto-complete directories and files. for example, start typing
```
/media/wray/
```
and you could hit tab at that point and it would show you the files and directories within media, then once you type the first letter like "C", you can hit tab again and it will auto-complete, then again, hit tab and it will show you the directories and files in that directory, then type the first letter again and hit tab, and it will auto-complete the directory path and escape the spaces for you correctly. Hope that helps you in the future.

---

