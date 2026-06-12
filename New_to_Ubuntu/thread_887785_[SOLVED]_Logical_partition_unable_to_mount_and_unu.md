---
title: "[SOLVED] Logical partition unable to mount and unusable..."
date: 2008-08-12
forum: New to Ubuntu
---

### Post by ionizd on 2008-08-12
Hi, all.
 I once had this laptop set up as a dual- boot Windows XP/ Xubuntu machine and decided to remove the Windows installation.  I reformatted the Windows partition using Gparted to ext3.  That partition doesn't show up in my Thunar file manager and  whenever I start Gparted, the following message pops up;
Failed to mount "20G Volume".
 I searched for similar issues, but nobody seemed to have any advice that would help me.
 I did have to enter my password to make the changes described above, but I didn't unmount the drive before reformatting.  I don't have the option now, however, since the Partition>unmount option on the toolbar is grayed out.
 I'd really like to have this partition to use as data storage, can anyone help?

---

### Post by theyranos on 2008-08-12
Can we see your current partition layout? Paste the results of ```

sudo fdisk -l
cat /etc/fstab
mount

```

---

### Post by ionizd on 2008-08-12
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2517    20217771   83  Linux
/dev/sda2   *        2518        4795    18298035   83  Linux
/dev/sda3            4796        4864      554242+   f  W95 Ext'd (LBA)
/dev/sda5            4796        4864      554211   82  Linux swap / Solaris
ionizd@ionizd-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6764e73c-be55-455c-b67c-afc10c44eb5a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
ionizd@ionizd-laptop:~$ mount

---

### Post by theyranos on 2008-08-12
The (formerly) windows partition is /dev/sda1, yes?

What happens if you try to forcibly mount it from the command line?
```

mkdir mountpoint
sudo mount -t ext3 /dev/sda1 mountpoint 

```

---

### Post by ionizd on 2008-08-12
In regards to your question, yes, I think so...
ionizd@ionizd-laptop:~$ mkdir mountpoint
ionizd@ionizd-laptop:~$ sudo mount -t ext3 /dev/sda1 mountpoint
ionizd@ionizd-laptop:~$ 
 Now what?

---

### Post by theyranos on 2008-08-12
It looks like it worked. If I'm right, the "mountpoint" folder is now your formerly windows partition. You can test that by typing ```
df --si
``` If the output of that command mentions /dev/sda1 at all (it should show it as being 20 GB of empty space), then your ex-windows partition is successfully behaving as an ext3 partition.

The problem is, it'll go away when you reboot and there's a pretty good chance it's not going to let you write to it unless you're root.

To make the change more perminant and fix the permissions errors, make a folder somewhere (without any spaces in the path or name) that you'd like to refer to your second partition, then add this line to /etc/fstab:```
/dev/sda1 /path/to/that/folder/you/just/made ext3 defaults 0 0
```

Then, if you
```

sudo umount mountpoint # unmount the temporary thing I had you do earlier
sudo mount -a # mount the stuff that /etc/fstab says to mount

```

you should be all set.

---

### Post by ionizd on 2008-08-12
> **theyranos said:**
> It looks like it worked. If I'm right, the "mountpoint" folder is now your formerly windows partition. You can test that by typing ```
df --si
``` If the output of that command mentions /dev/sda1 at all (it should show it as being 20 GB of empty space), then your ex-windows partition is successfully behaving as an ext3 partition.

The problem is, it'll go away when you reboot and there's a pretty good chance it's not going to let you write to it unless you're root.

To make the change more perminant and fix the permissions errors, make a folder somewhere (without any spaces in the path or name) that you'd like to refer to your second partition, then add this line to /etc/fstab:```
/dev/sda1 /path/to/that/folder/you/just/made ext3 defaults 0 0
```
 [COLOR="Red"]Sooo... I just make a folder on my desktop or something?  Does it matter where I make said folder?[/COLOR]

Then, if you
```

sudo umount mountpoint # unmount the temporary thing I had you do earlier
sudo mount -a # mount the stuff that /etc/fstab says to mount

```
 [COLOR="Red"]Sooo... I use the same command code as I did before, substituting "umount" for "mount"?[/COLOR]

you should be all set.
 I'll have to try this later. Thanks in advance if it works.

---

### Post by theyranos on 2008-08-12
[Quote=ionizd]
Sooo... I just make a folder on my desktop or something? Does it matter where I make said folder?
[/Quote]

Not really, although you probably should avoid places like /dev or /proc.

[Quote=ionizd]
Sooo... I use the same command code as I did before, ubstituting "umount" for "mount"?
[/Quote]

Once this is set up, you probably won't have to type any mounting-related commands again until the next time you change your partition layout or get new hardware. 

That "umount" command just removes the connection between your windows partition and the "mountpoint" folder I had you create back in post #4 to check whether the partition was working. Once the fstab entry is there, "sudo mount -a" will connect that partition to whatever folder you pointed to in /etc/fstab.

[Quote=ionizd]
I'll have to try this later. Thanks in advance if it works.
[/Quote]

Good luck. Post back if it doesn't :)

---

### Post by ionizd on 2008-08-12
Okay, it appears that the logical drive is linked to the folder I created, I can move folders and files to it and they appear when I open the file.  Also, when I right click>properties that folder, it says that the file's size is 18 Gb.  Should I be alarmed that Gparted reports the following when I open it?

[COLOR="Red"]Failed to mount "20G Volume".
org.freedesktop.hal.storage.mount-fixed auth_admin_keep_always <-- (action, result)[/COLOR]

WTF?  I thought this was solved.  I may want to do other things with this partition in the future.

***EDIT*** I guess this says it all;
> Once this is set up, you probably won't have to type any mounting-related commands again until the next time you change your partition layout or get new hardware.
...but I still have no idea why Gparted says it's not mounted.

---

### Post by theyranos on 2008-08-13
[quote=ionizd]I still have no idea why Gparted says it's not mounted.[/quote]

Neither have I, but I'm more of a command-line guy anyway. If you haven't already, you might try starting another thread just about the Gparted problem and hope someone more knowledgable happens by.

---

### Post by comer on 2008-08-14
You can try to use a partition table docctor to recover your partition.I recommend EASEUS Partition Table Doctor.It can recover the deleted, damaged, lost or corrupted partitions on hard drive and backup/restore MBR, partition table, boot sectors. [http://www.ptdd.com/](http://www.ptdd.com/) 
Hope this can help you!

---

