---
title: "[SOLVED] Cant write to Hard Drive"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by SILLAT on 2008-09-03
Hi ya'll
i hav 2 hard drives on my pc
i hav a 120 Gb FAT32 hard drive that i use for storing my Media files (music,vids)
i've decided that since i've now fully switched over to ubuntu i dont need my file system to be FAT32 Anymore, so i back up my media files and use Gparted to Format my Drive to EXT file system, after formatting to the EXT3 file system i'm now trying to move back over the files i've backed up back to my 12Gb drive but its not allowing me Write to the drive, if i copy a file i cant paste a file on the drive  ... 
a folder is on the file name "Lost+Found" if i try to open it it says you dont hav permissions to view lost amd found even though i am the admin.
is there a work aroun this issue an  how can i get back to writing to this drive as usual
i really need to add back my files to this hard drive??

---

### Post by aloshbennett on 2008-09-04
The drive might be owned by root.

> gksudo nautilus
will launch nautillus as root. You could perform all your copy paste from here.

Alternatively, you could change the ownership to you
change directory to the drive
> cd /media/disk1

and change ownership to you
> sudo chown `whoami` -R *

---

### Post by SILLAT on 2008-09-04
hey thnx for the tip the gksudo nautilus thing worked but
i tried change the ownership of the drive to me but now i can only paste in a folder name Lost+Found on the drive
i want to create folders on the drive and not only paste in the lost+found

---

### Post by Tatty on 2008-09-04
It sounds like it might be a problem with your fstab.

Can you post the output from ```
cat /etc/fstab
```

---

### Post by aloshbennett on 2008-09-04
My bad! When you go to the drive and did a 'chown *', it changed the ownership of all the files within the drive )in your case lost + found) and not the drive itself.

Its not a nice idea to change the ownership of the folder onto which you are mounting your drive. Its better to give everyone write access on the drive.

> sudo chmod a+w /media/disk
You are giving everyone (a) write access (w) on the drive.

---

### Post by SILLAT on 2008-09-04
this is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=1808f754-d246-463d-8992-6ae116630a58 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=939ff94f-6b20-41cb-bc1b-83f4a3161895 /boot           ext3    relatime        0       2
# /dev/sda3
UUID=80af4618-41b4-4e24-818e-44f70d84b059 /home           ext3    relatime        0       2
# /dev/sda7
UUID=0aab9eff-edd2-460c-b20f-7542b31f0bba /tmp            ext3    relatime        0       2
# /dev/sda6
UUID=82c8ad19-c0cd-4fe7-99f9-5d036e49defb /usr            ext3    relatime        0       2
# /dev/sda8
UUID=5647e493-37c5-442f-8451-101323d2f97e /var            ext3    relatime        0       2
# /dev/sda9
UUID=98c4fe3d-a216-4f32-a56f-d0e0e6365194 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid= 126 devmode=664 0 0

---

### Post by Tatty on 2008-09-04
Have a read of this, [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).

EDIT: I may have misundersood, is your drive an internal or external drive?  I assumed it was internal. Apologies but i also must go now, ill check back to this thread when i can.  Good luck with your problem

---

### Post by SILLAT on 2008-09-04
hey thnx guys
problem solved ... i can now write to my drive

---

### Post by egalvan on 2008-09-04
> **SILLAT said:**
> hey thnx guys
problem solved ... i can now write to my drive

So what was the solution?
That way others can profit from all this work.


Don't leave us hanging! :confused:

---

