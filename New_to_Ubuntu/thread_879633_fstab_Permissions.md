---
title: "fstab Permissions"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by nikki93 on 2008-08-04
Hello, this is my second day using Ubuntu (or any form of Linux), and I must say, its been awesome! :)

So, I wanted to mount my other two Windows partitions/drives, C: and D: (both NTFS), and, seeing that ntfs-3g came preinstalled, I started editing the fstab (I know that Ubuntu already gives me an option in the 'Places' menu for this, but I wanted to do it myself, because I wanted a directory different from the default one, and nothing on the desktop).

At first, I mounted the partitions with default options, but that gives me a 'Do you want to execute or view this file?' (or something like that) dialog every time I open a file on a Windows partition.

I searched around for what permissions would fix this (I'm a little new and still don't completely get how fmask and dmask work). This is what I ended up with:-
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

# Entry for /dev/sda7 :
UUID=1182c7da-1b41-497a-a95f-52edef225c14 / ext3 relatime,errors=remount-ro 0 1

# Entry for /dev/sda6 :
UUID=d59583c6-76ce-4ea3-a49f-a228237e8d2d none swap sw 0 0

/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

# Entry for windows drives (added by nikki):
# /dev/sda2 = C:
# /dev/sda5 = D:
/dev/sda2 	/windows/c 	ntfs-3g dmask=0222,fmask=0333 0 0
/dev/sda5 	/windows/d 	ntfs-3g dmask=0222,fmask=0333 0 0
```

This removes the dialog, but now the NTFS partitions are read-only.

Can anyone tell me how I can make 'em read/write-able, but without the dialog?

Thanks! :)

---

### Post by ibuclaw on 2008-08-04
1) ntfs-3g is no longer needed, you can just use good ol' ntfs instead.

2) replace your options with "defaults,gid=46,umask=007"

So we have something that looks like this:
```

/dev/sda2 	/windows/c 	ntfs    defaults,gid=46,umask=007 0 0
/dev/sda5 	/windows/d 	ntfs    defaults,gid=46,umask=007 0 0

```
Then remount them
```
sudo mount -o remount /dev/sda2
sudo mount -o remount /dev/sda5

```

You may need to change the gid number, but it should be the group number of the plugdev user.
```
cat /etc/group | grep plugdev
```

Regards
Iain

---

