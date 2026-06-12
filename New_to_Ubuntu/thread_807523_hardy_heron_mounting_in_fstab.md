---
title: "hardy heron mounting in fstab"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by xeth on 2008-05-25
when i was still  using gutsy gibbon i mounted my secondary HD by fstab. but when i upgraded to hardy heron it dones't work anymore. everytime i reboot it doesn't automount anymore.

my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=770bd2ef-b7f1-487c-9c18-11d395758c3e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d28e5d77-8e19-43b1-a7f8-2cf0f59cf242 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1	/media/1	ext3	defaults 0 0

the last one which is hdb1 is my secondary drive
now, everytime i reboot, i have to click the drive to mount it.
nothing really changed in the fstab so i don't know what's wrong

thanks

---

### Post by wolfen69 on 2008-05-25
> **xeth said:**
> 
/dev/hdb1	/media/1	ext3	**defaults** 0 0



you could change **defaults** to **user,auto,rw,exec**

and of course, feel free to change rw(read-write) to ro(read only)

remember to make a new line underneath the last line with nothing in it before saving.

then reboot for changes to take effect.

---

### Post by xeth on 2008-05-25
so i should leave the 0 0?
what does it mean by the way?

---

### Post by wolfen69 on 2008-05-25
yes, leave the 0 0

---

### Post by xeth on 2008-05-28
still won't mount at boot.

anymore ideas?

---

### Post by DoritosBR on 2008-05-28
> **xeth said:**
> still won't mount at boot.

anymore ideas?

what's the output of "mount -a"

---

### Post by xeth on 2008-05-29
ok i got it

when i upgraded to hardy heron. ubuntu renamed the media from hdb to sdb. i dunno why it did that

---

### Post by logos34 on 2008-05-29
maybe it's now being seen by Hardy as sdb1.  Mine changed

sudo fdisk -l

or try using the uuid like the others.  Find with:

blkid 

or 

ls -l /dev/disk/by-uuid

---

