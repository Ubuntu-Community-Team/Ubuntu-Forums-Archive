---
title: "Unable to write to external hard drive"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Binary.tobis on 2008-06-16
I have a 1TB NTSC hard drive that I use on my main computer. I'm trying to use it with my xubuntu install but for some reason I can't write files to the drive. Is there some permissions I should set? Thanks in advance!

---

### Post by tamoneya on 2008-06-16
first of all it is more likely a NTFS drive instead of NTSC.  NTSC is a video format.  Post the output of this command in terminal and we can show you how to mount it to your filesystem:```
sudo fdisk -l
```

---

### Post by Binary.tobis on 2008-06-16
Sorry, I knew that I just had a brain fart. -_-

```
Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe21ae21a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2345    18836181   83  Linux
/dev/hda2            2346        2432      698827+   5  Extended
/dev/hda5            2346        2432      698796   82  Linux swap / Solaris

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27544c21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    7  HPFS/NTFS

```

---

### Post by tamoneya on 2008-06-16
```
sudo mkdir /media/external
sudo mount -t ntfs /dev/sda1 /media/external
```
Now look in /media/external and you should see your files.

---

### Post by ChameleonDave on 2008-06-16
If you want it automatically mounted, you'll need it to be mentioned in your fstab file.  Post the output of this:

```

cat /etc/fstab

```

---

### Post by Binary.tobis on 2008-06-16
The first thing said it wouldn't work because the device was busy. Though I could still find them in media/device, finding the files wasn't the problem it was writing to the drive that was giving me trouble.

The entry into the terminal gave ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8e525607-248d-495f-872a-aee3b6e83423 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=2864b11c-f455-42f0-b83d-b6dc4114227a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by ChameleonDave on 2008-06-16
OK, so it's not in your fstab file.  I'm assuming your drive is normally connected, so you want to it mount all the time.

Open the file like this:

```
sudo *nano* /etc/fstab
```

You may replace "*nano*" with your favourite text editor (*gedit*, *kwrite*, *kate*, *mousepad*, *vim*...)

Add the following line:

```

/dev/sda1  /media/external  ntfs-3g  defaults,auto,rw,umask=007   0   1

```

If you don't want it to be auto-mounted, change "auto" to "noauto".  That will be better if you often disconnect it.

(In fact, I'm not sure, but there might be an error at boot time if fstab tries to auto-mount something that is not physically connected.)


Since we're working with NTFS, make sure you have all the software that you might need:

```

sudo apt-get install ntfs-3g ntfsprogs

```

---

### Post by Binary.tobis on 2008-06-16
That worked like a charm! You guys are miracle workers. :)

---

### Post by ChameleonDave on 2008-06-16
> **Binary.tobis said:**
> That worked like a charm! You guys are miracle workers. :)

Great!

Another thing though...

I told you to define the drive as "/dev/sda1" in the fstab file, but there is a better way to do it.

Type this into the terminal:

```

ls -l /dev/disk/*

```

It will give you a load of info about your drives.

You can also use this:

```

ls -l /dev/disk/* | grep sda1

```

...which does the same thing but prunes out everything except the info on sda1.

Look at that info, and see if a label is defined for the drive.  My one, for example, is labelled "Files".  This means that instead of "/dev/sda1", I can put "LABEL=Files" in my fstab file.

If there is no label, then use the UUID instead.  In my case, that means that I can put "UUID=b1d5011b-f544-4c19-b895-e8ba52f4aa54" instead of a label or a drive number.

The advantage of labels and UUIDs over drive numbers is that they don't change when you add additional drives.  You'll see that your current fstab file mainly identifies partitions by means of UUIDs.

---

### Post by Binary.tobis on 2008-06-17
Ok, I tried to mount my hard drive again but this time it isn't coming up. It displays an error saying "only root can do that". Can I stick a gksudo somewhere in that "/dev/sda1 /media/external ntfs-3g defaults,auto,rw,umask=007 0       1"?

---

### Post by ChameleonDave on 2008-06-17
> **Binary.tobis said:**
> Ok, I tried to mount my hard drive again but this time it isn't coming up. It displays an error saying "only root can do that". Can I stick a gksudo somewhere in that "/dev/sda1 /media/external ntfs-3g defaults,auto,rw,umask=007 0       1"?

There are two things here.  One is manually mounting with the "mount" command, and the other thing is having it mounted at boot time by /etc/fstab.

For the "mount" command, you always need to put "sudo" in front of it.  For /etc/fstab, no such thing is possible or necessary, because the whole boot process is a "root" thing anyway.

Once something is declared in /etc/fstab and for some reason you need to mount it manually (because it was set to "noauto" or because you have unmounted it manually) you no longer need to enter such a long command.  You can refer to the partition by either its device name or its mount point.  In other words, either "sudo mount /dev/sda1" or "sudo mount /media/external" will suffice.

* * *

If that doesn't work, then it may be that the drive is not being recognised as "/dev/sda1".  Since this is an external drive, I'd not be surprised.  As I said before, adding and removing drives can result in their drive numbers changing.

Did you follow my advice in my previous post about using labels or UUIDs to identify the drive?  Is the drive still recognised as "sda1"?  You can use the commands I provided previously to find out.

---

