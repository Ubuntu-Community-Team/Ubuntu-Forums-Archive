---
title: "permission for a newly mounted HDD"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by PeterFr on 2012-06-19
I have recognised a new HDD and formatted it. It can be mounted but cannot be written to as "permission denied". All my folders on the initial HDD work fine but I see them as mounted "in" root /.  My new HDD is in /media/removable (following a google hit).
I want this removable HDD to be;
1) recognised at boot, but may not be there at a subsequent boot
2) able to write/read to it from the fixed HDD and also;
3) see it from the network
I've tried; GNOME Commander, created the disk with GParted Partition Editor and would rather do this with the GUI than textual work in terminal.  
(Apple MAC user)
Any ideas?

---

### Post by carl4926 on 2012-06-19
Is it being mounted on the fly
ie; it's not been added to fstab? with a mount point?

---

### Post by jtarin on 2012-06-19
What file system did you format with?Is your user in the correct group to write to the drive?
You can right click on the drive in your file manager and control permissions.

---

### Post by anewguy on 2012-06-19
It's possible a udev rule file may need to be created as well with reference to a script to set some it up.

Dave ;)

---

### Post by PeterFr on 2012-06-19
> **carl4926 said:**
> Is it being mounted on the fly
ie; it's not been added to fstab? with a mount point?

No, it will be added to an "off" system and then restarted with the drive installed in an EZ-SWAP tray.  The system recognises the drive, and I can "mount" it by right clicking on it, BUT, I cannot write to it as I do not have the correct permission.  My internal HDD is at root mounted / and this swappable HDD is at /media/removable.
How can I give it the same permissions as the root drive?

---

### Post by PeterFr on 2012-06-19
> **jtarin said:**
> What file system did you format with?Is your user in the correct group to write to the drive?
You can right click on the drive in your file manager and control permissions.
/dev/sdb1 - formatted ext4 label removable.  It has one "system" folder lost+found but I cannot make a folder or copy anything to the drive;
owner of the drive is root but folder access is greyed out
There is only one user on the system (me) and I think I am administrator

---

### Post by carl4926 on 2012-06-19
If you add it to fstab
Set a mount point, I usually create a directory specific to a device or partition.
Then chown the mount point with -R

---

### Post by mastablasta on 2012-06-19
> **PeterFr said:**
> There is only one user on the system (me) and I think I am administrator
 
you have administrator rights (can elevate to that status usign sudo or gksu) but you are not root/administrator
 
not sure about mounting but for permission.... 
gksudo nautilus
 
this will elevate you to admin level.
then right click on the drive and change the ownership of the drive or direcotry to the user (yourself) and you can also set the sharing options here.

---

### Post by PeterFr on 2012-06-19
> **mastablasta said:**
>  not sure about mounting but for permission.... 
gksudo nautilus
finally convinced myself that I can read/write and see the drive over the network.  After shut-down the drives data is gone (using Dash) and comes back when system restarted with the drive installed.  All I did was get authority, go to the mount point and set permissions to (me) user; close everything up and restart - problem fixed.  Thanks for your interest and help!

---

