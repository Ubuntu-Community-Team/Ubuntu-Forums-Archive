---
title: "compilers(lazarus, free pascal, codeblocks) in ubuntu!"
date: 2012-06-28
forum: Programming Talk
---

### Post by thanhbuu on 2012-06-28
when I debug the program language (lazarus, free pascal or Codeblocks) I always have to save to home and run it there (in Windows I often put it in some driver but ubuntu is not like that. Can you suggest any solution so that I can save on another driver, too? Thanks you for reading and I hope you give me some solution! :)

---

### Post by oldos2er on 2012-06-29
Moved to Programming Talk.

---

### Post by thanhbuu on 2012-06-30
Somebody helps me please!

---

### Post by Zugzwang on 2012-07-01
Dear OP, let me start by telling that your post is very hard to understand due to grammar, word (driver <-> drive, what does "program language" mean in this context), and factual errors (CodeBlocks is not a compiler, but an IDE). which is probably the reason why you didn't get an answer yet.

So here is the question that I interpreted from your post, and I hope that it is the one you are asking, because I'll answer this below. You have the problem that you can compile and execute programs only from your home directory, but not from some other path in the file system (e.g., one corresponding to a pen drive).

This has to do with the type of file system. If you run "ls -la" in some dirctory, you will see the attributes of a file. In order to execute it, the executable (x) flag must be set. Volumes with the FAT file system (typically used by USB pen drives) do not support this flag, so they are set automatically. So you can't execute a program from there. Windows doesn't have this flag, so there, things still work.

What you can do is to mount your drive such that the executable bit is always set. I've read somewhere else that a command such as
```

mount /media/yourPenDrive -remount,exec

```
can do this.

---

### Post by thanhbuu on 2012-07-03
Yes, that's what I mean, but I want to mount on /media/DATA1 (it's NTFS) but this show the error 
```

mount: invalid option -- 'e'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```
What can I do next ? Thank you!:confused:

---

### Post by Zugzwang on 2012-07-03
[QUOTE=thanhbuu;12072012]Yes, that's what I mean, but I want to mount on /media/DATA1 (it's NTFS) but this show the error 
[...]
[/CODE]

Ok, technically "sudo mount -o remount,exec /media/DATA1" should work then, but it doesn't for me - all files still do not have the executable flag. Anybody else has a clue?

---

### Post by thanhbuu on 2012-07-04
Somebody please help us! :(

---

### Post by ofnuts on 2012-07-04
> **thanhbuu said:**
> Somebody please help us! :(Google for "linux mount ntfs executable"... hundreds of answers.

---

