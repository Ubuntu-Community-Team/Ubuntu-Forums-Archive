---
title: "Difficulty installing ubuntu 12.04 on new Windows 7 laptop"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by tomsax on 2012-08-25
I'm installing ubuntu on my new HP laptop which already has Windows 7.  I've got Ubuntu 12.04 on a DVD.

I want to install it in the best way and assume that is with a dual boot using a dedicated partition.

So I choose the "Something else" option after install.  (I tried the install in windows before but that doesnt work plus I don't think I want it installed within windows).

I get to the screen where it lists the partitions.  I have

dev/sda1 ntfs
dev/sda2 ntfs
dev/sda3 ntfs
dev/sda4 fat32

(there is no free space)

What do I do now?  

Tom

---

### Post by westie457 on 2012-08-25
Good of HP to make life easy (not)

This is a long process and is usually recommended on here.

1 Make backups of the Recovery Partition and the HP Tools partition

2 Make a Windows Recovery CD

Keep these disks in a safe place for future use.

Defrag Windows twice.


In Windows right click on the 'My Computer' icon and select 'Manage'. In the window that opens select 'Disk Management', you will see all of the partitions on the hard drive.

Right click on the HP Tools partition and select 'delete'
Do the same for the 'Recovery' partition. If not allowed to delete these do not panic, they can be removed later.

Right click on the main Windows partition and select 'Shrink Volume'. Make this as small as Windows allows. Leave this unallocated space as it is.

Now boot your Ubuntu Cd into a Live Desktop - 'Try' mode and open Gparted. In the window you should see all the partitions with a blank space in the middle.

Now you can delete the recovery and hp-tools partitions. Again leave this space blank (unformatted).

Now you can run the Ubuntu installer and install alongside Windows for the easy options or choose 'something else' for slightly harder (more control) options.

If you choose the 'Something Else' option and you want more guidance post back here with what you want to do.

---

### Post by tomsax on 2012-08-27
Thanks for your help.  All sorted!

---

