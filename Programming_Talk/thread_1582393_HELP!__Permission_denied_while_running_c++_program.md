---
title: "HELP!  Permission denied while running c++ program"
date: 2010-09-26
forum: Programming Talk
---

### Post by josephellengar on 2010-09-26
Hello.  My c++ program compiled well and is syntactically correct, but I get the following error when I try to run it:

```

ross@ross-laptop:~$ cd flash/current/CS260/assignment2/
ross@ross-laptop:~/flash/current/CS260/assignment2$ g++ assgn2RH.cpp assgn2RHFns.cpp -o assgn2exec
ross@ross-laptop:~/flash/current/CS260/assignment2$ ls        
Debug  Release  assgn2RH.cpp  assgn2RHFns.cpp  assgn2RHFns.h  assgn2exec
ross@ross-laptop:~/flash/current/CS260/assignment2$ ./assgn2exec
bash: ./assgn2exec: Permission denied
ross@ross-laptop:~/flash/current/CS260/assignment2$ sudo ./assgn2exec
[sudo] password for ross: 
sudo: unable to execute ./assgn2exec: Permission denied
ross@ross-laptop:~/flash/current/CS260/assignment2$ sudo chmod a+x assgn2exec
ross@ross-laptop:~/flash/current/CS260/assignment2$ ./assgn2exec
bash: ./assgn2exec: Permission denied

```

I also (unsuccessfully) tried to run it with sudo su.  Does anybody have any idea what might be happening here?

---

### Post by GeneralZod on 2010-09-26
Show the output of 

```

ls -l

```

instead of just ls.  Also, is this running from some kind of external drive? What filesystem is it?

---

### Post by josephellengar on 2010-09-26
Ok, I just took your recommendation and moved my file from an external drive to my regular drive.  Is it normal that putting code on an external drive causes problems?  Because I have a huge number of external drives connected to my computer that I always used when programming in java.  But now the program does work.  My external drive is fat32 filesystem.  Another is ntfs.  So, what do you think?  You seem to have solved that problem faster than my professor.

---

### Post by GeneralZod on 2010-09-26
Now that I think of it, being mounted "noexec" might be more likely than the filesystem.  Can you post the output of 

```

cat /etc/mtab

```

?

---

### Post by josephellengar on 2010-09-26
> **GeneralZod said:**
> Now that I think of it, being mounted "noexec" might be more likely than the filesystem.  Can you post the output of 

```

cat /etc/mtab

```

?

Shouldn't be mounted noexec.  I think I fixed that.  But here it is.  Thanks for your help.

```



/dev/sda5 / ext4 rw,errors=remount-ro,discard 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /tmp tmpfs rw,noatime 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
tmpfs /var/tmp tmpfs rw,noatime 0 0
tmpfs /var/log tmpfs rw,noatime 0 0
tmpfs /var/log/apt tmpfs rw,noatime 0 0
/dev/sdb1 /home/ross/storage fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ross/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ross 0 0
/dev/sdc1 /home/ross/flash vfat rw,noexec,nosuid,nodev,iocharset=utf8,umask=000,user=ross 0 0


```

Wow.  You were right.  There it is.  I was running off of the /dev/sdc1 entry.  Will just removing noexec fix the problem?

---

### Post by The Cog on 2010-09-26
The danger of removing the noexec setting is that FAT and NTFS don't have the ability to store the executable flag, so it is a mount option that applies to all files. So removing noexec would make every file on the drive executable, which is probably not really good practice.

---

### Post by josephellengar on 2010-09-26
> **The Cog said:**
> The danger of removing the noexec setting is that FAT and NTFS don't have the ability to store the executable flag, so it is a mount option that applies to all files. So removing noexec would make every file on the drive executable, which is probably not really good practice.

But it would solve my problem, right?  The convenience factor might be worth it because I edit the same code on the windows and linux parts of my computer, carry it around on my flash drive, etc.

---

### Post by The Cog on 2010-09-26
Yes I think it would solve your problem. Unfortunately, I don't know where to change how flash drives get mounted. It's probably not a good idea to change that anyway. You can probably use the mount command to remount it the way you want.

---

### Post by josephellengar on 2010-09-26
> **The Cog said:**
> Yes I think it would solve your problem. Unfortunately, I don't know where to change how flash drives get mounted. It's probably not a good idea to change that anyway. You can probably use the mount command to remount it the way you want.

You can change it in the /etc/fstab file.

---

