---
title: "set up automount"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by killerbyteeire on 2008-11-08
Hello

Please can somebody tell me is it possible to use the gui to set up internal disk file systems to automount in Xubuntu? I have fat32 and extension 3 internal disk file systems. I know some other distros automount at startup if not gnome ubuntu and kubuntu also.

Thank you very much
Brendan

---

### Post by taurus on 2008-11-09
You can add an entry to mount a drive/partition if you wish.  You just need to know which partition and filesystem you want to mount.

Just type this command in a terminal and it will show you the layout of your drive(s).

```
sudo fdisk -l
```

---

### Post by epitaph on 2008-11-09
You could try using pysdm to setup fstab and I know many swear by it. Personally, it barely worked intelligently enough when I used it on my laptop and I found just editing fstab easier and more reliable.

So, you can try using pysdm:

```
sudo apt-get install pysdm
```

Then go to System > Administration > Startup > Storage Device Manager to modify the disk setup.

Or, you can opt to edit /etc/fstab, but you will first want to do an fdisk to get some information.

```
sudo fdisk -l
gksudo gedit /etc/fstab
```

As an example, I want to mount my 500GB NTFS drive every time I start my system.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0926aacc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS
```

That's the relevant section of the fdisk that applies to that hard disk.

So, I edit my fstab file to have another line that says:

```
/dev/sda1                                  /media/darkside ntfs         nls=iso8859-1,umask=000     0  0 
```

The device is /dev/sda1 and I am mounting it to /media/darkside as an NTFS drive. Depending on the type of file system the partition has, you may have to use some different flags. If you search for more threads that discuss editing fstab you will find a lot of good references.

---

### Post by killerbyteeire on 2008-11-09
Epitaph I have tried pydsm already. I forgot to say that. It seems to be a good package but it does not work fully correctly on my computer and allow me to mount all my file systems. Thank you for the suggestion.

Thanks Taurus

I want to know is there a method of setting up automatic mounting using the gui in xubuntu. Browsing internal disk file systems is a capability new users would expect without having to do manual editing of configuration files. I know other distros have it and i think it is possible to use the gui in kubuntu to mount internal disk file systems. Does anybody know if it is possible with the gui in xubuntu?

---

### Post by taurus on 2008-11-09
What filesystem is that partition (drive)?  If it's ntfs, then install ntfs-config and use the GUI to configure it then.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by killerbyteeire on 2008-11-09
Taurus I have many file systems i want to mount. They are fat32 and extension 3.

This is from /Thunar-0.9.0/docs/README.volumes in the latest Thunar package.

Thunar is able to display mounted and mountable volumes in the shortcuts pane, and allows the user to mount or eject/unmount these volumes from the context menu. In addition, if the user double-clicks a volume in the shortcuts pane (or requests to open the shortcut in a new window), Thunar will first try to mount the volume if it's not already mounted.

There are no mountable volumes showing in my shortcuts pane. It is a clean fresh install done yesterday. Please can somebody tell me how to get mountable volumes to appear in the shortcuts pane?

Thank you very much
Brendan

---

### Post by taurus on 2008-11-09
Then why not just post the output of this command and I will show you how to add entries for those partitions in /etc/fstab if you tell me where you want to mount them?

```
sudo fdisk -l
```

Otherwise, we are just going around in a circle here.

---

### Post by killerbyteeire on 2008-11-09
ok ill do that when im home this evening. thanks very much taurus.

---

### Post by killerbyteeire on 2008-11-09
```


killerbyte@brendan:~$ sudo fdisk -l
[sudo] password for killerbyte: 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2af39065

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2295    18434556    5  Extended
/dev/sda2   *        2296        2614     2562367+   c  W95 FAT32 (LBA)
/dev/sda3            2615        3006     3148740    c  W95 FAT32 (LBA)
/dev/sda4            3007       10011    56267662+   c  W95 FAT32 (LBA)
/dev/sda5               1         893     7172959+   b  W95 FAT32
/dev/sda6            1531        1657     1020096   82  Linux swap / Solaris
/dev/sda7             894        1530     5116671   83  Linux
/dev/sda8            1658        2295     5124703+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd21bd21b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2611    20972826   83  Linux
/dev/sdb2   *        2612        5222    20972857+   c  W95 FAT32 (LBA)
/dev/sdb3            5223        6497    10241437+  83  Linux
/dev/sdb4            6498        9729    25961040    f  W95 Ext'd (LBA)
/dev/sdb5            6498        9598    24908751    b  W95 FAT32
/dev/sdb6            9599        9729     1052226   82  Linux swap / Solaris

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x042af29a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc3               1       36483   293049666    c  W95 FAT32 (LBA)
killerbyte@brendan:~$ 


```






i dont mind where they are mounted. i suppose mnt or media would be the best place to mount them. i would like to mount all of my file systems. this is the same text but not needed anymore: [http://pastebin.com/m1e1b906](http://pastebin.com/m1e1b906).

thank you very much taurus

---

### Post by cardinals_fan on 2008-11-09
@killerbyteeire: surround the output in [code] tags, or highlight it and click the little # sign in the upper right of the forum reply box.

Which drives in that list do you want to mount?

---

### Post by killerbyteeire on 2008-11-10
cardinals fan i would like to mount all of my file systems

---

### Post by bumanie on 2008-11-10
post the output of > cat/etc/fstab

---

### Post by killerbyteeire on 2008-11-10
```
killerbyte@brendan:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda8
UUID=0465eec3-da5f-4d6b-8468-66535a346e0c  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda6
UUID=e9c4b699-3b86-40cc-b48e-4dd04a2de95f  none           swap         sw                          0  0  
# /dev/sdb6
UUID=7c2ff1bb-92e7-4fed-af5a-e4fb3c8fde73  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb5                                  /media/sdb5    vfat         defaults                    0  0  
/dev/sdc3                                  /media/sdc3    vfat         defaults                    0  0  
/dev/sda3                                  /media/sda3    vfat         defaults                    0  0  
/dev/sda4                                  /media/sda4    vfat         defaults                    0  0  
/dev/sda5                                  /media/sda5    vfat         defaults                    0  0  
/dev/sda6                                  /media/sda6    swap         defaults                    0  0  
/dev/sda7                                  /media/sda7    ext3         defaults                    0  0  
/dev/sda8                                  /media/sda8    ext3         defaults                    0  0  
/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0  
/dev/sdb2                                  /media/sdb2    vfat         defaults                    0  0  
/dev/sdb3                                  /media/sdb3    ext3         defaults                    0  0  
/dev/sdb6                                  /media/sdb6    swap         defaults                    0  0  
killerbyte@brendan:~$ 

```

---

### Post by abrussak on 2008-11-10
Have you installed this package: thunar-volman?
```

sudo apt-get install thunar-volman

```

[http://packages.ubuntu.com/intrepid/thunar-volman](http://packages.ubuntu.com/intrepid/thunar-volman)
Or
[http://packages.ubuntu.com/hardy/thunar-volman](http://packages.ubuntu.com/hardy/thunar-volman)

It just sounds like you don't have the package installed. I think that's what my roomie said when I was trying out XFCE....

---

### Post by killerbyteeire on 2008-11-10
killerbyte@brendan:~$ sudo apt-get install thunar-volman
Reading package lists... Done
Building dependency tree        
Reading state information... Done
thunar-volman is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
killerbyte@brendan:~$

---

### Post by abrussak on 2008-11-10
Hmmm...I don't know for sure, you could try running it, but from the sounds of it....it should be running already through Thunar. I'm not at home, so I cannot ask my roommate.

---

### Post by killerbyteeire on 2008-11-10
im pretty sure it is running but i only see settings to do with external storage devices rather than internal devices.

---

### Post by cardinals_fan on 2008-11-10
They should be mounted, based on that fstab... :confused:

---

### Post by killerbyteeire on 2008-11-11
sda1 and sdb4 are not mounted. Do these file systems actually contain files and can they be mounted? sda1 is 'Extended' and sdb4 is 'W95 Ext'd (LBA)'. Is there a difference?  There are other missing ones but ill add them to fstab myself.

thanks
brendan

---

### Post by bumanie on 2008-11-11
sda1 won't mount as such as it the extended partition - it is technically a primary partition, but is being used as a 'container' for all the other filesystems on sda. The same situation is occurring with sdb4 - it is an extended partition and contains partitions sdb5 and sdb6. All your available filesystems are mounted except for sdb5, which you can manually add. sda1 and sdb4 are both the 'extended partition box' containing other filesystems, they won't show up in fstab, as they don't have a filesystem - being used as exteneded partitions they are merely containers.

---

### Post by killerbyteeire on 2008-11-11
its actually sda4 that isnt mounted but i think i can mount that myself. i think ill talk to the thunar community about their management of internal disk file systems. I do think more can be done graphically. thanks very much everybody for your help

---

### Post by bumanie on 2008-11-11
According to /etc/fstab sda4 is mounted on /media/sda4 with a FAT32 (vfat) filesystem.

---

### Post by killerbyteeire on 2008-11-11
sorry sda2 :) we all make mistakes. im very tired. sdb5 is at the top of the fstab list and is mounted too

---

