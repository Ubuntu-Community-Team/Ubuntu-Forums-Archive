---
title: "fstab didn't works during boot"
date: 2018-12-27
forum: New to Ubuntu
---

### Post by sed_faster on 2018-12-27
Hello folks,

I have this system:
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial
$ uname -a
Linux ubuntu 4.4.0-131-generic #157-Ubuntu SMP Thu Jul 12 15:49:15 UTC 2018 i686 i686 i686 GNU/Linux

```

And I intend configure fstab to mount two hard drive during boot time. For this I configured the /etc/fstab this way:
```

UUID=various_numbers       /home/user/tg1     ext4    auto,user,rw    0       0 

UUID=various_numbers       /home/user/tg2     ext4    auto,user,rw    0       0

```

When I tried run command "sudo mount -a" never happen. After I reboot all system this units didn't mounted in system. If I execute this command "sudo mount /dev/sdc1 /home/user/tg1" I can mount the hard drive in this folder. However I thought the problem was permission but I don't know much about permission to know if the source of the problem comes from.
```

drwxr-xr-x 4 user user 4096 Dec 25 02:42 tg1
drwxrwxr-x 2 user user 4096 Dec 25 02:33 tg2

```

Thanks

---

### Post by TheFu on 2018-12-28
The directories must exist.
/home/user/tg1 , /home/user/tg2

File systems must exist on the device you are attempting to mount. Each must be ext4 by the settings.  Is that actually true or is the file system that the disks arrived with from the vendor being used?  **lsblk -fs ** will show file systems, devices, UUIDs, and LABELs.

I've never used those options in the fstab. Have you tried to make auto,user,rw into "defaults"?
Is the storage permanent or temporary?    For temporary storage, I prefer to use LABEL= rather than UUID=

The fstab manpage says this:```

       The fourth field (fs_mntops).
              This  field  describes  the  mount  options  associated with the
              filesystem.

              It is formatted as a comma-separated list of options.   It  con-
              tains at least the type of mount (ro or rw), plus any additional
              options appropriate to the filesystem  type  (including  perfor-
              mance-tuning options).  For details, see mount(8) or swapon(8).

              Basic filesystem-independent options are:

              defaults
                     use  default  options: rw, suid, dev, exec, auto, nouser,
                     and async.

              noauto do not mount when "mount -a"  is  given  (e.g.,  at  boot
                     time)

              user   allow a user to mount
...
       The sixth field (fs_passno).
              This field is used by fsck(8) to determine the  order  in  which
              filesystem  checks  are  done at boot time.  The root filesystem
              should be specified with a fs_passno of  1.   Other  filesystems
              should  have  a fs_passno of 2.  Filesystems within a drive will
              be checked sequentially, but  filesystems  on  different  drives
              will  be  checked at the same time to utilize parallelism availâ
              able in the hardware.  Defaults to  zero  (don't  fsck)  if  not
              present.

```

---

### Post by sed_faster on 2018-12-28
This is my result of the command lsblk -fs
```

$ lsblk -fs
NAME       FSTYPE LABEL    UUID                                 MOUNTPOINT
fd0                                                             
sda1       ext4   systemSO string_number /
`-sda                                                           
sda2                                                            
`-sda                                                           
sdb1       ext4   1T1   string_number /home/user/d1
`-sdb                                                           
sdc1       ext4   1T2   string_number /home/user/d2
`-sdc                                                           
cryptswap1 swap            string_number [SWAP]
`-sda5     swap            string_number 

```

Yes, the path /home/user/d1 exist. I can mount this directory manually, but through fstab, ver doing "sudo mount -a" I can't mount anything!
Thanks

Since I can't mount this hard drives through fstab file I mounted from script:
```

#!/bin/bash
sudo mount /dev/sdb1 t1/
sudo mount /dev/sdc1 t2/

```

But frequency the hard drives disconnected. Right now I am transferred through scp software amount data through network. The first package (almost 50GB) finished and I started the second sending. But when I access the system, through ssh protocol, I see which I send all files to /home/user/t2/ right but the hard drive wasn't longer mounted on the system. I need move all data to another directory, run script which I use to mount all hard drive and move again all data to inside hard drive.

What goes wrong with my system? I never see this behavior.
Thanks

---

### Post by zorlax on 2018-12-28
How are the hard-drives connected, USB/SATA?

---

### Post by Impavidus on 2018-12-29
> **sed_faster said:**
> 
And I intend configure fstab to mount two hard drive during boot time. For this I configured the /etc/fstab this way:
```

UUID=various_numbers       /home/user/tg1     ext4    auto,user,rw    0       0 

UUID=various_numbers       /home/user/tg2     ext4    auto,user,rw    0       0

```

When I tried run command "sudo mount -a" never happen. After I reboot all system this units didn't mounted in system.

You use the auto option. This means mount -a, which is executed automatically during boot, will attempt to mount the partitions – good if they are internal drives and you always want them available, bad if they are external as you'll get an error message at boot if not present (unless you add the nofail option). You also use the user option, which allows non-root users to mount or unmount these partitions. That's nice if the the drives are external, but not really needed if internal, as it should already be mounted at boot (so no need to mount later) and for internal drives there should rarely be a reason to unmount before shutdown. You don't use the nofail option, so whenever mount -a fails to mount these partitions, you should get a hard to miss error message. You don't see this error message (or at least, haven't told us about it), which suggests that mount -a doesn't see these lines at all.
Show us```
cat /etc/fstab
sudo mount -a
mount | grep home
```Maybe there's a subtle error somewhere.

 If the partitions automatically unmount shortly after mounting, that's something different. Check the log files.

---

### Post by sed_faster on 2018-12-29
> 
If the partitions automatically unmount shortly after mounting, that's something different. Check the log files.

How can I check log files?
Thanks

My two disk is internal and I repeat all I said in this post:
```

$ uname -a
Linux ubuntu 4.4.0-131-generic #157-Ubuntu SMP Thu Jul 12 15:49:15 UTC 2018 i686 i686 i686 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial

```

My hard disk **internal** is:
```

$ sudo fdisk -l
[sudo] password for user: 
Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa4atrca7

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 136718335 136716288 65.2G 83 Linux
/dev/sda2       136720382 156301311  19580930  9.3G  5 Extended
/dev/sda5       136720384 156301311  19580928  9.3G 82 Linux swap / Solaris


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x12fftraa

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953523711 1953521664 931.5G 83 Linux


Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x12775cc3

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1        2048 1953523711 1953521664 931.5G 83 Linux


Disk /dev/mapper/cryptswap1: 9.3 GiB, 10024910848 bytes, 19579904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

I wrote this lines in my fstab
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=7dyta30a-795e-42ee-a4c1-3c9d7e36f4bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
#UUID=4e338ed48-72a2-48fb-bd26-858db2f1cc64 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

# LABEL="WD1" - /dev/sdb1 - 931.5 GiB
UUID=70ee834e-c722-420d-8492-bd1e04d54419    /home/user/wd1    ext4    defaults    0       0

# LABEL="WD2" - /dev/sdc1 - 931.5 GiB
UUID=aa9d1341-480d-44a4-a7d1-47f93754dc94       /home/user/wd2/    ext4    defaults    0       0

```

If I did sudo mount -a or reset all system I haven't hard drives mount in system. I need do this:
```

#!/bin/bash
sudo mount /dev/sdb1 wd1/
sudo mount /dev/sdc1 wd2/

```

I can't tell you why, but after 5 minutes of failing to access the system via ssh this hard drives disappear. I need run again the script to mount all drives. Do you understand!?
Thanks

**UPDATE1**
The behaviour where the hard drives disappear doesn't always happen. I can not find a relationship with events. Because it happened to be connected via ssh and the disks disconnected.

[B]UPDATE2
[/B]I really understand why this happened. I don't know how I should googled about this issue! I am really adrift! :confused::confused::confused::confused:

---

### Post by TheFu on 2018-12-29
If a ssd or HDD is disappearing, that will show up in the log files.  Check the power and SATA cables and SATA port used.  

If it is connected via USB, check the USB cable and try a different USB plug.  USB connections can be  impacted by vibrations.

**dmesg** will show HW disconnections.  If you see those, something is failing and I would expect the HDD is the problem until proven otherwise.  Make backups ASAP.

BTW, there's zero reason to hide UUIDs.  There's nothing special about them except they are guaranteed to be unique on any system and likely to be unique between systems.  You can force a UUID to be changed, if you like, then just fix any references to it in the OS like fstabs.

---

### Post by sed_faster on 2018-12-29
This is the output of my dmesg: [https://pastebin.com/yDgp4w34](https://pastebin.com/yDgp4w34)

**[UPDATE1]**
All hard drives are new but the mother board no. This is model of the board: [https://www.asrock.com/MB/ATI/775Twins-HDTV%20R2.0/index.asp](https://www.asrock.com/MB/ATI/775Twins-HDTV%20R2.0/index.asp)
I only can install Ubuntu Server 16.04.5 LTS (32Bits) on this board. If I try install Ubuntu Server 18.04 LTS 64Bits (because I can't find version 32bits of this flavor) I get stuck on this screen and after more a less five minutes I see a black screen with normally output script but many error relative of the disc. Finally I get stuck on this screen: [https://snag.gy/GgKCb6.jpg](https://snag.gy/GgKCb6.jpg)

**[UPDATE2]**
I don't know how I should configure the options in BIOS relative of the hard drives. Maybe I can't install the 18.04 version because the motherboards it is older or I should configure a different way parameter of the disc in BIOS.
[B]
[UPDATE3][/B]
All hard drives is internal and 3.5 connecting with the board through cable sata

---

### Post by TheFu on 2018-12-29
Try different SATA cables.
Check the power connections.
Check the PSU.
Move the SATA cables around to see if the issue follows the port on the motherboard.
New HDDs can be DOA.  Check the SMART data using a different computer.

---

### Post by sed_faster on 2018-12-29
> **TheFu said:**
> 
New HDDs can be DOA.  Check the SMART data using a different computer.

What this is means?
By the way I use this flavor ubuntu: [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/) ([32-bit PC (i386) desktop image]("http://releases.ubuntu.com/16.04/ubuntu-16.04.5-desktop-i386.iso"))

Thanks

---

### Post by TheFu on 2018-12-29
I did a little googling ... 
[https://en.wikipedia.org/wiki/Hard_disk_drive](https://en.wikipedia.org/wiki/Hard_disk_drive)
[https://www.webopedia.com/TERM/D/DOA.html](https://www.webopedia.com/TERM/D/DOA.html)
[https://www.howtogeek.com/134735/how-to-see-if-your-hard-drive-is-dying/](https://www.howtogeek.com/134735/how-to-see-if-your-hard-drive-is-dying/) - on Linux the tool is **smartctl**, but I've heard that some GUI disk tools will display the data. I'm happier using commands that work on servers since those work on desktops too.

Why did I say to use a different computer?  Because everything about _this_ computer is suspect.  We don't know that it is working correctly.

---

### Post by oldos2er on 2018-12-30
> **sed_faster said:**
> What this is means?

See [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by sed_faster on 2018-12-31
Thanks to all your support. I reinstall all system and I can operate all hard drives well. I really don't understand why this issues occurred because I followed the same steps in installations.
Thanks again to all support and advice

---

