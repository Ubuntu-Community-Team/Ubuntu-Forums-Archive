---
title: "[SOLVED] automatically mount windows partition in ubuntu using fstab"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by peterjakey on 2008-08-13
Hi, My Amarok points to my music folder on my windows partition, however the partition doesn't mount automatically on boot and requires a superuser password. Therefore when I startup Amarok doesnt see the music collection and I have to rescan every time. Can I do this easily by editing my fstab file?

---

### Post by dexter.deepak on 2008-08-13
i presume you have an ntfs partition for mounting.
the format is something like :
```
/dev/sdaX	/media/sda6	ntfs-3g		defaults,rw	0	0

```
add this line (after properly editing it) to your /etc/fstab
if this doesnt work, post your /etc/fstab here.

---

### Post by tarps87 on 2008-08-13
There is a program call ntfs-config which should run under kubuntu but I have not tried it, this program will allow you to control ntfs drive using a gui.

If not it can be done with fstab, here is a wiki on it:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you want to mount it in rw mode use ntfs-3g as the file system type
if you want to mount it in ro mode use ntfs file system type

If you get stuck let me know and I'll try and help

---

### Post by prshah on 2008-08-13
> **peterjakey said:**
> Hi, My Amarok points to my music folder on my windows partition, however the partition doesn't mount automatically on boot and requires a superuser password. Can I do this easily by editing my fstab file?

NOTE: You do this at your own risk.

You can add the following lines to your /etc/fstab; Note that you need to:
a) replace /dev/sdx? with your actual partition IDs, 
b) gid with the gid for the plugdev group.
c) ntfs with whichever filesystem you're using (vfat, ntfs)
d) create the blank directories in /media/ as referenced below, with user "root" and group "plugdev"

```

/dev/sdx8 /media/disk1     ntfs    defaults,umask=007,gid=46 0       1
/dev/sdx9 /media/disk2     ntfs    defaults,umask=007,gid=46 0       1

```

_Once again_, I specify the risk is all yours. You can feel free to ignore my advice related to fstab entries, or get it confirmed elsewhere.

---

### Post by peterjakey on 2008-08-13
Thanks for your reply

I added that line to my fstab file but it didn't work so I have copied the contents of my fstab file below (I have also included the output of sudo fdisk -l)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d161bf08-effa-43d8-b345-2941566eba13 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f3731413-c3aa-438c-8d1d-1448be53d226 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdaX	/media/sda6	ntfs-3g		defaults,rw	0	0






sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15935   127997856    7  HPFS/NTFS
/dev/sda2           15936       19457    28290465    5  Extended
/dev/sda5           15936       19306    27077526   83  Linux
/dev/sda6           19307       19457     1212876   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

---

### Post by Elfy on 2008-08-13
I guess you've got a bit confused, 

> /dev/sdaX /media/sda6 ntfs-3g defaults,rw 0 0

you need to specify the number for x in sdaX from your drives in the fdisk -l output nad make sure that there is a folder to mount it in - you've got /media/sda6. Did you actually make that folder as it could get a bit confusing later as that is where you're swap is.

You have 2 windopws partitions - the first one on the 160Gb drive which I assume is where you're win is installed and the 500Gb drive.

Where is your music?

You might feel better doing it with the ntfs-config tool in post 2 - you can search for it in adept. If you want to do it manually you need to confirm where the music is
- sda1 or sdc1 and whether you have made a directory in /media.

---

### Post by peterjakey on 2008-08-13
Windows is installed on the 160gb hdd and the 500gb is a USB external drive (sorry I should have been more clear) I didn't create any directories within the media folder, I just copied the line from the first post into my fstab file without paying much attention to it. The music is in the 'my music' folder within my profile on the windows installation.

---

### Post by Elfy on 2008-08-13
If the usb drive isn't always connected it would cause an error with fstab when you booted buntu. I do think that the best way would be for you to install the tool and use that but to do it manually decide on name to mount as - I'll use music - but you can change as suits

This all assumes that the drive you are trying to get mounted is the 500Gb one.

make the folder ```
sudo mkdir /media/music
```

add line to fstab [kdesu kate /etc/fstab[/code]

Remove the line you put in and add this 

```
# /dev/
UUID= /media/music ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

save and exit - then check it has mounted ok, 

```
sudo mount -a
mount
```

There should be a line in the output of mount corresponding to your new line.

It is important to realise that if you put the line in fstab and the drive isn't available it will cause problems.

**[COLOR="Red"]Edit[/COLOR]** - Actually for that reason change slightly, run 
```
 sudo blkid
``` with the external plugged in, you will get something similar to

> /dev/sda1: UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9

copy the number for sdc1 and put in _directly_ after UUDI= in the fstab line

---

### Post by peterjakey on 2008-08-13
I used the gui tool and it worked perfectly, thanks for the help

---

### Post by Elfy on 2008-08-13
Glad you got there, bear in mind the fstab editing - it is easy enough once you've got it sorted - check out what the tool did to it.

---

