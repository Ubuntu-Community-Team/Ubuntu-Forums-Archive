---
title: "Create FAT32 and ext3 partitions on pendrive"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by corkscrew on 2008-11-09
I am trying to create 2 partitions on a 8 gig USB pen drive. I want 1 partition FAT32 and 1 ext3 (for quickstart a linux backup program).

I am using gparted from under Hardy Heron. It makes both partitions ok, but i can only read and write to the FAT32, I cant do anything on the ext3 partition.

What have i done wrong?

---

### Post by handydan918 on 2008-11-09
Sounds like it's a permissions issue on the ext3 partition. Since fat32 doesn't do permissions, you wouldn't have a problem there.

chmod 777 partition_name

---

### Post by corkscrew on 2008-11-09
The ext3 partition appears on the desktop if i right click and select permissions it says permissions of "disk1" could not be determined what do i do to fix this

thanks for your help

---

### Post by C.S.Cameron on 2008-11-09
Have you tried "gksu nautilus"?

---

### Post by corkscrew on 2008-11-09
no whats that?

---

### Post by C.S.Cameron on 2008-11-09
You can type it in terminal or after pressing Alt F2.
This might let you change permissions on the flash drive.

---

### Post by MasterSander on 2008-11-09
gksudo nautilus let's you run nautilus as root, that way you might be able to access the ext3 partition, normal users might not have permissions to access it. had that problem on openSuse, I couldn't access my ntfs partitions

---

### Post by jwood1961 on 2008-11-15
I also cannot mount an ext3 partition on my pen drive. In my case a 32Gb from Alcor Micro (chinese?). Format to ext3, with or without another FAT32 partition on the pendrive and the system fails to mount with error messages as in attached screenshot. First comes the "Cannot mount Volume", then a minute or so later, the "Unable to Mount Volume".

Suggests using DMESG | TAIL .... the output from which is attached. Suggests system tries to mount first as FAT32, then as ext3, then complains of not finding a valid journal superblock. Not sure what that is, or how to fix it.

I've tried both things suggested so far in this thread: gksu nautilus, and chmod 777 /dev/sdb1 etc... still the same result.

If I reformat to FAT32 it all mounts fine again. But this means I can't use rsync, or Unison properly to create a backup mirror; or use sbackup because of the 4Gb limit on FAT32 filesize.

I was using gParted to partition/format. Tried the gParted forum - suggested it was an error in the Dbus subsystem used by Gnome to manage hotplugging.

Here is the thread: [http://gparted-forum.surf4.info/viewtopic.php?id=4913](http://gparted-forum.surf4.info/viewtopic.php?id=4913)

Which also has some other /etc/fstab, lsusb, and DMESG | /dev/sdb1 outputs.

System Intrepid with latest updates applied.

Any ideas/workarounds?

JW

JW

---

### Post by corkscrew on 2008-11-15
chmod 777 worked for me and I downloaded programs that allowed me to label the partitions as well.

As far as backing up i've gone through loads of posts and programs since i keep my data on ntfs and fat32 disks and partitions.

However i finally came up with the solutuin for a newbie to linux like me its a GUI for rsync called Grsync which seems to back up and sync to anything. You can download from synaptic package manager.

good luck

---

