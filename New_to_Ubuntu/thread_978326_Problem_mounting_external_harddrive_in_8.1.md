---
title: "Problem mounting external harddrive in 8.1"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by DieHards77 on 2008-11-11
Ive been searching over the past week and havent found anything that would work.
Im a new Linux user of a few weeks and before i upgraded to 8.1 my hard drive was mounting perfectly fine now I upgraded and it wont mount I keep getting the error box saying:
"You are not privileged to mount the volume 'Iomega HDD"

These are the settings for my hard drive

[IMG]http://img88.imageshack.us/img88/5162/volumego0.jpg[/IMG]

[IMG]http://img205.imageshack.us/img205/9421/drivede3.jpg[/IMG]

any suggestions would be great, thanks a lot and i appreciate any help

---

### Post by sven_wien on 2008-11-11
lol,

with my IOMEGA_HDD i have simelar problem.
For me it says cant mount volume, any ideas?

---

### Post by DieHards77 on 2008-11-11
also when i try to mount it through disk manager this is what i get

"$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details."

---

### Post by DieHards77 on 2008-11-11
> /dev/sda1: UUID="a3a40d3c-b4b3-46d0-8a0c-ffc9e5823754" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="311be9a7-6f1d-4da3-8599-25ff97b85924" 
/dev/sdb1: UUID="D27431CF7431B6D7" LABEL="Iomega HDD" TYPE="ntfs"

thats what i got when i ran 

sudo blkid in terminal

---

### Post by fenian on 2008-11-11
Have you tried editing yourr fstab?Open a terminal and enter...

> sudo mkdir /media/widows

this creates the mount point for the drive.
Now to edit the fstab in the terminal enter...

> sudo gedit /etc/fstab

you will get a text editor with  something like this (this is mine yours will be alittle different)
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6a1083b3-d1d7-4bc2-ae64-d13f0dc05cfc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9e956bb8-97da-416e-9851-e14d51d208bf none            swap    sw              0       0
# /dev/sdb1     
UUID=052b7d71-73d0-4fb4-956f-7f02feb49bf0 /media/vortex   xfs     defaults        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Look for a line with /dev/sdb1 if you find one replace it with (if you live outside the US change the locale accordingly)...

> # /dev/sdb1 
UUID=D27431CF7431B6D7 /windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

If there is no entry for /dev/sdb1 add one (paste the following)
> 
# /dev/sdb1 
UUID=D27431CF7431B6D7 /windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

Then mount the drive with the command...

> sudo mount -a

---

### Post by DieHards77 on 2008-11-11
hmm i tried that and this is what i got 

> jayloewy@jayloewy-laptop:~$ sudo mount -a
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


thanks again for your help i definitly appreciate this

---

### Post by Ryadt on 2008-11-11
Try changing the permission of the drive```
sudo chmod -R 777 /media/lomega_HDD
```

---

### Post by fenian on 2008-11-11
You need to boot into windows and run chkdsk /f ,instructions on how to do this are [here]("http://www.ehow.com/how_2052292_run-chkdsk-f-windows-xp.html").You then need to boot into  Windows two times before booting back into Ubuntu.

---

### Post by DieHards77 on 2008-11-11
> **fenian said:**
> You need to boot into windows and run chkdsk /f ,instructions on how to do this are [here]("http://www.ehow.com/how_2052292_run-chkdsk-f-windows-xp.html").You then need to boot into  Windows two times before booting back into Ubuntu.

i dont have windows installed on my laptop, only ubuntu but ill try that on my roomates laptop tomorrow, thanks a lot

---

