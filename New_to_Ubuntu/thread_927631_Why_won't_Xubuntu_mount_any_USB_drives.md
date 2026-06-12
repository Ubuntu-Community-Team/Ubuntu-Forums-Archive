---
title: "Why won't Xubuntu mount any USB drives?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-09-23
I have three computers two with Ubuntu hardy and one Xubuntu hardy. Both the Ubuntu computers have no trouble mounting USB drives but the Xubuntu install cannot mount any (of several) USB drives I have tried. 

Attached is a screenshot. Has anybody any idea why this is occurring. 

Cheers,

James.

Edit: by the way, the screenshot reveals something odd. It calls the volume "1G Volume" but in fact, it's a 2G volume.

---

### Post by tangibleorange on 2008-09-23
> **Jimmy9pints said:**
> I have three computers two with Ubuntu hardy and one Xubuntu hardy. Both the Ubuntu computers have no trouble mounting USB drives but the Xubuntu install cannot mount any (of several) USB drives I have tried. 

Attached is a screenshot. Has anybody any idea why this is occurring. 

Cheers,

James.

Edit: by the way, the screenshot reveals something odd. It calls the volume "1G Volume" but in fact, it's a 2G volume.

could you post the output of:

```
cat /etc/fstab
```

---

### Post by Jimmy9pints on 2008-09-23
Thanks for your reply.

The output of 

cat /etc/fstab

is 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9b929288-1a98-4a95-871a-db08da3495e9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b408e1cc-b8e3-40ab-8865-a450807a6776 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by aimpau on 2008-09-23
Never mind my previous post. Check out my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1e77df68-7cd0-4845-9905-d3246a7fe343 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=81109867-3647-42f4-985b-de29b4283397 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
       
/dev/sdb1 /media/windows ntfs nls=utf8,umask=0222 0 0

```

However, I do not get the error you are having.

---

### Post by tangibleorange on 2008-09-23
> **Jimmy9pints said:**
> Thanks for your reply.

The output of 

cat /etc/fstab

is 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9b929288-1a98-4a95-871a-db08da3495e9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b408e1cc-b8e3-40ab-8865-a450807a6776 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

hmm well that file looks fine. after getting the error, could you try the output of:

```
dmesg | tail
```

---

### Post by jimmy the saint on 2008-09-23
It sounds to me like you don't have either gnome-mount (the default ubuntu automounter) or Volman (Thunar's built in mounter) activated.  Try going into the menu>settings>settings manager and (I think it is Desktop).  One of the tabs deals with volume management.  Make sure you have Thunar set to handle volume management.  In this case, volume is storage, not sound!!

---

### Post by Jimmy9pints on 2008-09-25
> **jimmy the saint said:**
> It sounds to me like you don't have either gnome-mount (the default ubuntu automounter) or Volman (Thunar's built in mounter) activated.  Try going into the menu>settings>settings manager and (I think it is Desktop).  One of the tabs deals with volume management.  Make sure you have Thunar set to handle volume management.  In this case, volume is storage, not sound!!

Thanks Jimmy, but I checked firstly in synaptic to make sure volman is installed then went to menu > settings > settings manager and then went into file manager. It's all enabled so I don't think this is the reason.

Is there a way to reinstall Volman perhaps?

---

### Post by Jimmy9pints on 2008-09-25
> hmm well that file looks fine. after getting the error, could you try the output of:

Code:

dmesg | tail

Thanks again

The output of that is:

```
[  141.765928] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  141.765973] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  144.194537] UDF-fs: No partition found (1)
[  144.194946] UDF-fs: No partition found (1)
[  144.195039] UDF-fs: No partition found (1)
[  144.195127] UDF-fs: No partition found (1)
[  144.484593] ISOFS: Unable to identify CD-ROM format.
[  144.485179] ISOFS: Unable to identify CD-ROM format.
[  144.572416] ISOFS: Unable to identify CD-ROM format.
[  144.581534] ISOFS: Unable to identify CD-ROM format.

```

By the way, the system is "Unable to identify CD-ROM format" because the CD drive is buggered after being dropped. This doesn't apply to the usb ports though because they work in windows.

James.

---

### Post by tangibleorange on 2008-09-26
try manually mounting the drive:

```
sudo mkdir /media/USB
sudo mount -t /dev/sdb1 /media/USB
```

---

