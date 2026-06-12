---
title: "Not able to view/access windows partitions and files"
date: 2016-12-21
forum: New to Ubuntu
---

### Post by harrychauhan on 2016-12-21
Hello, I am new user of Ubuntu 16.10. I don't have any experience of using Ubuntu.
I have installed Ubuntu 16.10 using pendrive and previously I had Windows 10 with 3 partitions **C:** for windows, **D:** and **E:** for personal usage, 
I have installed ubuntu by removing windows by selecting first option while installation.

I'm not able to see any usage data of windows partitions.

After searching about this I followed these commands:

```

harry@terminator:/media/windows$ sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x67d4e835

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048 1945448447 1945446400 927.7G 83 Linux
/dev/sda2       1945450494 1953523711    8073218   3.9G  5 Extended
/dev/sda5       1945450496 1953523711    8073216   3.9G 82 Linux swap / Solaris

Partition 2 does not start on physical sector boundary.

```

```

harry@terminator:~$ sudo ntfs-3g /dev/sda1 /media/windows
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
harry@terminator:~$ 

```

and running this command:
```

fuser -m /dev/sda1

```
Gives the output(trimmed for question):
```

harry@terminator:~$ fuser -m /dev/sda1
/dev/sda1:               1rce     2rce     3rce     5rce     7rce     8rce     9rce    10rce    11rce    12rce    13rce    14rce    15rce    16rce    18rce    19rce    20rce    21rce    22rce    24rce    25rce    26rce    27rce    28rce    30rce    31rce    32rce    33rce    34rce    35rce    36rce    37rce    38rce    
....... trimmed for question

```

Now I don't have any idea of how to access all my files of **D: & E: **partitions. they have very important data that I don't want to lose anyhow?

Any help will be awesome.
Thanks :)

---

### Post by yancek on 2016-12-21
the fdisk output you posted above shows only Linux installed.  sda1 shows as a Linux filesystem which is why your attempt to mount it as ntfs fails.  You may be able to recover data using software such as testdisk if you stop using this computer.  If you selected the first option as show in this tutorial "Erase disk and install Ubuntu", that was your mistake.  It does exactly as it states.

[https://fossbytes.com/install-ubuntu-16-10-yakkety-yak-installation-guide/](https://fossbytes.com/install-ubuntu-16-10-yakkety-yak-installation-guide/)

If you had a pre-installed windows system, it was likely using UEFI.  The Ubuntu documentation at the site below explains in detail how to do this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by harrychauhan on 2016-12-21
So now can i get the old data after installing windows again and recovering it?

---

### Post by QIII on 2016-12-21
Hello!

Please do not reinstall Windows. That will just compound the problem.  So will using the machine at all right now.

Shut the machine down.  Use a different machine to download and create a TestDisk disk.  Boot to that and attempt to recover your data from your hard drive.

---

### Post by harrychauhan on 2016-12-21
How do i do this? Do i have to remove the hard drive from pc? And how do I boot to that disk? 
Need a bit long explanation thanks.

---

### Post by oldos2er on 2016-12-21
Testdisk has lots of online documentation: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

The simplest way for you to run it might be to boot from your Ubuntu pendrive, then install it and run it from there: ```
sudo apt-get install testdisk && sudo testdisk
``` No need to remove the hard disk. 

> they have very important data that I don't want to lose anyhow? No backups?

---

### Post by harrychauhan on 2016-12-21
No extra hd drive so could not take backup.

I have a bootable pendrive so if I boot from that prendrive it will ask me for installing the OS, so what should I do?

Or I install testdisk in this OS(Ubuntu 16.10) and recover directly, I guess this would not be possible because the error I might get could the '/ target is busy' i guess. Not sure..

---

### Post by yancek on 2016-12-22
I think your best option is to use the bootable pendrive and download and run testdisk from there.  Lots of documentation and instructions at their site.  When you boot this, you should have the option to try or install so select to try rather than install.  You have installed Ubuntu over your previous windows so your only hope is to recover some data.  You need somewhere to save the data to, another dirve, flash drive or partition.

---

### Post by oldos2er on 2016-12-22
> **harrychauhan said:**
> I have a bootable pendrive so if I boot from that pendrive it will ask me for installing the OS, so what should I do? It should give you two options, try Ubuntu or install Ubuntu. Choose "try." You did download the desktop ISO, right?

---

### Post by khPWXxF on 2016-12-22
I can clarify the problem but not tell you how to fix it.  Windows 10 leaves its partitions locked after closedown for security (and flummox Linux users?). The feature can be turned off in w10 with
Window key + X
Power options
Choose what power buttons do
Turn on fast startup - untick it.

Ditto for the other power off mechanisms.

If you still have w10 runnable then that's the fix.  I don't know what to do if w10 is not available to you.
Hth.
Phil

---

