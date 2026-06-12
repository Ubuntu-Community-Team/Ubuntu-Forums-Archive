---
title: "Change Permissions to allow User access"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2012-05-05
I've set up a second administrator user on my laptop which has 12.04 ubuntu dual boot with a shared drive between xp and ubuntu. 

However the new user does not have access to the shared drive and i do not know how to change the permissions to allow access. 

I've tried to change the permissions on the shared drive by: 
(right click on it and selecting) -properties, 
-permissions,
-and changing folder access,

however whatever i do just changes back before I even get to click: "apply permissions to enclosed files", I've played around with it quite a bit now...

If anyone has any solution to this, to give the second user access to the shared drive..

---

### Post by gordintoronto on 2012-05-05
I suppose there's always the chown command, but that seems an awkward, brute-force approach.

Is the shared drive formatted as NTFS? Fat32 might be easy to share.

How big is the drive?

---

### Post by pqwoerituytrueiwoq on 2012-05-05
chmod the folder to 1777 i think that should do it

---

### Post by souravc83 on 2012-05-05
Yes, chmod/chown command will do.
Why is it brute force?
It is supposed to control the permissions to folders.
The reason the OP cannot do it by right clicking is because he is not root, and hence cannot change permissions.
You can
1) be root and right click. For this, you have use the "gksudo nautilus" command I think. I have never tried this. I think it is kinda dangerous.
2) Much more robust way is to go to the command line and use chmod as root and change the permission of the folder where the drive is mounted.

---

### Post by Morbius1 on 2012-05-05
> I've set up a second administrator user on my laptop which has 12.04  ubuntu dual boot with a shared drive between xp and ubuntu. If you mean a shared partition then it's most likely an ntfs or fat32 partition.
> I've tried to change the permissions on the shared drive by: 
(right click on it and selecting) -properties, 
-permissions,
-and changing folder access,

however whatever i do just changes back before I even get to click:  "apply permissions to enclosed files", I've played around with it quite a  bit now...
This would be consistent with an ntfs or fat32 partition. When you mount an ntfs partition it creates a "view" of that partition that looks like it has linux permissions but they are immutable so a chown or a chmod has no affect.
> However the new user does not have access to the shared drive and i do not know how to change the permissions to allow access. 
Please post the output of each of the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```With those commands you will have all the information you need to have this partition automount with access to everyone on your system by adding a line to /etc/fstab. 

For an NTFS partition you can use the following as a template:
```
UUID=DA9056C19056A3B3 /media/Shared ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

```** the blkid command will give you the correct UUID number for your partition.

** You will have to make the mount point yourself:
```
sudo mkdir /media/Shared
```** If the shared partition is currently mounted, unmount it.

** Then run the folllwoing command to test for errors and mount the partition:
```
sudo mount -a
```

---

