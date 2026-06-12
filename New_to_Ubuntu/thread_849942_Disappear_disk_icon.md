---
title: "Disappear disk icon"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by kobras on 2008-07-05
8 hours before i have copied photos to my notebook, but now its impossible to find any information. SDA5 icon have disappeared from desktop, and directory /media/sda5/ empty:(
maybe this information can help to find the problem
maryan@maryan-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  7.9G  5.3G  61% /
varrun                252M   84K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   76K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile

 PS sorry for my bad English

---

### Post by ZabiGG on 2008-07-05
It appears your sda5 drive is not mounted. 

Try this:

sudo mount /dev/sda5 /media/sda5

You should be able to access that partition.

---

### Post by kobras on 2008-07-06
I dont know some mistake...

$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda5': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

---

### Post by ZabiGG on 2008-07-06
OK. What format is sda5? 

If you open Gparted, you'll see it easily. You'll have to tell me if it is NTSF, FAT, EXT2, EXT3 or any other format before I can try to help you more.

If you don't have Gparted on your system, search for it in Synaptic or enter this in a terminal:

```
sudo apt-get install gparted
```

Then, to launch it, click System > Administration > Partition Editor.

Then please report back. Can you also attach the result of this command:

```
dmesg > dmesg_txt
```

(You might have to compress the document to upload it. You should find text document dmesg_txt in your /home/yourusername folder)

Thanks,

Z.

---

### Post by kobras on 2008-07-06
now i have get only dmesg.txt. My notebook dont have internet connection so i will try tomorrow install Gparted.

---

### Post by kobras on 2008-07-08
its info from Partition Editor:

---

### Post by zakirs on 2008-07-08
last time when you used windows did you forced it to shut down ?

---

### Post by DezSP on 2008-07-08
The NTFS partition has been marked as "dirty" and needs to be checked by Windows. This should happen automatically when you boot into Windows, but if it doesn't or you don't have it installed you can use an XP or Vista CD recovery console to run "chkdsk /f", which will scan (and hopefully fix) any errors on the drive. Linux cannot perform repairs on NTFS, so you must use Windows for this.

---

### Post by kobras on 2008-07-09
i have installed ntfsprogs, and use ntfsfix, now its works. But one folder with photos i can not open, all time:
The folder contents could not be displayed
How i can copy this folder or open?

---

