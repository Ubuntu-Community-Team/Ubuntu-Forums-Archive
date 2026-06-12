---
title: "Auto-mount USB-HD at Startup?!"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by manikinxvx on 2014-02-22
I have selected and turned on every option for mounting my external USB drive which contains my music library and other items. My goal is to have this drive auto-mount at startup, so I can then tell Banshee to also launch when the system does without it encountering errors for the music library files not being present. So far, getting this drive to mount without having to right-click and then "mount volume" has been unsuccessful. I'm just wondering if anyone could please provide some direction and insight. 

Here are the details from Terminal regarding the drive in question [note: I already manually-mounted the volume, thus the reading of the last line with regard to "state=mounted"]:

*-disk
             description: SCSI Disk
             product: 1200BEVExternal
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
             version: 1.02
             serial: E
             size: 111GiB (120GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: guid=7f060435-03f5-492a-80f7-fe9aa4761271
           *-volume
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@8:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/Monkeystone
                version: FAT32
                serial: 98b1-51c6
                size: 111GiB
                capacity: 111GiB
                capabilities: fat initialized
                configuration: FATs=2 filesystem=fat label=Monkeystone mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1001,gid=1001,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted

---

### Post by ajgreeny on 2014-02-22
Although this is an external drive which will automount when you plug it in, it will not do so (not every time anyway) if it is attached at boot.

To make sure it does, and that it mounts at the same folder every time you will need to add a line to /etc/fstab as follows
```
UUID=7f060435-03f5-492a-80f7-fe9aa4761271 /media/data vfat iocharset=utf8,umask=000 0 0
```
or
```
UUID=7f060435-03f5-492a-80f7-fe9aa4761271 /media/data1 vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```
or
```
UUID=7f060435-03f5-492a-80f7-fe9aa4761271 /media/data2 vfat defaults,user,dmask=027,fmask=137 0 0
```
I am not sure which of those three is the most recent and preferred version, but I think it is the last of them.

You can check the UUID of the partition is 7f060435-03f5-492a-80f7-fe9aa4761271 with command ```
sudo blkid -c /dev/null
```
You can also use another mountpoint if you wish, but whatever you choose you will need to make it first with, for example, ```
sudo mkdir /media/data
```

---

### Post by manikinxvx on 2014-02-23
Thank you very much for that info. I have added it to fstab and will test upon next restart. Right now is not a good time for that part of the process.

---

### Post by manikinxvx on 2014-02-23
Well... this nearly worked, in as much as I received a notification from the system that the disk was not yet ready or present at startup. I went into BIOS and changed the boot order; putting USB devices ahead of the system drive. However, that only resulted in a black screen with blinking cursor and not proceeding any further. Is there a way to now tell it it to boot/load after USB devices *are* ready without this problem occurring?

---

### Post by fdrake on 2014-02-23
paste here your fstab 
```
cat /etc/fstab
```
make sure you respected the spacing between each field.

---

### Post by manikinxvx on 2014-02-28
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d00596f0-94f1-4d55-a529-ea9af20d905c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1bf6d08d-1ba2-41ab-9434-ae58bfbf823c none            swap    sw              0       0
# mounting of Monkeystone at  /dev/sdb1
UUID=7f060435-03f5-492a-80f7-fe9aa4761271 /media/data2    vfat    defaults,user,dmask=027,fmask=137              0              0

---

