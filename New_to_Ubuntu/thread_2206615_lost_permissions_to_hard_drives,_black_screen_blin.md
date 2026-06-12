---
title: "lost permissions to hard drives, black screen blinking cursor, live cd works"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by styrofoam-feet on 2014-02-19
I have been trying for ahwile to change the permissions for my internal hard drives ( desktop, 3 internal SATA, and a cluster**** of partitions).lost and found, cannot read or write or access, ecept for filesystem drive. I cannot figure it out on my own. I have scoured countless forums, asked a few for help, its just not clicking. Or I am just ****ing it up every time. BUT now I have a bigger problem that has arisen. I can't load to the desktop. Grub starts, I can go through all the options, but after I choose one, blinking cursor on a black screen. infinity. I can boot live cds and everything is cool, have done lubuntu 13.04 and ubuntu 12.04, great success. But now I cannot login as root on livecds, so my hard drives are still off limits, or else I would just reformat and say **** it. I'm afraid I will reformat the filesystem drive and the computer will not recognize the previous root privileges on my media drives, and then I will forever lose my data. I can wipe the drives, but I really would like to recover my stuff. So if anyone can start me on the right track, as if I know nothing at all, I would be very appreciative...

---

### Post by varunendra on 2014-02-20
Welcome to the forums styrofoam-feet !

Try not using words that need to be filtered out by the forum's automatic filters. :P

From Live CD/USB, you can access the files/partitions with root access by opening the file-manager as root -
```
gksu nautilus
```
If using a version later than 12.04, you may have to install "gksu" first -
```
sudo apt-get install gksu
```
**[COLOR="#FF0000"]CAUTION !![/COLOR]** Any files you copy/modify in this mode will become owned by root, so be VERY CAREFUL while you are running the file manager as root.

And if you do a fresh install on the hard disk, you can become the owner of both the partitions and their contents recursively by the following command -
```
sudo chown -R **user:user** /media/*<mount-point of the partition>*
```
..where "user" would have to be replaced by the user name that you need the partition/contents to be owned by.

VERY IMPORTANT : In your attempt to modify permissions, try not to play with 'chmod' until you have safely backed up all the data in its current state, and/or know very well what you are doing. Otherwise you may accidentally convert directories into files which will be useless and irreversible.

---

### Post by styrofoam-feet on 2014-02-21
Hey, thanks for the reply! It worked! I recovered my information. So at this point I was hoping to just start over. Is there a way to just reformat every internal drive with one foul swoop? Effectively getting rid of all partitions and permissions stuff? Then I can do a fresh install and get on the right track.

---

### Post by varunendra on 2014-02-21
> **styrofoam-feet said:**
>  Is there a way to just reformat every internal drive with one foul swoop? Effectively getting rid of all partitions and permissions stuff? Then I can do a fresh install and get on the right track.

Sure.

If you are going to install on the same drive whose partitions you want to remove, simply choose the option to "Use Whole Disk" during installation. It will automatically remove all existing partitions, create new ones as the OS needs (probably one large partition occupying almost all of the disk space + a small swap partition), and install itself.

If you want to use it just as storage, not install any OS on it, use GParted (Live CD/DVD already has it, installed one will need it to be installed first) to remove the existing partitions and recreate them. Choosing Device > Create Partition table.. option in GParted menu will remove all existing partitions in one go, but deleting them one-by-one is also as easy as right-click on them (in gparted) > delete > Apply

Be aware though that if the partition you create with GParted is capable of storing permission bits (like EXT2/3/4 partitions), **they will again be owned by 'root' at the time of creation** (because Gparted only runs with root permissions, means it was 'root' who created the partitions). So as soon as you get into your installed version of Ubuntu, the first thing you should do it to either 'Own' it to your user (the "sudo chown -R user:user <mount-point>" command), or change its permission to 777 ("sudo chmod -R 777 <mount-point>") so that everyone has the right to read/write/execute the data on it.

If changing permission to '777', make sure to do it BEFORE there is any data on the partition, otherwise all the files on the partition will become executable which is something that probably nobody wants. Removing the 'executable' bit recursively is also something you shouldn't even try, since it will render the directories 'Unreadable' (directories do need the 'executable bit' (x, or permission '7') to list their contents).

---

