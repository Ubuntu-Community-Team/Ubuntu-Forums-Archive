---
title: "[SOLVED] How do I mount an internal floppy drive?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-07-09
I have just upgraded to Hardy Heron and everything seems to be working correctly but when I put a floppy disc into the drive nothing happens.  After a few seconds the drive spins up then back down and when I double click on the "floppy disc" icon in the Computer section it says "Unable to mount location.  Can't mount file" 
Any ideas what might be causing this or how to fix it?

---

### Post by iaculallad on 2008-07-09
> **curiousnoob said:**
> I have just upgraded to Hardy Heron and everything seems to be working correctly but when I put a floppy disc into the drive nothing happens.  After a few seconds the drive spins up then back down and when I double click on the "floppy disc" icon in the Computer section it says "Unable to mount location.  Can't mount file" 
Any ideas what might be causing this or how to fix it?

Try using Places->Floppy Disk if it works.

---

### Post by curiousnoob on 2008-07-09
> **iaculallad said:**
> Try using Places->Floppy Disk if it works.

As soon as I clicked Places I could here the floppy drive spin up but when I selected it nothing happened.

---

### Post by ChameleonDave on 2008-07-09
Please go to a terminal and enter the following commands.  Post the output here.

```

cat /etc/fstab
sudo blkid

```

Have you tried with only one floppy?  Does it fail with others too?  Is the floppy properly formatted?

---

### Post by iaculallad on 2008-07-09
> **curiousnoob said:**
> As soon as I clicked Places I could here the floppy drive spin up but when I selected it nothing happened.

You're problem might be related to bug [#203722]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/203722").

---

### Post by curiousnoob on 2008-07-09
> **ChameleonDave said:**
> Please go to a terminal and enter the following commands.  Post the output here.

```

cat /etc/fstab
sudo blkid

```

Have you tried with only one floppy?  Does it fail with others too?  Is the floppy properly formatted?

Unfortunately I only have one disc right now although I know it used to work.  
Here is the results of the commands: 
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5f2a10d9-b11c-4492-9e96-d3a7cd79b380 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6634d6cf-26bb-49a4-b792-7b8753dd5714 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D2-0B0B" TYPE="vfat" 
/dev/sda2: UUID="F0246BE5246BAD72" TYPE="ntfs" 
/dev/sda3: UUID="5f2a10d9-b11c-4492-9e96-d3a7cd79b380" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="6634d6cf-26bb-49a4-b792-7b8753dd5714"

---

### Post by ChameleonDave on 2008-07-09
Hmm, with only one disc, we can't discount the possibility that it's just the disc that is screwed.  Floppies can be damaged, e.g. by being left near a magnet.

Do you actually need the data on this disc?  How about simply formatting it?  I haven't actually got a floppy drive myself, but I believe that the following command with format it:

```

sudo apt-get install fdutils
sudo superformat /dev/fd0

```

Try manually mounting the floppy like this:
```

sudo mount -v /dev/fd0

```

What happens?

---

### Post by curiousnoob on 2008-07-10
> **ChameleonDave said:**
> Hmm, with only one disc, we can't discount the possibility that it's just the disc that is screwed.  Floppies can be damaged, e.g. by being left near a magnet.

Do you actually need the data on this disc?  How about simply formatting it?  I haven't actually got a floppy drive myself, but I believe that the following command with format it:

```

sudo apt-get install fdutils
sudo superformat /dev/fd0

```

Try manually mounting the floppy like this:
```

sudo mount -v /dev/fd0

```

What happens?

I am now able to access the files on the disc but I am unable to erase them or add anything.  
When I attempt to superformat I get this: 
sudo superformat /dev/fd0
open: Device or resource busy

And when I try to write something to the disc I get this: 
Error opening file '/media/floppy0/PCTgrade082.xls': Permission denied 

The disc is not write protected either.

---

### Post by ChameleonDave on 2008-07-10
It sounds like you mounted it with the second command I gave, and then tried to format it with the first command.  Is that right?

When formatting, the drive must be unmounted.  Close down anything which is accessing the drive, and then do "sudo umount /dev/fd0".

I suspect that the "Permission denied" stuff is because we mounted it as the superuser.  Try mounting it again without the "sudo" part.  (Normally, sudo is necessary with the mount command, but we don't need it if the device is listed in fstab.)

---

### Post by curiousnoob on 2008-07-10
> **ChameleonDave said:**
> It sounds like you mounted it with the second command I gave, and then tried to format it with the first command.  Is that right?

When formatting, the drive must be unmounted.  Close down anything which is accessing the drive, and then do "sudo umount /dev/fd0".

I suspect that the "Permission denied" stuff is because we mounted it as the superuser.  Try mounting it again without the "sudo" part.

I'm getting so close.  You were right, I accidentally switched the order of the commands and once I unmounted the drive I was able to successfully format it.  
Now I am not able to mount it again for some reason.  I have tried using the mount command with and without the sudo prefix and both give this result:
mount -v /dev/fd0
mount: you didn't specify a filesystem type for /dev/fd0
       I will try all types mentioned in /etc/filesystems or /proc/filesystems
Trying fuseblk
mount: I could not determine the filesystem type, and none was specified
johnson@johnson-desktop:~$ sudo mount -v /dev/fd0
mount: you didn't specify a filesystem type for /dev/fd0
       I will try all types mentioned in /etc/filesystems or /proc/filesystems
Trying fuseblk
mount: you must specify the filesystem type

---

### Post by ChameleonDave on 2008-07-10
Hmm.  It is as though the act of formatting it somehow removed the references to the floppy drive in /etc/fstab.

Please run "cat /etc/fstab" again to see if something has changed in that file.

---

### Post by plucky on 2008-07-10
Two methods 

1) Open a terminal and ```
mkfs.vfat /dev/fd0
```
Open **Places** and select Floppy.Your file browser should now open on the floppy.

or

2) Open a terminal and ```
mkfs -t ext2  /dev/fd0
sudo mount /dev/fd0 /media/floppy0
```

The floppy should now be mounted and available in the file browser.

Don't forget to dismount the floppy before removing ```
sudo umount /dev/fd0
```

Good Luck

---

### Post by curiousnoob on 2008-07-10
> **plucky said:**
> Two methods 

1) Open a terminal and ```
mkfs.vfat /dev/fd0
```
Open **Places** and select Floppy.Your file browser should now open on the floppy.

or

2) Open a terminal and ```
mkfs -t ext2  /dev/fd0
sudo mount /dev/fd0 /media/floppy0
```

The floppy should now be mounted and available in the file browser.

Don't forget to dismount the floppy before removing ```
sudo umount /dev/fd0
```

Good Luck 
That fixed it.  Thank you to everyone who helped out.  I was going slowly insane trying to figure this out.

---

### Post by ChameleonDave on 2008-07-10
> **curiousnoob said:**
> That fixed it.  Thank you to everyone who helped out.  I was going slowly insane trying to figure this out.

That mounted it.  But we haven't checked fstab.

---

### Post by plucky on 2008-07-11
> That mounted it. But we haven't checked fstab. 


Fstab will not change but mtab will

This is the line added to mtab after the floppy is mounted > /dev/fd0 /media/floppy0 vfat rw,nosuid,nodev,utf8,user=field 0 0


Hope that helps

---

### Post by ChameleonDave on 2008-07-11
> **plucky said:**
> Fstab will not change but mtab will

This is the line added to mtab after the floppy is mounted 


Hope that helps

No, it doesn't help.  You don't know what you're talking about.

---

### Post by plucky on 2008-07-11
etc/mtab shows the mounted partitions and drives on your system and changes as drives are mounted and dismounted.

etc/fstab tells the system how to mount the partitions and drives and does not change dynamically.If you want the system to mount a partition in a specific way(say read only),you would put that information into fstab.
You as the user controls fstab,your system controls mtab and shows how the drives and partition are mounted and changes when changes are made to the system by you.

Hope that helps.

---

### Post by ChameleonDave on 2008-07-11
> **plucky said:**
> etc/mtab shows the mounted partitions and drives on your system and changes as drives are mounted and dismounted.

...

Hope that helps.

Perhaps you'll tell me how to tie my shoelaces next?

---

