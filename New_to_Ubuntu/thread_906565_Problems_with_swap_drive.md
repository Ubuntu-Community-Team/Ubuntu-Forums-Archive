---
title: "Problems with swap drive"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by thesonglessbidr on 2008-08-31
I have two physical hard drives, the first is partitioned for Vista and Ubuntu, the second is where I dump all my music and work etc.

When I installed Ubuntu, I set this second drive as the swap drive, expecting it to just create a file to use as swap, like Windows. Now the drive doesn't show up in Windows and I really could do with accessing the files on the drive...

...is there some way to resolve this or have I made a huge mistake?

---

### Post by Elfy on 2008-08-31
Can you run this command from a terminal in ubuntu please

```
sudo fdisk -l
```

This link [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) will maybe help to recover some of the data.

---

### Post by thesonglessbidr on 2008-08-31
Ok...

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d49085c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59527   478144504    7  HPFS/NTFS
/dev/sda2           59528       60801    10233405   83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18ff18fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24793   199146496   82  Linux swap / Solaris


```

---

### Post by Elfy on 2008-08-31
Yea - you made a mistake the secdond hard drive is all swap.

If you haven't rebooted yet, wait a moment I'll be back.

---

### Post by eyyou101 on 2008-08-31
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by thesonglessbidr on 2008-08-31
Ok...appreciate the help!

---

### Post by Elfy on 2008-08-31
Turn off swap in your ubuntu you will have to work without for the moment

```
sudo swapoff -a
```

---

### Post by Elfy on 2008-08-31
Unmount the swap drive as well

```
sudo umount /dev/sdb1
```

---

### Post by Elfy on 2008-08-31
Check that it has unmounted please with

```
df -h
``` post the output of that command for me, I have another link 

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) you are going to need both tthat and the one I gave earlier.


Edit - install testdisk - from aterminal run

```
sudo apt-get install testdisk
```

---

### Post by thesonglessbidr on 2008-08-31
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.7G  2.5G  6.8G  27% /
varrun                2.0G  100K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   56K  2.0G   1% /dev
devshm                2.0G   12K  2.0G   1% /dev/shm
lrm                   2.0G   44M  1.9G   3% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      9.7G  2.5G  6.8G  27% /home/dan/.gvfs

```

---

### Post by Elfy on 2008-08-31
Run top in a terminal - need to make sure swap is off.

Also did you see the edit to install testdisk above.

---

### Post by thesonglessbidr on 2008-08-31
Swap: 0k total, used and free. I presume this means it's definitely off?

Testdisk is installed ok.

---

### Post by Elfy on 2008-08-31
OK - this will be fun then as I've not used the program, run it with ```
sudo testdisk
``` - see if it can find the old partition information


This link should be helpful, with screenshots - you're going to have to change some things as you are not running from a livecd - you will likely need some spare space to copy recovered data to. How full was the 260Gb drive before you partitioned it?

[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

---

### Post by Yannick Le Saint kyncani on 2008-08-31
Hi thesonglessbidr,

Yeah, you've made a big mistake. Basically you've formatted your entire second drive with swap.

Photorec is a program that's supposed to be able to recover most of your data though. It's available in package "testdisk".

Also open a console (accessories->terminal I think) and "sudo nano /etc/fstab". Remove the line that contains swap, as you don't want to modify anything on this disk from now on.

You may want to buy another disk at least as big as your second one and try to recover your files using photorec. There should be some howtos on the web.

Good luck, even though you must be pretty distraught after such a big mistake.

---

### Post by Elfy on 2008-08-31
> Also open a console (accessories->terminal I think) and "sudo nano /etc/fstab". Remove the line that contains swap, as you don't want to modify anything on this disk from now on.Good catch - didn't think about a possible reboot and swap turning on again.

Edit - to stop swap loading

open file to edit
```
gksudo gedit /etc/fstab
```

Find line which will appear similar to and put # at beginning of the line

```
# /dev/sdb1
[COLOR="Red"]#[/COLOR]UUID=f5a73ef7-b700-4e6c-b23e-489197b33e62 none            swap    sw              0       0
```

Save the file, you'll be able to reboot now without swap turning on, so the drive will not be touched.

---

### Post by thesonglessbidr on 2008-08-31
Thanks for all the help...managed to get some files back, but i've still lost a fair bit of work. Guess it's time to invest in an external hard drive!

---

### Post by Elfy on 2008-09-01
Did you try to retrieve the partition table, [this]("http://www.techsupportforum.com/hardware-support/hard-drive-support/194492-have-you-lost-hard-drive-partition-files-your-computer.html") might help if you didn't although it's for windows it should be applicable for you.

Once you have got back all the data you can you will need to deal with your swap - you won't be needing to have 260Gb  :) when you're ready either make a new rtthread or we can do it here.

---

