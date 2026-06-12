---
title: "rename a partition"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by kneewax on 2008-07-07
Hi Guys,

This weekend I reinstalled Hardy, after a rather catastrophic mishap!  I was able to backup all my settings and data, so no major issues there except that on reinstall Hardy has given the name 'disk' to my data (FAT32) partition.  A number of my restored programs now won't run properly because they are looking for the old data name of 'sda2'.  I have looked, but can find no obvious way of altering this.  Can anyone help?

Cheers

---

### Post by DezSP on 2008-07-07
Run gksudo gedit /etc/fstab

You need to find the right entry, it'll probably look something like this:

# /dev/sda2
UUID=F6B42B8EB42B5103 /media/disk  ntfs    defaults,umask=007,gid=46 0

You then need to replace /media/disk with the correct directory. Then run:

sudo mkdir /media/sda2 

Or similar, to make the folder. Then reboot and it should be solved. :)

---

### Post by derred on 2008-07-07
> **kneewax said:**
> Hi Guys,

This weekend I reinstalled Hardy, after a rather catastrophic mishap!  I was able to backup all my settings and data, so no major issues there except that on reinstall Hardy has given the name 'disk' to my data (FAT32) partition.  A number of my restored programs now won't run properly because they are looking for the old data name of 'sda2'.  I have looked, but can find no obvious way of altering this.  Can anyone help?

Cheers

As far as I can figure out you're mounting the partition as /media/disk when in fact you wanted to mount it somewhere else (don't know where maybe /media/sda2 but I'm not sure)

Your best bet is to edit the /etc/fstab file. However that file is vital for the system to function properly so if you mess it up ubuntu will not work. Before you do anything to it you should copy the file to a safe location so that if you have to you can restore it (boot with the live cd and replace the corupt file with the backup)

I think you will have to the file something like this
# /dev/sda2
UUID=*strangenumbersandletters* */new/place/for/sda2*           vfat...

to

# /dev/sda2
UUID=*strangenumbersandletters* */old/place/for/sda2*           vfat...

 
Info about the fstab file can be found here
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

More info, including the content of the fstab file will be usefull if you post it here ;)

---

### Post by kneewax on 2008-07-07
OK folks, I editted the fstab file, but the disk still mounts as 'disk'.

here is my current fstab file:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=afc94c6e-da2d-4320-807a-592685c1f0d3 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=69BA-7802  /media/sda2      vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=dd1ec119-bbd4-4c8e-a4cd-8a2d8de86464 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

any ideas what I am doing wrong. I followed instructions above and I now have a folder called 'sda2' in the /media/ folder, but it is just a folder not this partition.

---

### Post by bumanie on 2008-07-07
According to [this article]("https://help.ubuntu.com/community/RenameUSBDrive"), you need to install e2label to relabel ext2/3 partitions. The article is specific to usb drives, but should work for hard drives.

---

### Post by kneewax on 2008-07-07
[remove]

inane comment

[/removed]

---

### Post by sayakb on 2008-07-07
> **kneewax said:**
> OK folks, I editted the fstab file, but the disk still mounts as 'disk'.

here is my current fstab file:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=afc94c6e-da2d-4320-807a-592685c1f0d3 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=69BA-7802  /media/sda2      vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=dd1ec119-bbd4-4c8e-a4cd-8a2d8de86464 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```any ideas what I am doing wrong. I followed instructions above and I now have a folder called 'sda2' in the /media/ folder, but it is just a folder not this partition.

Suppose you want the label as MyDisk
So first at a terminal:
```
sudo mkdir /media/MyDisk
sudo gedit /etc/fstab
```
And change the string **/media/sda2 **to **/media/MyDisk**
Save the file and reboot.

---

### Post by DezSP on 2008-07-07
Have you restarted? /etc/fstab is only read at boot-time.

---

### Post by kneewax on 2008-07-07
yep!

---

### Post by JohnLM_the_Ghost on 2008-07-07
Lame question, but anyways...

It might show up as 'disk' but mounted on /media/sda2
Have you checked that?

The Partiton Label has nothing to do with mount-point if /etc/fstab is correct

EDIT:
btw, Did you separate entry /media/sda2 with tabs or spaces? I believe fstab expects tabs.

---

### Post by kneewax on 2008-07-07
thanks - I checked that - the mount point is def. still /media/disk and fstab is seperated by tabs.

at a real loss on this.  Following above instructions creaed a folder in/media/ called 'sda2' but it was exactly that a folder on the first partition.

Not sure it is relevant but if I right-click > properties on the second partition (mounted as 'disk') in the permissions tab it says the following: "The permissions of 'disk' could not be determined"

I am getting quite unstuck  with this - any further help much appreciated.

Thanx

---

### Post by JohnLM_the_Ghost on 2008-07-07
If for some reason UUID had changed,
try replacing UUID with device like

```
# /dev/sda2
UUID=69BA-7802  /media/sda2      vfat    utf8,umask=007,gid=46 0       1

```
with this

```
# /dev/sda2
**/dev/sda2**  /media/sda2      vfat    utf8,umask=007,gid=46 0       1

```

There is one caveat though... If you ever swap/change hard disks the device path might change... so mount would go out of order... again.

---

### Post by kneewax on 2008-07-07
> **JohnLM_the_Ghost said:**
> If for some reason UUID had changed,
try replacing UUID with device like

```
# /dev/sda2
UUID=69BA-7802  /media/sda2      vfat    utf8,umask=007,gid=46 0       1

```
with this

```
# /dev/sda2
**/dev/sda2**  /media/sda2      vfat    utf8,umask=007,gid=46 0       1

```

.

Hi there,  Thanks I tried that, and after restart the volume said I no longer had permission to mount it.  So I have reverted to the fstab posted earlier.

Is there a way of simply resetting the mount point without messing about in the fstab file?  I have backups so although it'd be  a pain I could delete the partition and reset it, but as I remember gParted assigns the mount point automatically if you do this, is there a way to tell it to mount to point /media/sda2

Ta

---

