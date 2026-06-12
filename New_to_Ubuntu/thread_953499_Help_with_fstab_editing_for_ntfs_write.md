---
title: "Help with fstab editing for ntfs write"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by gfk on 2008-10-20
I want to have write permissions on a NTFS partition.  I have a feeling that it is because of my unmask settings can somebody give me the right code and maybe give some insight?

Here is my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb8
UUID=d2a3f178-ce47-4107-841e-289cb09a2a40 /               jfs     relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=f21d0595-77b0-4775-95aa-f03abc16b932 /boot           ext3    noatime,nodiratime,data=journal,commit=600   0    2
# /dev/sdb5
UUID=b08c28b3-327d-4742-be6c-569fe001e34f /home           jfs     relatime        0       2
# /dev/sdb7
UUID=2a74c6fb-794c-474b-a248-396cfb22c93d /var            jfs     relatime        0       2
# /dev/sdb3
#UUID=94fa0b3b-0983-4a09-b60e-0980c119fbd0 /mnt/sdb3-LFS   ext3    relatime,commit=600   0   2
# /dev/sda1
UUID=F8F48DC4F48D861A /media/sda1-Documents   ntfs-3g    noatime,nodiratime,auto,exec,nouser,rw,umask=002,utf8   0  1
# /dev/sda2
UUID=64A0E067A0E04162 /media/sda2-Videos      ntfs    noatime,nodiratime,auto,noexec,nouser,ro,umask=002,utf8   0  1
# /dev/sda3
UUID=480E-A4E7 /media/sda3-FAT32-Pagefile     vfat    noatime,nodiratime,noauto,noexec,nouser,ro,utf8,umask=007,gid=46  0  1
# /dev/sda5
UUID=47E2-4F85 /media/sda5-FAT32              vfat    noatime,nodiratime,auto,exec,user,rw,umask=000,utf8   0   0
# /dev/sda6
UUID=082a30fa-ad16-4145-a099-8d4e55835507 none            swap    sw              0       0
/dev/scd0       /media/dvdrom   udf,iso9660 user,noauto,exec,utf8 0       0
```

I just trying it out for sda1 for now.

---

### Post by alpage2 on 2008-10-20
I have a dual boot system with edubuntu on sdb1 and WinXP on sda1, similar to your setup. Edubuntu does not mount the windows partition on bootup, so I take the easy way prior to accessing the partition, I use the thunar file manager to mount it automatically, via the Places menu.

My /etc/fstab is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=17a985ea-a9ed-4b4e-a2d2-b5361df2a2a2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=18D8EEF0D8EECAD8 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=44FD-755D  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=64794d76-c531-4f7d-93eb-da237cbbe22e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Hope that helps.

Alan

---

### Post by hyper_ch on 2008-10-20
have you installed ntfs-3g?

---

### Post by gfk on 2008-10-20
Thanks for the help but still nothing.  I tried changing the unmask to 007 but now I couldn't access the partition.  So I changed it back to 002 which is kinda unique situation because I had to change it to that so I could get it to share on samba.

I think that the drivers for ntfs and ntfs-3g is the same driver.  Anyways I do have the drivers installed.

I do know that unmask is similar with FTP permissions but you do some additions to the codes.  I don't really know to codes so I was hoping somebody to give the right one.

I'm thinking it could be the gid thing?

---

### Post by Paqman on 2008-10-20
> **hyper_ch said:**
> have you installed ntfs-3g?

It's installed by default since Gutsy.

**gfk**: I wouldn't bother editing fstab by hand. Just install ntfs-config and have it do all the work for you.

---

### Post by gfk on 2008-10-20
Yeah but I do like the total control of manual hand editing it's kinda fun.

I now got it working it was the gid, a quick look at the man page of mount tells it is to do with ownership.  So I was wrong in thinking it was to do with unmask.

So I just added ```
gid=46
``` and now I got write permissions.

---

