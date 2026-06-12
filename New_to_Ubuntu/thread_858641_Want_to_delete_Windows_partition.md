---
title: "Want to delete Windows partition"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-07-13
I've had Ubuntu for months now and want to get rid of the unused XP partition hanging out on my hard drive.  I was planning on using GParted.  Problem is, I can't figure out which partition it is.  In GParted, it seems like /dev/sda1 is Ubuntu and /dev/sda3 is Windows.  I say this because /dev/sda1 has a 'boot' flag under the flag section, and when I start my computer it auto-boots to Ubuntu.  In 'sudo fdisk -l', though, I get this:
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6597    52990371    7  HPFS/NTFS
/dev/sda2           11449       12161     5727172+   5  Extended
/dev/sda3            6598       11448    38965657+  83  Linux
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris
/dev/sda6           11449       11661     1710859+  82  Linux swap / Solaris

```

which clearly shows /dev/sda3 being Linux.  Another reason I thought /dev/sda1 was Ubuntu was because I don't think I would have made the Windows partition bigger than Ubuntu's.

Anyways, now I am pretty sure /dev/sda1 is the one I want to delete (Windows), I am just posting the above so someone can hopefully verify which is which without any doubt.

So after identifying the one I need to delete, how do I do so?  In the graphical representation of the partitions in GParted, right-clicking on /dev/sda1 has a 'delete' option.  Is that all I need to do?  Also, can I delete the swap partition since Windows will be gone?

And what is the 'Extended' partition?

Thanks in advance.

---

### Post by OutOfReach on 2008-07-13
I am pretty much certain that /dev/sda1 is your Windows Installation, since Windows ONLY uses the NTFS file system.

---

### Post by halitech on 2008-07-13
/dev/sda1 is your windows partition

do you have a c:\ and d:\ when you are in windows?

---

### Post by YaroMan86 on 2008-07-13
NTFS == Windows.

GPartEd specifies exactly what file systems are what.

---

### Post by ConMan318 on 2008-07-13
Alright, so can I just right-click > 'delete' on /dev/sda1 to delete the partition?  And how about the 2 swap partitions I seem to have?  Can they go, too?

---

### Post by YaroMan86 on 2008-07-13
Keep one of them. Go ahead and toast the other if you really want to.

---

### Post by halitech on 2008-07-13
if you want to keep ubuntu then I would make sure you keep one at least, otherwise things could go haywire. not sure which you should keep though. anyone else got an idea?

---

### Post by ConMan318 on 2008-07-13
Alright, I'll just keep the swaps.  I just didn't know if their only purpose was storing files in a place that both Windows and Ubuntu could access them.

---

### Post by halitech on 2008-07-13
the swap file in linux works more like the pagefile.sys in windows. It would not work for windows as it is in a format that windows cant read.

---

### Post by ConMan318 on 2008-07-13
Alright, that was extremely simple, the reformat was essentially instantaneous.  So now I have a large unallocated partition.  How can I make Ubuntu take up that space?  Right-clicking the Ubuntu partition shows the 'resize' option grayed out.

Thanks for your help, by the way.

---

### Post by halitech on 2008-07-13
you cant resize an active (mounted partition) so you will need to boot from the Gparted cd or the live cd and do it from there

---

### Post by ConMan318 on 2008-07-13
Alright, downloading the .iso for the GParted LiveCD now.  Hopefully the resize will be as easy as the deletion of Windows. :p

Thanks again guys!

---

### Post by halitech on 2008-07-13
I've never done it myself (lack of a cd rom on the laptop where I needed it friday night) but from what I've read and seen, it should be just as easy

---

### Post by Liakath on 2008-07-13
Dear ConMan318,

> **ConMan318 said:**
> I've had Ubuntu for months now and want to get rid of the unused XP partition hanging out on my hard drive.  I was planning on using GParted.  Problem is, I can't figure out which partition it is.  In GParted, it seems like /dev/sda1 is Ubuntu and /dev/sda3 is Windows.  I say this because /dev/sda1 has a 'boot' flag under the flag section, and when I start my computer it auto-boots to Ubuntu.  In 'sudo fdisk -l', though, I get this:
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6597    52990371    7  HPFS/NTFS
/dev/sda2           11449       12161     5727172+   5  Extended
/dev/sda3            6598       11448    38965657+  83  Linux
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris
/dev/sda6           11449       11661     1710859+  82  Linux swap / Solaris

```

which clearly shows /dev/sda3 being Linux.  Another reason I thought /dev/sda1 was Ubuntu was because I don't think I would have made the Windows partition bigger than Ubuntu's.

Anyways, now I am pretty sure /dev/sda1 is the one I want to delete (Windows), I am just posting the above so someone can hopefully verify which is which without any doubt.

So after identifying the one I need to delete, how do I do so?  In the representation of the partitions in GParted, right-clicking on /dev/sda1 has a 'delete' option.  Is that all I need to do?  Also, can I delete the swap partition since Windows will be gone?

And what is the 'Extended' partition?

Thanks in advance.

Your /dev/sda1 is the Windows Partition for sure. As far as the two swap partitions /dev/sda5 & /dev/sda6 you may choose to remove /dev/sda6 as it seems to be quite large and you need to have only a maximum of two times of your RAM. Open the terminal and output the results of   

```
df
```

for us to make a decision along with the memory in your system.

Liakath

---

### Post by ConMan318 on 2008-07-13
Alright, well the deed is done, and Windows is no longer present in my laptop :).  Liakath, my 'df' output is:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             81453580  20526996  57616556  27% /
varrun                 1037144        92   1037052   1% /var/run
varlock                1037144         0   1037144   0% /var/lock
udev                   1037144        56   1037088   1% /dev
devshm                 1037144        12   1037132   1% /dev/shm
lrm                    1037144     38684    998460   4% /lib/modules/2.6.24-19-generic/volatile

```

I actually have one further question; my menu.lst file still contains an entry for the non-existant windows partition.  The end of /boot/grub/menu.lst looks like this:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

and I was just wondering how much to delete, i.e. do I delete everything below "### END DEBIAN AUTOMAGIC KERNELS LIST" or everything after the divider block, or somewhere else?  What should the end of that file look like?

---

### Post by halitech on 2008-07-13
since windows is now gone, should be able to safely delete everything after the ###

---

