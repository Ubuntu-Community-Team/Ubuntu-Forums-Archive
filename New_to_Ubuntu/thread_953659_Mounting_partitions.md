---
title: "Mounting partitions"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Markstar on 2008-10-20
Hi,
I know there are plenty of threads about this but after going through the first 150 threads and trying to understand "man mount" I must admit I'm still (very) confused.

All I want to do is

a) mount my FAT32 and my NTFS partitions
b) do this whenever Ubuntu starts.

I know they get mounted automatically when I click on them under *Places -> Removable Media* but I would also like to understand the command line commands.

Here is fdisk -l:
```
 fdisk -l
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb406d9f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            3827      121601   946027687+   f  W95 Ext'd (LBA)
/dev/sda5            9572      121601   899880943+   7  HPFS/NTFS
omitting empty partition (5)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f342f33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        3188     5124735    7  HPFS/NTFS
/dev/sdb3   *        3189        5738    20482875   83  Linux
/dev/sdb4            5739       60801   442293547+   f  W95 Ext'd (LBA)
/dev/sdb5            5739        7013    10241406    7  HPFS/NTFS
/dev/sdb6            7014        7651     5124703+  82  Linux swap / Solaris
/dev/sdb7            7652       14026    51207156    7  HPFS/NTFS
/dev/sdb8           14027       58251   355237281    7  HPFS/NTFS
/dev/sdb9           58252       60801    20482843+   b  W95 FAT32

```
and /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=130df278-650e-4b1b-9278-cfb523f94a7c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=5019e5c8-8ba9-4806-abbe-28e2ff7ca5fe none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

My first concern is that I have seen many different variations of the mount command, for example:
*sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/hda1 /media/MyNTFS*

But which one is correct? Which switches do I actually need? What is the minimal command that I can use so that I have full read/write access to my FAT32 and NTFS drives (I guess umask=0777 is for read/write, is that correct?).

And then, of course, do I just copy those commands to /etc/fstab or what do I have to add there?

Thank you in advance!!!

Kind regards
  Markstar

---

### Post by tjwoosta on 2008-10-20
follow this guide

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

first install ntfs-3g (gives you write support for ntfs)

```
sudo apt-get install ntfs-3g
```

make a mountpoint anywhere you want  (i will use /media/Windows as an example)

```
sudo mkdir /media/Windows
```

then edit your fstab

here is an example of what you could add to your fstab in order to mount /dev/sdb1


/dev/sdb1 /media/Windows ntfs-3g defaults,locale=en_US.utf8 0 0


For a list of locales available on your system, run
```
locale -a
```


again eveything i just told you came directly from that link i gave you

---

### Post by Duck2006 on 2008-10-20
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jerome1232 on 2008-10-20
A bare fstab entry that I use, makes the device readable/writable by all users (give those guides a look over they will give you more insight as to what the switches do)
```

UUID=gobly-gook /media/windows ntfs defaults,umask=000 0 2
```

---

### Post by vanadium on 2008-10-20
[quote=jerome1232]UUID=gobly-gook /media/windows ntfs defaults,umask=000 0 2[/quote]
It may not be too "newbee-friendly" to put it like this (this is the "Absolute Beginners Section"). Additionally, this will not allow for writing to the drive.

1) "UUID=gobly-gook" must be replaced by the actual identifier (the "UUID") of the partition you want to mount. An easy way to see the UUID of your partition is using the command

```

sudo blkid

```

This will list all your partitions line by line. Each line also contains the UUID. You can now copy the UUID="..." part from the terminal and paste it in your /etc/fstab instead of "UUID=gobly-gook" in the above template line.

2) Instead of "ntfs", substitute "ntfs-3g" if you need write support. When you specify "ntfs", you are using the standard (read-only) ntfs driver from the kernel. Specifying "ntfs-3g", you are using the read/write ntfs-3g ("third generation") driver

[quote=tjwoosta]
first install ntfs-3g
[/quote]
No need to install ntfs-3g, unless you use Ubuntu versions older than 6.10. ntfs-3g is installed by default.

---

### Post by jerome1232 on 2008-10-20
Actually it does allow write support. That's what my fstab looks like for my ntfs drive and it has read/write support.

I didn't noob it up because I was figuring the op would give those guides a look over they should cover everything :)

---

### Post by Markstar on 2008-10-20
Thank you guys for your replies. :)

@tjwoosta: I read through the guide and found it very informative. I added following lines to fstab:
```
/dev/sda5	/media/1000-1	ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdb8	/media/500-3	ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdb9	/media/MS	vfat	defaults,user,dmask=027,fmask=137 0 0
```While it seems mounting the NTFS partitions works (btw, why do I need to specify a locale?), I get an error when I try to access the FAT32 partition: 
> The folder contents could not be displayed.

You do not have the permission necessary to view the content of "MS".

So what exactly does dmask=027 and fmask=137 mean (and umask)? Is it similar to 777 in web-hosting? 

I would like to be able to read, write (and execute if necessary) files just as I would under Windows, are the entries above appropriate for this (for example, I want to use the FAT32 partition for programming).

@Duck2006: Thank you. I hope I will get it to work either way. 
> **jerome1232 said:**
> A bare fstab entry that I use, makes the device readable/writable by all users (give those guides a look over they will give you more insight as to what the switches do)
```

UUID=gobly-gook /media/windows ntfs defaults,umask=000 0 2
```I'm sorry, I don't really understand this and this is exactly what I meant in the first post: Your line looks very different from the other suggestions and I have no clue what the advantages are of either one of them. :(
But it is true, I did not need to install ntfs-3g...

---

### Post by Michaelg14 on 2008-10-20
I use a program called ntfs-config from the synaptic package manager that will automatically set up your fstab file and allow you to make the partitions read/write at the same time.  It is not without issues but give it a try it won't hurt anything.

---

### Post by kansasnoob on 2008-10-20
Try installing fatsort:

```
sudo apt-get install fatsort
```

It's helped me with external drives.

---

### Post by Markstar on 2008-10-21
> **Michaelg14 said:**
> I use a program called ntfs-config Yes, that's the same tool that was described in the tutorial linked by Duck2006. Because I thought the "manual" way did not work (when I wrote "ls" in the terminal, all entries were green <- what does that mean anyways?), I tried that, but it wrote the exact same line in fstab as I did. Furthermore, it did not allow me to mount my FAT32 partitions, so I uninstalled it again.

I would really appreciate it if someone could explain to me what umask, dmask, fmask mean? And maybe what entries make sense so I can can execute the appropriate files on my FAT32 partition? :(

**Edit:** Oh, and also: How can I mount the partitions but not let them show up on the desktop?

---

### Post by hubiedo on 2008-10-21
thanks vanadim,

your command to get the UUID# worked great to fix my post install partition change but i could not get it to mount automatically. 

thank you
hubert

---

### Post by vanadium on 2008-10-21
[quote=jerome1232]Actually it does allow write support.[/quote]
Thank you for telling this. This behavior might have changed from Ubuntu Edgy.

[quote=Markstar]How can I mount the partitions but not let them show up on the desktop? [/quote]

To not have your volumens show up on the desktop, mount them under /mnt instead of under /media. This way, removable media will still appear on the desktop. To disable displaying drives on the desktop altogether, you chan change a setting in gconfig-editor.

@hubiedo: you will need to provide more info for someone to be able to help.

---

### Post by Markstar on 2008-10-21
> **vanadium said:**
> To not have your volumens show up on the desktop, mount them under /mnt instead of under /media. This way, removable media will still appear on the desktop. To disable displaying drives on the desktop altogether, you chan change a setting in gconfig-editor.Great, thank you! All I need now is to figure out how to properly mount my FAT32 partitions so I can (hopefully) share my Firefox & Thunderbird profile with my other installs. :)

---

### Post by jerome1232 on 2008-10-22
This is a bit late but you asked about umask vs fmask and dmask and I found these descriptions, hopefully it helps. It's from the man page of ntfs-3g. 

Basically umask is fmask and dmask combined, fmask being permissions on files, dmask being permissions on directories. I'm still unsure what other numbers besides 0 do.

```
       umask=value
              Set  the  bitmask of the file and directory permissions that are
              not present. The value is given in octal. The default value is 0
              which means full access to everybody.

       fmask=value
              Set  the   bitmask of the file permissions that are not present.
              The value is given in octal. The default value is 0 which  means
              full access to everybody.

       dmask=value
              Set  the   bitmask  of  the  directory  permissions that are not
              present. The value is given in octal. The  default  value  is  0
              which means full access to everybody.
```

---

### Post by vanadium on 2008-10-22
These umasks are values that are "subtracted" from full permissions. An umask of 000 means permissions will be 777. An umask of 022 means permissions will be 755.

An umask actually consists of four numbers, of which the last three apply to the "usual" permissions. The first value pertains to advanced permission features that i do not understand yet myself ("sticky" attribute, suid, and the likes). Do not worry: if you specify 022, a "leading" 0 is assumed: saying 022 is the same as saying 0022 (and specifying "7" will result in an umask 0007).

---

### Post by Markstar on 2008-10-22
Ahh, thank you. 

@jermome1232: Ahh, yes, I was looking for something like that! So fmask means I set what permissions the files will have, dmask the same for directories?

So instead of saying *fmask=000,dmask=000* I might as well just write *umask=000*? Is that it?

I also have another question concerning mounting:
I have successfully mounted my FAT32 and NTFS partitions now (except [this problem]("http://ubuntuforums.org/showthread.php?p=6011785#post6011785")), but for my Samba shares I would like to mount only certain folders to my samba shared folder. I have already tried this, but it doesn't work:
```
#/dev/sda5/Audio	/home/samba/Audio 	ntfs-3g defaults,locale=en_US.UTF-8 0 0
```
:(

Thank you for your help, I really appreciate it!!!

---

### Post by roadrocket13 on 2008-10-24
try this to auto mount your fat32 partition

```
UUID=[your FAT UUID]   /[your mount point]            vfat    user,rw,noauto      0   0
```

the FAT filesystem doesn't support users, hence the options entry "user,rw"

to find the UUID use;
sudo vol_id -u [block device name]

your device name is the name of the partition on disk like /dev/sda1 would be first partition on the first SATA disk

for example;
```
sudo vol_id -u /dev/sda1
```

will find the UUID of /dev/sda1

---

### Post by steveneddy on 2008-10-31
> **Duck2006 said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

This is where I would have sent you.

Also check out the links in my sig. they may help you with some of your other issues.

---

