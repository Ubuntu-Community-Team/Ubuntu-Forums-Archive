---
title: "Fstab Questions"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by lookitseman on 2008-05-12
I have installed Ubuntu via Wubi because I like the concept and I hate partitioning, there's always that "hold your breathe and pray" kinda of feeling that I'm trying to get rid of.  Wubi works great, but now that I'm on Hardy (from Gutsy), I need to do a little fstab work to get my drives mounting.  On Gutsy they worked fine.

Here's the deal, I've got my Drobo unit mounted at /dev/sdb.  /dev/sdb2 is my music partition which it recognized fine.  however, /dev/sdb1 is my life and Hardy doesn't wanna recognize it.  Gparted lists it as an unknown file system.

Here's my fstab
```

# /etc/fstab: static file system information.
#
# <file system>                <mount point>   <type>  <options>       <dump>  <pass>
proc                           /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk   /               ext3    loop,errors=remount-ro  0       1
/host/ubuntu/disks/boot        /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk   none            swap    loop,sw         0       0
/dev/scd0                      /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Ordinarily I would probably add the following to the file and give that a shot:
/dev/sdb1   /media/Drobo   ntfs  default  0 0

However, it recognized and mounted my music at "/media/Drobo Music", but it's not in the fstab, leading me to believe there's some key point I'm missing in this grand scheme.

Am I missing something?  I'm still rather new with the whole linux thing, and this is probably something simple I"m overlooking.

Thank you for your help, I don't wanna take a stab and fstab (har har...) and mess up, that's for sure.

---

### Post by Victormd on 2008-05-12
Here are a few checks before you edit your fstab.
When you boot into ubuntu, even though you don't have your ntfs partitions on the desktop, they should be listed in the menu "Places". Simply click on it and it should show up on your desktop.

Now, if you want to leave the same mount point as the ubuntu default, browse to your media folder (or in the terminal type cd /media then ls) and look at the mountpoint given to your ntfs partition (i.e. folder called backup - in my case).

Now from the terminal, type
```
sudo fdisk -l
```

this will list all your partitions. This is what my looks like.
> 
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2550 20482843+ 7 HPFS/NTFS
/dev/sda2 2551 4400 14860125 83 Linux
/dev/sda3 4401 4462 498015 82 Linux swap / Solaris
/dev/sda4 4463 9725 42275016 7 HPFS/NTFS
So from this list, I know I want to mount /dev/sda1 and /dev/sda4

Now, from the terminal type
```
sudo gedit /etc/fstab
```

this will open your fstab. Let's say I wanted to mount my /dev/sda1, then I would add this to the last line:
> 
/dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 1
This will mount /dev/sda1 in the /media/backup folder (as explained above)
simply keep adding lines as you need more partitions. Save your fstab and reboot. You should now get the partitions automatically mounted and the respective icons on your desktop.

An alternative is to add a line to the end of fstab using the UUID option instead of /dev/sda1. You can determine the UUID by using (i.e., for sda1)
```
sudo vol_id -u /dev/sda1
```

so your fstab file will have this line
> 
UUID=NUMBER_ID /media/backup ntfs defaults,umask=007,gid=46 0 1
where NUMBER_ID is the output from vol_id for your device, i.e.:
UUID=78980E1B980DD890 /media/backup ntfs defaults,umask=007,gid=46 0 1
instead of
/dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 1
I found this to be more stable/suitable than using the /dev/sda1 option. I don't know if with WUBI this will work the same way, but I'm assuming that it should...

Hope this helps

---

### Post by lookitseman on 2008-05-13
Thank you for your help, it has been very useful.

Here's what I did...
I added this to my fstab

```

#mine...fingers crossed
/dev/sdb1     /media/drobo    ntfs    defaults,umask=007,gid=46 0 1 

```

I don't know what the umask and gid are for, but I'm sure I'll learn over time.

I ran
```

sudo mount -a

```

To mount the drives, which it told me that the drive was not properly ejected.  Went to windows, properly ejected it, came back to linux, and it didn't mount at startup.

Ran mount -a again, tuns out the mountpoint needed to be preexisting, so I made the /mount/drobo folder, ran mount -a one more time, and it mounted!

I'm assuming when I restart I won't have future trouble mounting the device.

I agree that using the UUID is more secure, I'll probably tweak this down the line to take that route, for now I'm just happy with what I've got.

Thanks again!

---

### Post by Xiong Chiamiov on 2008-05-13
Just to wrap up a few things that came up:

umask is an option for setting permissions.  It works exactly the opposite of chmod.  A setting of 007 gives full priviledges for the owner and those in the same group, but not for anyone else.

gid is... [googling] the group that get the ownership of the hard drive, I guess.

Yes, you must have a folder created before mounting something to it.

And, using the UUID will keep you from having to change things if you rearrange the order of drives in your system.  I personally use the /dev/sda1 format because it makes my fstab cleaner and easier to read, but I muck around in it too much and am not bothered with having to change it.

---

### Post by Victormd on 2008-05-13
Don't forget to mark this as solved if you solved it... :)
best wishes...

---

### Post by Inxsible on 2008-05-13
Check out the link in my signature for fstab. It explains a great deal about it.

---

