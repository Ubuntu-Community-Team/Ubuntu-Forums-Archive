---
title: "folder permissions"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by bkamalnivas on 2008-06-19
is it possible to change the permissions ofthe folder - wannna change the group from root to administrator ....is it possible?
if so ...how??

---

### Post by mike2357 on 2008-06-19
You can use the command line. To do so open up a command window with ALT-F3, then type the commands:
cd parent_folder_of_the_one_you_want_to_change
chgrp admin folder_name

If you don't own the folder, you'll need to precede the command with sudo.

From gnome/nautilus:
Navigate to the parent folder, right-click on the folder for which you want to change permissions, select properties, then select the Permissions tab.

---

### Post by hyper_ch on 2008-06-19
what folder do you want to change?

---

### Post by bkamalnivas on 2008-06-19
i ve installed wubi...
am unable to create a shortcut to a folder in D drive thou am able to access it

---

### Post by hyper_ch on 2008-06-19
enjoy: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by bkamalnivas on 2008-06-19
just cudnt get this done...
am able to make links if folder group is administrator 
and not able to do the same if its root??

---

### Post by bodhi.zazen on 2008-06-19
Ownership and permissions are confusing at first. Take a look here :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

With that said, with both FAT and NTFS file systems permissions are set at the time of mount (you can not chown / chmod these partitions).

Unmount the partition.

Then :

sudo mount /dev/sdxy /media/windows -o uid=1000,gid=100,dmask=027,fmask=137

If you want to relax permissions user dmask=000,fmask=111

---

