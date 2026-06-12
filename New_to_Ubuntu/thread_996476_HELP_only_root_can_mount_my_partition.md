---
title: "HELP only root can mount my partition"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by sarc on 2008-11-28
I created an ext3 partition with GPARTED and it's wokring fine except:
- I cannot fin a way to name it: it shows on Nautilus as "50GB Disk"
- Non root users can access it only if root is logged on

How can I name it "D" and have users access it freely (it's my data parition)?  Use fstab?

---

### Post by bodhi.zazen on 2008-11-28
You need an entry in fstab to mount it automatically or allow users to mount the drive.

Set permissions with chown and chmod.

Say the drive is mounted at /media/foo (with the partition mounted)

sudo chown you.users /media/foo
sudo chmod 777 /meida/foo

"you" = your log in name, "users" = the group users.

those  chown / chmod will give full access to everybody.

If you wish you can tighten access.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by sarc on 2008-12-05
I tired to fix FSTAB but it didn't go well!!  On reboot stopped at command line, saying that cannot read disk - then I pressed ctrl-alt-del and the desktopn came on.
I think I got several problems in fstab since I reformated the VFAT on SDA4 to ext3.  I would like to mount the new ext3 on /D and have all Users have read/write privilege.  My UUIDs are wrong... I'm afraid of messing around in case I cannot boot again... can someone tell me the right FSTAB?

us@9000:~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 120 2008-12-06 09:31 .
drwxr-xr-x 6 root root 120 2008-12-06 09:31 ..
lrwxrwxrwx 1 root root  10 2008-12-06 16:52 012ccdc1-d18f-41b8-81ef-1b3a56c4c644 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-12-06 09:31 05B4B59970DDA36F -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-12-06 09:31 2eba5dd8-f88e-41f4-a280-d3d79a78e26e -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-12-06 16:52 8f4be01b-ca06-48e9-977a-61ef277da390 -> ../../sda4


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=012ccdc1-d18f-41b8-81ef-1b3a56c4c644 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
# UUID=47D4-1DA8  /D              ext3    utf8,umask=0111,gid=46 0       1
# /dev/sda3
UUID=28227804-d593-44ba-8559-c1f5471e3d0f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by handydan918 on 2008-12-05
Yer heading for a train wreck, pard. linux DOES NOT use windows naming conventions. Trying to shoe-horn linux into the perverse mess that M/S has made of computer science won't serve you well. Best learn to do it the way it is intended. Ubu is NOT just a free replacement for windows.

---

### Post by psusi on 2008-12-05
You said yourself you have the wrong UUID number.  Well, fix it.  Also you have the line commented out ( starts with a # ) so it has no effect.

---

### Post by bodhi.zazen on 2008-12-05
LOL, be nice, it is stressful to be having these issues ;)

First you can show your partitions by UUID with :

```
sudo blkid
```

To my eye the output is easier to read.

You can also cut and paste the uuid from the terminal output (reducing the potential for typos).

Next stop a minute and look at the syntax of FSTAB

[device] [mount point] [file system] [options] 0 0

So lets walk through /dev/sda4

Device = UUID=8f4be01b-ca06-48e9-977a-61ef277da390
mount point = /media/D
file sytem = auto (or use ntfs-3g if this is a ntfs partition)
options = defaults (add others as needed)

With that information in hand, open fstab for editing

```
gksu gedit /etc/fstab
```

Make the entry for /dev/sda4 look like these lines
Keep in mind , comments start with a octothorpe
# an octothorpe is a hash, pound sign, or #
# Remember, one entery in fstab per partitoin (there can only be 1)

```
#/dev/sda4
UUID=8f4be01b-ca06-48e9-977a-61ef277da390  /media/D  auto defaults 0 0
```

Save and exit gedit.

Now

```
sudo mkdir /media/D
sudo mount /media/D
```

See the fstab link I gave you as well, should start to make more sense.

---

