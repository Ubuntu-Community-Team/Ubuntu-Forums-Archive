---
title: "Trouble creating a separate home partition"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by gerhard34 on 2008-08-24
I found this HOW-TO by Robin Catling in the Full Circle Magazine, Issue 15 and was very happy, for I have been looking for a long time for such an instruction.
Unfortunatly it did not work as it should, though I truely followed the instructions. After I entered the first commands

[I]sudo mkdir /mnt/newhome
sudo mount -t ext3 /dev/hda3 mnt/newhome
sudo mkdir /mnt/oldhome
sudo mount -t ext3 /dev/hda1 /mnt/oldhome[/I]
 
which worked quite normal, I entered *cd /oldhome*  which brought the message *No such file or diectory* which I do not understand, for the *mkdir /mnt/oldhome* must have created this directory.

Does anyone have an idea how to solve this problem or should I post directly to the Full Circle Magazine?

Thankful for any suggestion.:confused:

Gerhard

---

### Post by Malta paul on 2008-08-24
I'm sure your directory is there. sudo cd /mnt/newhome and you should go into it. It is in root.

If you want to use GUI go to Places>search for files.

:)

---

### Post by Elfy on 2008-08-24
I haven't read the articel but if you haven't

sudo mkdir /mnt/oldhome

the cd command won't work

---

### Post by gerhard34 on 2008-08-24
Sorry, *sudo cd /oldhome* did not work either. Same message: *No such file or directory* 

@ forestpixie: What do you mean by "replicated the command"? Since I am not an English native speaker I got no idea what to do.

Gerhard

---

### Post by Elfy on 2008-08-24
Got it all wrong - sorry read it wrong 

you are trying to change to /oldhome it's /mnt/oldhome

```
cd /mnt/oldhome
```

---

### Post by garyed on 2008-08-24
I'm a little confused.
I thought to create a separate partition you needed to use Gparted or fdisk or something similar first to create it before you mount it.

---

### Post by Elfy on 2008-08-24
The partitions were already there

> sudo mkdir /mnt/newhome
sudo mount -t ext3 [COLOR="Red"]/dev/hda3[/COLOR] mnt/newhome
sudo mkdir /mnt/oldhome
sudo mount -t ext3 [COLOR="#ff0000"]/dev/hda1[/COLOR] /mnt/oldhome

You can make the folder anywhere you want and then mount them, in this case 2 folders in /mnt, ubuntu usually uses /media - eg

/mnt/one/folder/inside/another/one

so you could mount it in there. You'd have to read the whole article to get it all - or use psychocats 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://fullcirclemagazine.org/issue-15/](http://fullcirclemagazine.org/issue-15/)

---

### Post by gerhard34 on 2008-08-24
First of all thanks. The hint to alter the *cd /oldhome* to*cd /mnt/oldhome* has been successful. So I could copy the contents of home as described in the article. It took about 45 minutes! But then the troubles started again. By the way: Of course I have read the article several times. I could not rename the old /home as a safe backup and mount the new home as stated on page 10 though I followed the description very carefully. There must be another bug in the article. I will study psychocats to find out if I can mount my sdb3-partition (which already contains the contents of home) as /home and get rid of the old home in the sdb1-partition.

---

### Post by Elfy on 2008-08-24
When I wanted to do the same thing last year the psychocat tutorial was the one I followed. 

If you could post the command which failed then we could make sure the syntax is correct - you can get commands back in aterminal by using the up arrow, laternatively you can view your whole history with 

```
cat ~/.bash_history
```

---

### Post by Elfy on 2008-08-24
I just want to check something here - when you followed the article did you make sre that you changed his /dev/hda3 /mnt/newhome for example to match the partitions you actually have on your system?

If you are at all unsure about what I am saying then open a terminal and run

```
sudo fdisk -l
```

---

### Post by gerhard34 on 2008-08-24
The bash_history does not work for of course I entered the commands while in the Live-CD session. The result of *sudo fdisk -l*
Platte /dev/sda: 80.0 GByte, 80060424192 Byte
255 Köpfe, 63 Sektoren/Spuren, 9733 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xdfe1dfe1

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9733    47464042+   f  W95 Erw. (LBA)
/dev/sda5            3825        6434    20964793+   b  W95 FAT32
/dev/sda6            6435        9733    26499186   83  Linux

Platte /dev/sdb: 60.0 GByte, 60022480896 Byte
255 Köpfe, 63 Sektoren/Spuren, 7297 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xe22521d3

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1        3213    25808391   83  Linux
/dev/sdb2            7110        7297     1510110    5  Erweiterte
/dev/sdb3            3214        7109    31294620   83  Linux
/dev/sdb5            7110        7297     1510078+  82  Linux Swap / Solaris

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge
gerhard@gerhard-desktop:~$

---

### Post by Elfy on 2008-08-24
If you used the commands as they are eg

sudo mount -t ext3 /dev/hda3 mnt/newhome

sudo mount -t ext3 /dev/hda1 /mnt/oldhome

It would be trying to mount in the wrong place I think, for one thing I'm not sure it would know hda from sda.

Further - if hda1 did get recognised as sda1 then it would be trying to do it with the ntfs drive and sda3 doesn't actually exist.

As long as you changed the hda? to match your system's sda or sdb - that was all I wanted to check with you.

---

### Post by gerhard34 on 2008-08-24
It was the command *sudo mv /oldhome/home /oldhome/home_backup* which did not work. The answer was: Call of stat for /oldhome/home not possible. No such file or directory. This was the end of the long journey

---

### Post by Elfy on 2008-08-24
Yea - that's cool I was just checking :)

Good luck with it

---

### Post by gerhard34 on 2008-08-24
I have to excuse. In my first posting I mentioned hda1 and hda3 , because I copied from the article. When executing I used of course sdb1 and sdb3

---

### Post by Elfy on 2008-08-24
LOL that was what I wanted to check

and why I couldn't understand the lack of errors :D

---

### Post by gerhard34 on 2008-08-25
Hello, I passed an adventurous morning by following the commands in the psychocats tutorial. After entering the suggested codelines and rebooting everything was over. Did not boot the normal way, told me that there is no /home and something more. My rescue were the four code lines at the end of the tutorial. It brought me back to normal life. I think I'll let it be. After all many thanks for your assistance.
Gerhard

---

### Post by Elfy on 2008-08-25
Maybe have another go at a later date; the tutorial does work, or at the least did for me and som eothers I've shown it too.

To be honest by the time I next reinstall all that I will have in my /home will be configs as everything else has now been moved to seperate data partitions, so a quick backup of the little left will be all I will need to do.

Good luck.

---

