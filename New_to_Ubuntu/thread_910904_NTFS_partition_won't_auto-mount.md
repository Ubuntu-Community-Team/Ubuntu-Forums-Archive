---
title: "NTFS partition won't auto-mount"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by EricJD on 2008-09-05
I just installed Ubuntu 8.04, I'm running a dual boot setup with Windows Vista. I used the automatic partition resizer when I set up Ubuntu, with 225.4 GB for Vista and 20-some for Ubuntu. I want to be able to access Vista's NTFS partition from within Ubuntu. "225.4 GB Media" shows up in my places list and in Computer, and it seemed to mount properly when I double-clicked it. But when I restart, it unmounts. What I want to do is make it so this automatically mounts as "Windows" when I boot Ubuntu. I tried changing the mount point using the properties menu, but now it won't mount at all. A little help, please? :)

[http://www.imgdash.com/uploads/187a0_error.png](http://www.imgdash.com/uploads/187a0_error.png)

---

### Post by Corrupt3d on 2008-09-05
The graphical method always unmounts on startup,
Your normally supposed to edit the fstab to get it to mount permanently.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

edit your fstab & try,
<name of windows dev> <place where you want to mount it> ntfs defaults 0 0

you can find out the name of the devices by running gparted or by typing, "sudo fdisk -l"

---

### Post by abhishek.malhotra35 on 2008-09-05
For mounting automatically, add an entry in fstab. The error you have attached might be because windows wasn't properly shutdown. If same problem arises, you can forcefully mount the partition using mount command and using forcefully option.

---

### Post by Crafty Kisses on 2008-09-05
You can try manually mounting it:

First let’s figure out where our NTFS partition is hiding. I’m going to assume that you’ve got an NTFS partition, an EXT3 partition and perhaps a FAT32 partition laying about. Open up a terminal session and type the following:
```
   sudo fdisk -l
```
You’re looking for the NTFS partition, the output should be something like this:
```
   Device Boot Start End Blocks Id System
    /dev/sda1 * 1 2550 20480008+ 7 HPFS/NTFS
    /dev/sda2 2550 7493 39707451+ f W95 Ext’d (LBA)
    /dev/sda3 7494 9729 17960670 83 Linux
    /dev/sda5 2550 7394 38911288+ b W95 FAT32
    /dev/sda6 7395 7493 795186 82 Linux swap / Sabayon
```

It’s **/dev/sda1** that you're interested in, so find it and write it down.

So let's finally get this working, try installing these packages:
```

    sudo apt-get install libfuse2 fuse-utils libntfs8 ntfsprogs
```

Now let’s add fuse to the list of stuff that our kernel will load:

```
    echo fuse | sudo tee -a /etc/modules
```

Now let’s add a group which we’ll use to control who can or can’t get access to the NTFS partition.

```
    sudo addgroup ntfs
```

After that's done you should get some GID output (Group ID).

Now we're gonna make a mount point for Windows:
```

    sudo mkdir /media/windows

    sudo cp /etc/fstab /etc/fstab.bak

    gksudo gedit /etc/fstab
```

Now that you’ve got the fstab file backed up and open in gedit, let’s add the following line to the bottom of it.

   ```
 /dev/hda1 /media/windows ntfs-fuse auto,gid=1002,umask=0002 0 0
```

Now, let’s add your user to the NTFS group:

  ```
  sudo adduser user ntfs
```

Now reboot and you should be good.

---

### Post by EricJD on 2008-09-05
Hmm...

After a bit of tinkering around, I still can't get it to automatically mount on startup. My fstab file doesn't make much sense, really.. Here is what it contains (plus my added line)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8378e074-fb2d-407c-9e0c-0f633f4be8b3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e124533f-3109-42a0-a898-77a46981abab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 	/media/Windows	fuseblk rw,user 0 0
```

---

### Post by bumanie on 2008-09-05
THe easiest way to to > sudo apt-get install ntfs-3g followed by > sudo apt-get install ntfs-configThen go to Applications --> System Tools --> NTFS configuration tool, fill out the GUI window that appears and /etc/fstab will automatically be edited to automount windows.

---

### Post by EricJD on 2008-09-05
I tried both methods by Codename and bumanie.. Codename's didn't work, it just told me I was not privileged to mount the volume. bumanie's method worked, and it automounts on startup, but it appears on my desktop as "225.4 GB Media" and I can't rename it. How would I go about doing that?

---

### Post by Crafty Kisses on 2008-09-05
> **EricJD said:**
> I tried both methods by Codename and bumanie.. Codename's didn't work, it just told me I was not privileged to mount the volume. bumanie's method worked, and it automounts on startup, but it appears on my desktop as "225.4 GB Media" and I can't rename it. How would I go about doing that?

Did you **sudo **while doing the commands?

---

### Post by Bucky Ball on 2008-09-05
[https://help.ubuntu.com/community/RenameUSBDrive#NTFS](https://help.ubuntu.com/community/RenameUSBDrive#NTFS)

That should cover the rename issue. :)

---

### Post by EricJD on 2008-09-05
Well, it seems that Ubuntu has killed my NTFS partition. I can't mount it at all now, and Vista bluescreens when I attempt to boot it.

---

### Post by Bucky Ball on 2008-09-05
Can you boot to Ubuntu? If so, open a terminal and type:

sudo fdisk -l

The drive itself was working okay before all this, yea? Windoze blue screen are not usually a result of Ubuntu tweaking.

---

