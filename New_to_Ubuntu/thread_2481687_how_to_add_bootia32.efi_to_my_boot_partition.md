---
title: "how to add bootia32.efi to my boot partition?"
date: 2022-12-06
forum: New to Ubuntu
---

### Post by bagle2 on 2022-12-06
HI,

New to the forums.
Been running linux for a couple of years - so still a newbie.
I am attempting to install Ubuntu 64 bit ( 22.10 ) on my Linx 1020 Windows tablet ( intel atom, 2gb ram, 32gb EMMC).

These belong to a long line of tablets which are 64 bit arch, but 32 bit uefi.

Installing is not a problem, as I can manually add ''bootia32,efi'' to the bootable flash drive.

But once installed, Ubuntu wont boot
I am guessing the 'bootia32,file' does not get included in the ubuntu installation?

So,,, How do I add this file to the EFI/BOOT partition of the installed ubuntu.?
And is this all I need to do to get it to boot?
I have booted back into the ubuntu LIve CD, but I cannot get the relevant EFI/BOOT partition to mount as read/write, in order to paste the file into the relevant folder.

Any help would be appreciated

Don

---

### Post by bagle2 on 2022-12-06
o.k- found a ''respun ''iso that works

---

### Post by oldfred on 2022-12-06
I always have trouble mounting from live installer.
Is ESP partition mounted? Usually my dolphin does not mount any ESP I have on other drives.
And from inside my install fstab has it set to no permissions or umask=0077. They used to use defaults, but I think for security they do not want a rogue task to mount it, since it has important boot files.
Live installer has default user as 999 where install's first user is 1000. And FAT32 or NTFS are typically root, but more open permissions, so you can read write.

mount
If mounted unmount (umount)
If not mounted create mount point & manually mount using defaults.

I was able to mount an ESP I have on another drive. I have ESP on every drive, but really only use one.
```
[FONT=monospace][COLOR=#000000]sudo mkdir /media/fred/temp
[/COLOR][/FONT][FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo mount /dev/sda1 /media/fred/temp [/COLOR]
[COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ll /media/fred/temp [/COLOR]
total 16 
drwxr-xr-x   4 root root 4096 Dec 31  1969  [COLOR=#5454ff]**.**[/COLOR][COLOR=#000000]/ [/COLOR]
drwxr-x---+ 10 root root 4096 Dec  5 03:18  [COLOR=#5454ff]**..**[/COLOR][COLOR=#000000]/ [/COLOR]
drwxr-xr-x   7 root root 4096 Aug 30  2021  [COLOR=#5454ff]**EFI**[/COLOR][COLOR=#000000]/ [/COLOR]
drwxr-xr-x   2 root root 4096 Aug 10 16:27 [COLOR=#5454ff]**'System Volume Information'**[/COLOR][COLOR=#000000]/[/COLOR]

[/FONT]
```

---

### Post by mIk3_08 on 2022-12-07
> **bagle2 said:**
> o.k- found a ''respun ''iso that works
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by bagle2 on 2022-12-08
THank you for your reply.

Cheers

Don

---

