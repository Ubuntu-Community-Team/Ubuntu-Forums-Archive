---
title: "Sharing folders over network, permission issues"
date: 2017-03-19
forum: New to Ubuntu
---

### Post by kiicki on 2017-03-19
So I have managed to share the folders I want from my Linux so I can map them on my Windows 10 from a different PC. Because of permission issues, I cannot share my external HDD but if I mount the external HDD to "/home/username/external HDD" I can share my whole "Home" folder and on my Windows map that folder and find my external HDD. I can even write to it. What I find odd is that all other folders that is located in that "Home" folder such as: documents, downloads etc cannot write like the external HDD. To be able to write to it I need to manually share them which I didn't need to do with my external HDD.

So basically if I share my Home folder, I can read everything inside there but I cannot write except for the External HDD which can write.

I cannot manually share the external HDD and I need to manually share Downloads and documents folder that is inside the Home folder.

My question is: Why can I write to the external HDD without manually share it, and why can't I write to other folders inside the Home folder unless I manually share those folders?

Do I need to manually share every folder in home to be able to write on it from a different computer if I map it?

---

### Post by TheFu on 2017-03-19
If you edit the /etc/samba/smb.conf file, use the [homes] section to allow your userid access from Windows clients. Be certain to set the smbpasswd correctly.

As for external disks, the file system used matters. Ownership and permissions matter very much to Linux and all Unix-like OSes. It is central to the system security. Often, external disks do not support Unix-style permissions, so only the mount options can provide the necessary permissions statically.  If you format the external disk to have a Linux file system (not NTFS or FAT-whatever), then manually mount the disk, and share it via the smb.conf in a different section, then it should work, provided the file and directory permissions allow it.

In another post here, I list  the techniques I use to make samba "just work." If you do those things, then it will work.

---

### Post by Morbius1 on 2017-03-20
> Because of permission issues, I cannot share my external HDD
Sure you can. But if you are allowing the system to automount the HDD in it's default mount point ( /media/username/external HDD ) then you will confront a security measure Linux adopted some years ago.

You didn't say how your are sharing it so I'm going to assume it's Samba since Win10 is involved. And you didn't say with what mechanism - declare a share definition in smb.conf or create one through Nautilus. But let's go through the mechanics of this.

I want to share /media/username/external HDD so I create a share definition allowing write access to everyone:
> [external HDD]
path = /media/username/external HDD
read only = no
guest ok = yes
That will not work. It won't work regardless of what permissions are on "external HDD". The problem is /media/username.

Run the following command:
```
ls -dl /media/$USER
```
You will get something like this:
> drwxr-x---+ 2 root root
That doesn't look right as it would appear that only root can access that folder and anything mounted under it. But there's that little "+" sign at the end which signifies that an extended attribute is in play here. Now run this command:
```
getfacl -t /media/$USER
```
You will get back something like this:
> getfacl: Removing leading '/' from absolute path names
# file: media/morbius
USER   root      rwx     
user   morbius     r-x     
GROUP  root      ---     
mask             r-x     
other            ---
Root has the power of life and death over /media/username but you have the power to traverse the folder to get to what's mounted under it. In fact you are the only regular user that can get to what's mounted under it. This is done by design. The samba "guest" user is not you so access is denied - not by Samba but by Linux.

You can mount the HDD somewhere else like your home folder or even just one step up under /media directly ( /media/external HDD ) or you can modify your share definition:
> [external HDD]
path = /media/[COLOR=#0000cd]**username**[/COLOR]/external HDD
read only = no
guest ok = yes
[COLOR=#0000cd]**force user = username**[/COLOR]
Now the anonymous "guest" user will be converted to "username" for that share and he will be able to get past /media/username to what's mounted under it.

---

