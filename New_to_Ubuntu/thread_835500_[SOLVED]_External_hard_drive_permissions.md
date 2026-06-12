---
title: "[SOLVED] External hard drive permissions"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by bertwagner on 2008-06-20
I have recently formatted my external hard drive as fat32.  I have it auto mount successfully on startup by including the following line in my /etc/fstab file:
```
/dev/sdb1 /media/outer vfat auto,user,exec,rw,sync 0 0
```

My problem is that I can only write files to the drive as root.  I have tried changing permissions as root through nautilus and through chmod commands but niether have worked.  I also have tried editing /etc/udev/rules.d/40-basic-permissions.rules to the following but it also does not allow me to write to the drive as non-root:
```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device",		MODE="0666"
```

I'm out of ideas of what to try next.  It seems I cannot write files to the drive with any user besides root. Any suggestions for what I should try next would be greatly appreciated.

---

### Post by Pjotr123 on 2008-06-20
You've probably forgotten to "safely remove" (unmount) the USB external drive in Windows. This is also necessary in Windows. Windows then writes a stop code that Linux needs.

Solution: boot up Windows and let it "safely remove" the disk as yet. That should do the trick.  :-)

---

### Post by chrisccoulson on 2008-06-20
If you can write as root, then it's a permissions issue as opposed to a filesystem issue. Don't play with UDEV rules to try and fix this unless you really know what you're doing with them. You're likely to break your system doing that.

You could add the following mount options to the drive: 'uid=0,gid=46,umask=0007' - this will give read-write access to root and all members of plugdev.
```
/dev/sdb1 /media/outer vfat auto,user,exec,rw,sync,[Color="Red"]uid=0,gid=46,umask=0007[/Color] 0 0
```

---

### Post by paulderol on 2008-06-20
who is the "owner" of the drive? if it is root, then that would explain this, and i'm not sure if you can make it go back and forth [linux/windows] while retaining ownership permissions like that. 

perhaps chown will fix this problem? 

or perhaps you're not part of the "usb" group in your permissions settings?

---

### Post by Pjotr123 on 2008-06-20
It's FAT32, so it *has* no owner. Only NTFS has an owner (and the various Linux formats ofcourse)

This is really a "missing stop code" issue, as I said in my earlier post.

---

### Post by chrisccoulson on 2008-06-20
> **Pjotr123 said:**
> It's FAT32, so it *has* no owner. Only NTFS has an owner (and the various Linux formats ofcourse)

This is really a "missing stop code" issue, as I said in my earlier post.

No, that is wrong. The ownership and permissions of all the files on a FAT32 filesystem are defined at mount-time by the mount options uid, gid and umask. This is exactly the same as how the permissions and ownership for NTFS partitions are defined. Neither FAT32 or NTFS understand *nix file permissions and ownership. 

Please read 'man mount' for an explanation of the mount options.

The issue here is because the OP hasn't specified uid, gid or umask. Without that, mount defaults to uid=0,gid=0,umask=0022 which means that only the root user can write to it. He's already stated that he can write to it as root.

If it was uncleanly unmounted (or a 'missing stop code' as you put it) and the filesystem was panic-ing, then it would get mounted read only and the user would see a message telling them it was a read-only filesystem, regardless of whether it was root or a normal user trying to write to it.

This is purely a permissions problem. The OP just needs to specify a uid,gid and umask value at mount-time

---

### Post by bertwagner on 2008-06-20
> **chrisccoulson said:**
> If you can write as root, then it's a permissions issue as opposed to a filesystem issue. Don't play with UDEV rules to try and fix this unless you really know what you're doing with them. You're likely to break your system doing that.

You could add the following mount options to the drive: 'uid=0,gid=46,umask=0007' - this will give read-write access to root and all members of plugdev.
```
/dev/sdb1 /media/outer vfat auto,user,exec,rw,sync,[Color="Red"]uid=0,gid=46,umask=0007[/Color] 0 0
```

Thanks a lot Chris, that did it!

---

### Post by sisco311 on 2008-06-20
> **Pjotr123 said:**
> It's FAT32, so it *has* no owner. Only NTFS has an owner (and the various Linux formats ofcourse)

This is really a "missing stop code" issue, as I said in my earlier post.

You can set up the (*fake*) permissions when you mount the fat or ntfs partition.

The options are:
uid = user id
gid = group id
umask = user mask
[COLOR=Red]
uid=0 [COLOR=Black]--> owner = root[/COLOR]
gid=46 [COLOR=Black] --> group = plugdev[/COLOR]
umask=0007[COLOR=Black] --> permissions = 0770 (rwxrwx---)  [/COLOR][/COLOR]

The ntfs-3g driver can't handle the permissions on ntfs partitions.
You can't change the permissions on the partition when is mounted.

---

### Post by ajgreeny on 2008-06-20
Just out of interest, why did you need to add a line to your fstab file to get the drive to mount at boot.  USB drives, whether flash drives or external hard drives usually auto mount (if plugged in and switched on, in the case of hard drives) at boot time with no problem.  If it was plugged in swithced on and you booted, I think it would mount and you would be able to write to it without doing anything else.

---

### Post by Pjotr123 on 2008-06-20
> **chrisccoulson said:**
> No, that is wrong. The ownership and permissions of all the files on a FAT32 filesystem are defined at mount-time by the mount options uid, gid and umask. This is exactly the same as how the permissions and ownership for NTFS partitions are defined. Neither FAT32 or NTFS understand *nix file permissions and ownership. 

Please read 'man mount' for an explanation of the mount options.

The issue here is because the OP hasn't specified uid, gid or umask. Without that, mount defaults to uid=0,gid=0,umask=0022 which means that only the root user can write to it. He's already stated that he can write to it as root.

If it was uncleanly unmounted (or a 'missing stop code' as you put it) and the filesystem was panic-ing, then it would get mounted read only and the user would see a message telling them it was a read-only filesystem, regardless of whether it was root or a normal user trying to write to it.

This is purely a permissions problem. The OP just needs to specify a uid,gid and umask value at mount-time

Never too old to learn!  :-)

---

