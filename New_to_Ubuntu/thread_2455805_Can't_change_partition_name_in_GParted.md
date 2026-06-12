---
title: "Can't change partition name in GParted"
date: 2020-12-28
forum: New to Ubuntu
---

### Post by zeenx1 on 2020-12-28
I have tried restarting the system multiple times and still can't change the name of the partition:(((. Pls helpppp
ref:[COLOR=#FFFFFF][FONT=&quot]https://imgur.com/a/PqmtWTW[/FONT][/COLOR]

---

### Post by rbmorse on 2020-12-28
Not sure what the problem is. Will the dialog box for Partition Name not accept any input at all, or that the name you enter does not "stick" when you close gparted? 

If it's the latter, after you enter the name in the dialog box you have to click on the little arrow in the menu bar to commit (finalize) the change.

---

### Post by zeenx1 on 2020-12-28
Partition Name doesnt accept any input at all, it is a grey text box for some reason

---

### Post by CelticWarrior on 2020-12-28
Is it mounted? It seems you're trying to make the change in a running system. Usually we do it in a live session. Depending on which partition you're trying to change you may do it from the installed system but said partition cannot be mounted.

---

### Post by zeenx1 on 2020-12-28
im a noob lol, i just burnt ubuntu to a pendrive and clicked try ubuntu then started to partition in GParted. I dont know whether im in a live session or not

---

### Post by CelticWarrior on 2020-12-28
Yes, that is a live session.

Now, which partition are you trying to rename, exactly?

---

### Post by zeenx1 on 2020-12-28
I was followning this tutorial on yt:[https://www.youtube.com/watch?v=gvYM6hqTkQo](https://www.youtube.com/watch?v=gvYM6hqTkQo) I was renaming partition for root boot and home

---

### Post by CelticWarrior on 2020-12-28
I'm out of here.
I'm definitely not wasting 20 minutes of my life to watch a video by some random silly college kid.

---

### Post by zeenx1 on 2020-12-28
lmao

---

### Post by zeenx1 on 2020-12-28
mind if you recommend me a tut?

---

### Post by CelticWarrior on 2020-12-28
It depends.

What exactly are you trying to do? Please explain that in detail, NOT what you think is a solution, the typical X-Y problem...

---

### Post by oldfred on 2020-12-28
There now are two labels, if using gpt, file system & partition (partlabel).

For ext4 formatted partitions, other tools for other formats:
[http://askubuntu.com/questions/276911/how-to-rename-partitions](http://askubuntu.com/questions/276911/how-to-rename-partitions)
Easy way to label partitions
System> Admin.> Disk Utility

WARNING: mke2fs will reformat your partition and set a label at the same time. This will delete any data on the target partition.

To see labels:
lsblk -o name,fstype,size,fsused,label,partlabel,mountpoint

To set a label without reformatting use e2label or tune2fs
1. Make a label and format Do not use unless new partition:
     # mke2fs -L <label> <dev>
2. Make a label
      e2label <dev> <label>
          tune2fs -L <label> <dev>
sudo e2label /dev/sdb8 groovy
sudo e2label /dev/sda4 focal

For gpt partition's  label you can use gdisk. see
man gdisk

sudo gdisk /dev/sda
Command (? for help): c
Partition number (1-7): 6
Enter name: kubuntu
w to write change


Shows other tools also:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by zeenx1 on 2020-12-28
all I'm trying to do is install Ubuntu on my external hard disk, but can't proceed as I can't name the partition, so can you share a tutorial on youtube which would help me install ubuntu
Thanks for sticking lol

---

### Post by zeenx1 on 2020-12-28
Thankssssssss

---

### Post by zeenx1 on 2020-12-28
Finally found the correct phrase for it: I want to map a name to the partition!!!! Finallllyyyyy

---

### Post by oldfred on 2020-12-28
If UEFI & gpt partitioning, you have to partition in advance.
Are  you now discussing mklabel which is different than labeling a partition. 
That is labeling a drive as either the 40 year old MBR (msdos) partitioning used with BIOS or the newer gpt partitioning used with UEFI (and with Linux can be used with BIOS also).

This erases drive and converts it to gpt partitioning for UEFI type installs.
sudo parted /dev/sdaX mklabel gpt # where sdX is your drive like sdb, sdc etc, not a partition like sdc5

You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.

See link below in my signature for lots more info & links to even more details.

Install Ubuntu in UEFI mode on second HDD without affecting first HDD
[http://ubuntuforums.org/showthread.php?t=2305876](http://ubuntuforums.org/showthread.php?t=2305876) & 
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312) & 


Note with UEFI installs, Ubuntu's Ubiquity installer only wants to install grub to first drive's ESP.

[https://askubuntu.com/questions/1296065/dual-booting-w10-ubuntu-with-2-separate-ssds-in-uefi-mode/1296153#1296153](https://askubuntu.com/questions/1296065/dual-booting-w10-ubuntu-with-2-separate-ssds-in-uefi-mode/1296153#1296153)
Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

