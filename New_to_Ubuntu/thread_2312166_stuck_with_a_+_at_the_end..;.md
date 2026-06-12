---
title: "stuck with a + at the end..;"
date: 2016-02-02
forum: New to Ubuntu
---

### Post by claude9 on 2016-02-02
HI guys

Could someone enlighten me a bit...Hre is what I'm after

31013  4 drwxrwxrwx+ 5 root   root    4096 févr.  2 17:29 .
130305  4 drwxrwx--x  4 root   claude  4096 nov.  24 18:05 ..
     5 12 drwx------  1 claude claude 12288 févr.  2 16:03 01CAA6875263FA00
     5  4 drwx------  1 claude claude  4096 févr.  2 16:03 01CAA6888510BC30
     2  4 drwxrwx--x  2 claude claude  4096 févr.  2 10:28 60826654-32a3-4345-af41-2871edc532ae

first line is a parent directory ( belonging to root..) giving acces to 3 disks ( in fact a big 1,5T usb disk with 3 partitions...)
2 quickies:
1) First line: What is the meaning of this small x at the end of the "rights" section of the line ?
2) claude ( me BTW...) is a superuser but even if i'm logged as claude,I'm stricly unable to change the rights on any of the 3 disks...

must be goofing somewhere !!!!
Thks in advance

Claude

---

### Post by carverj on 2016-02-02
1) I believe the answer to your question is that 'others' may view the contents of 'this' directory
2) I would recommend using super user account for modifying permissions and ownership
Any questions please ask!

---

### Post by nerdtron on 2016-02-03
> 1) First line: What is the meaning of this small x at the end of the "rights" section of the line ?
the x means execute. If this is a directory (as indicated by "d" on the beginning of the permissions) means you can execute the folder, which means you can "go inside" that folder.

> 2) claude ( me BTW...) is a superuser but even if i'm logged as claude,I'm stricly unable to change the rights on any of the 3 disks...
the user claude is a normal user with admin privileges. In order for you to use your "admin rights" you should use "sudo" on the beginning of your command. For example to update the apt-get cache you run:
```
 sudo apt-get update 
```

---

### Post by Dennis N on 2016-02-03
> 31013 4 drwxrwxrwx+ 5 root root 4096 févr. 2 17:29

The + symbol at the end of the permissions means the folder has an acl, or "access control list", which grants some extra permissions for that folder to specified users.

[https://wiki.archlinux.org/index.php/Access_Control_Lists](https://wiki.archlinux.org/index.php/Access_Control_Lists)

If you are the owner of a file or directory, you can change the permissions for it without admin. privileges. 

In a listing, the file system on a partition is a directory.
```
[dmn@Zotac mnt]$ ls -l
total 4
drwxr-xr-x 19 dmn dmn 4096 Dec 25 19:15 Common-Files
```
Common Files is a directory (d), but also the root of a file system on a partition. The owner can change the permissions.

---

### Post by claude9 on 2016-02-04
Thks guys...
I think I've found the solution...
I was trying to share a folder located on an external NTFS harddisk attached to a PC being under Ubuntu acting as a Samba Server for a remote Android samba client..
the problem was I had no rights to acces the HDD folders. My understanding is that NTFS is the problem ( not beeing POSIX compatible..) and consequently, when the HDD was mounted, it was given a very restricted set of rights..
Thks for all yr tips, gentlemen

---

