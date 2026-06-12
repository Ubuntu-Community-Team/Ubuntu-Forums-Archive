---
title: "unable to mount NTFS drives not privleged"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2008-10-24
Hi I have 2 NTFS drives
STORAGE 320 and STORAGE 750
They both show up under Computer but when I click on them I get the message.

> You are not privileged to mount the volume 'Storage750'.

I had got them to auto mount by adding them to fstab but this worked fine so I'm not sure if thats relevant.
I'm not sure how long I've been unable to access them but its been a few days at least

---

### Post by northern lights on 2008-10-24
Can you please post the outputs of ```
sudo fdisk -l
``````
cat /etc/fstab
```and```
sudo mount -a
```Thank you.

---

### Post by bigmonmulgrew on 2008-10-24
sudo fdisk -l
```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c203c1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3937    31623921    7  HPFS/NTFS
/dev/sda2            3938        9039    40981815    f  W95 Ext'd (LBA)
/dev/sda5            3938        4183     1975963+  82  Linux swap / Solaris
/dev/sda6            4184        9039    39005788+  83  Linux

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdee5314c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x040be534

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=c4668640-20c8-463a-bd8c-36243eabff09 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f462f4f7-f404-4e14-a1ed-250adfc79396 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 	/media/Storage750 ntfs defaults 	0 	0
/dev/sdc1 	/media/Storage320 ntfs defaults 	0 	0

```

sudo mount -a
```
fuse: failed to access mountpoint /media/Storage750: No such file or directory
fuse: failed to access mountpoint /media/Storage320: No such file or directory

```

The folders arent there. I cant create them either

---

### Post by Nepherte on 2008-10-24
You have to create the two mounting points in advance:
```
sudo mkdir /media/Storage750
sudo mkdir /media/Storage320
```

---

### Post by northern lights on 2008-10-24
> **bigmonmulgrew said:**
> 
sudo mount -a
```
fuse: failed to access mountpoint /media/Storage750: No such file or directory
fuse: failed to access mountpoint /media/Storage320: No such file or directory

```

The folders arent there.
That's what *mount* is complaining about...

> **bigmonmulgrew said:**
> I cant create them either.That's what should be done though. Are you sure you can't?

Run ```
sudo mkdir /media/Storage750 && sudo mkdir /media/Storage320
```and then```
sudo mount -a
```again. Drives should now mount.

---

### Post by bigmonmulgrew on 2008-10-24
ah thank you both.
Not sure why the folders got deleted but there there now.
It wouldnt let me make the directories in the GUI and I couldnt remember the command to make them in a terminal. I'm not big on the terminal.
Thanks again both of you they are now both mounted

---

### Post by northern lights on 2008-10-24
Sorted then.

For future reference though, you could have done the same via the GUI also.

The underlying principle is that any user only has write permissions for his /home. This is one of the vital aspects of the *nix security model.

Thus you have do run file operations outside /home as root/superuser (administrator, if you so will). You ran the *mkdir* command with *sudo* cause that gives you temporary admin powers.
Analogously you can start a GUI app as root also. Running ```
gksu nautilus
``` either from the terminal or the "Alt+F2" dialog will result in an instance of nautilus (you filemanager) that will let you modify things outside /home. Just remember to close it right after you've done the necessary operations to prevent accidental screw-ups.

For reference, see [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

