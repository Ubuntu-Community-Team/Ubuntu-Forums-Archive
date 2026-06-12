---
title: "unable to mount old windows drive"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by ajsu on 2013-07-06
I am trying to Mount my old windows drive and the mount option is hidden under partition manager. Under File Manager I get the error...      udevil: error 64: unable to determine device fstype - specify with -t

Is there any way to Mount this drive?    :(

---

### Post by BreezyBrooke on 2013-07-06
Usually when you get messages like that, the hard drive has died. If possible, use Ubuntu's Disk Utility called "Disks" in Ubuntu 13.04 to check the drive's SMART data. To get the data, select the drive in the utility and click the cogs icon I believe and click "SMART data and tests" and type here what is says. OK? :) Specifically the warnings and such.

---

### Post by Double.J on 2013-07-06
> **ajsu said:**
> 
Is there any way to Mount this drive?    :(


Hi there, and welcome to the forums!

As Breezy says, it is often not a good sign when ubuntu can't tell you the file system of a windows disk. As it's your first post, I'll assume you're new to ubuntu and keep it simple, so sory for any overlap :)

You can try a manual mount from the command line? just open a terminal, or just press the windows key on your keyboard and type 'terminal'
```
sudo apt-get install[COLOR=#ff0000] ntfs-3g[/COLOR]              #this installs the ntfs driver if you don't already have it
sudo mkdir[COLOR=#008000] /Windows[/COLOR]              #this makes a new directory /Windows -call it what you like
sudo fdisk -l                       #this should show you all connected drives. it's a lowwer case L - for list
sudo mount -t [COLOR=#ff0000]ntfs-3g[/COLOR] /dev/sd[COLOR=#0000ff]X[/COLOR][COLOR=#800080]Y[/COLOR][COLOR=#008000] /Windows[/COLOR]    #this mounts the drive using the ntfs driver. [COLOR=#0000ff]X[/COLOR]&[COLOR=#800080]Y[/COLOR] are found in the list that's just printed
cd[COLOR=#008000] /Windows[/COLOR]                                #this moves you into the windows partition
ls                                                 #if all your windows folders show up it's worked
```


if /dev/sdXY is hard to determin, then for this output from fdisk -l (mine)
```
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
[COLOR=#ee82ee]/dev/sda2          206848    81922047    40857600    7  HPFS/NTFS/exFAT[/COLOR]
/dev/sda3        81922048    82331647      204800   83  Linux
/dev/sda4        82335742   272904191    95284225    5  Extended
/dev/sda5        82335744   194975743    56320000   8e  Linux LVM
/dev/sda6       194977792   195366911      194560   83  Linux
/dev/sda7       195368960   234428415    19529728   83  Linux
/dev/sda8       234430464   268608198    17088867+  83  Linux
/dev/sda9       268609536   272904191     2147328   82  Linux swap / Solaris
```

line two has my C drive on - notice the NTFS at the end, and it is a lot bigger than the boot partition on line 1. so for this I would use /dev/sd[COLOR=#0000ff]a[/COLOR][COLOR=#800080]2[/COLOR]

Best of luck, really hope there isn't any damage done to the drive for you!

---

