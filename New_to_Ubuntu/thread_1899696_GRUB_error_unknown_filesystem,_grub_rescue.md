---
title: "GRUB error: unknown filesystem, grub rescue"
date: 2011-12-24
forum: New to Ubuntu
---

### Post by nnjond on 2011-12-24
Hi,

I'm trying to repair my grub with a live cd.

sudo fdisk -l

returns:
Disk /dev/sda: 250.1 GB

But sudo mount /dev/sda

returns:

can't find...

I understand I need to mount before I,-

sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by coffeecat on 2011-12-24
> **nnjond said:**
> I'm trying to repair my grub with a live cd.

sudo fdisk -l

returns:
Disk /dev/sda: 250.1 GB

It should return a lot more. All that line is telling you is that you have a 250GB drive designated sda. You've left out all the partition information which you need in order to see which is your Kubuntu root partition.

> **nnjond said:**
> 
But sudo mount /dev/sda

returns:

can't find...

You can't mount a whole disk, only a partition, and you need to specify a mount point. The mount command needs to be:

```
sudo mount /dev/sdaX /mnt
```

Where X = the partition number of the partition you are trying to mount, that is your Kubuntu mount partition.

> **nnjond said:**
> I understand I need to mount before I,-

sudo grub-install --root-directory=/mnt/ /dev/sda

That line is correct, but you need to determine which partition you need to mount. Run fdisk again and post the whole of the output. It's quite lengthy, so highlight it in the terminal, right-click -> copy and then paste it into your post, enclosed between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by nnjond on 2011-12-24
> sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d113f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   486432767   243215360   83  Linux
/dev/sda2       486434814   488396799      980993    5  Extended
/dev/sda5       486434816   488396799      980992   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 




A rescue disk has returned:

Cannot find a valid root file system

---

### Post by coffeecat on 2011-12-24
> **nnjond said:**
> A rescue disk has returned:

Cannot find a valid root file system

Which rescue disk? 

If your Kubuntu root partition was undamaged, it would be sda1. In which case, the commands to re-install grub from the live CD would be:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

It will do no harm to try, but if it doesn't work, then we must assume the rescue disk message is accurate and this will need more investigation. If this is so, boot up the live (K)ubuntu CD, ensure that you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags.

---

### Post by nnjond on 2011-12-24
Thanks

```
sudo bash boot_info_script.sh 

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information...                                                   
Searching sda5 for information... 
Searching sdb1 for information...                                                   
                                                                                    
Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Documents/".

```

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   486,432,767   486,430,720  83 Linux
/dev/sda2         486,434,814   488,396,799     1,961,986   5 Extended
/dev/sda5         486,434,816   488,396,799     1,961,984  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2023 MB, 2023751680 bytes
255 heads, 63 sectors/track, 246 cylinders, total 3952640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63     3,951,989     3,951,927   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        d1fe2e27-bee0-4f73-b053-9d8a466d0742   ext4       
/dev/sda5        4b65ac39-74e1-471e-8d0b-48ad8555668e   swap       
/dev/sdb1        d6185cc0-15e1-4702-8924-7d6ab1458f3a   ext4       2GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by coffeecat on 2011-12-24
This is the important bit:

> **nnjond said:**
> ```

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   [COLOR="Red"]mount: wrong fs type, bad option, bad superblock on /dev/sda1,[/COLOR]
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

I guess this is why the rescue disk gave the error it did. (You didn't say what the rescue disk is - there are many.) You need to run a filesystem check on sda1 from the live CD. The easiest way is to open Gparted, right-click on sda1 and choose "check". This may or may not work, depending on how damaged the filesystem is.

You haven't told us anything about the events that led up to this. Something must have caused the filesystem in sda1 to be damaged. Do you know what this might be?

---

### Post by nnjond on 2011-12-24
The option to check sda1 is ghosted.

# My os froze during a mundane click and I tried to reboot.

# Can't remember which of several rescue discs I tried not knowing what I was doing

---

### Post by coffeecat on 2011-12-24
> **nnjond said:**
> The option to check sda1 is ghosted.

That doesn't look good. The only other thing you can try is fsck from the terminal and see whether you get any useful messages. I fear that the filesystem damage may be too severe, but try this from a live session terminal:

```
sudo fsck -v /dev/sda1
```

---

### Post by iculookingatme on 2011-12-27
Hi everyone,

I have spent some time going through most of the threads on this site about Grub errors, and whilst the instructions are quite lengthy, I have become confused and would like to ask for the "Dummys Guide" instructions on how I can possibly fix my issue.

I have a Dell Optiflex GX270 (if that even helps) with no operating system. I installed via CD the UBUNTU 11.10. The set up appeared to be going well. Until I had to restart the comp.

I now receive a message "Primary drive 0 not found"
I select F1 to continue
I receive a message "error: unknown filesytem."
"grub rescue>"

I typed in ls and receive the following:
(hd0) (hd0,msdos1) (fd0)

It is from this point I am confused. Please please can someone help me? #1 Absolute Beginner.

(I know whoever answers must be overjoyed to have to help me in baby steps :confused: )

Thank you very much!!!

---

