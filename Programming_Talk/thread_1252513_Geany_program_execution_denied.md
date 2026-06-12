---
title: "Geany: program execution denied"
date: 2009-08-28
forum: Programming Talk
---

### Post by abrari on 2009-08-28
Hi all...

I wrote a very simple C program using Geany. I saved the source file outside my home directory (on windows' partition, mounted on /media/sda2, it's NTFS). **I can compile the source and build it**. But when I try to execute it, the output window (the black one) says something like permission denied. 

```

./geany_run_script.sh: 5: ./blahblah: Permission denied
```

Even when I execute it using terminal (sudo ./blahblah) it says the same thing.

```

bash: ./blahblah: Permission denied
```

But when I move those files to my home directory, I can execute it like a charm.

So, what permission of which file/directory I have to change? The binary file of the program (blahblah) already has -rwxrwxrwx permission.

---

### Post by x33a on 2009-08-28
try adding exec to mount options

---

### Post by abrari on 2009-08-28
How to do that?
The partition is mounted automatically on startup (using pysdm).

---

### Post by x33a on 2009-08-29
i haven't used pysdm, so don't know how it manages partitions.

could you post the output of 
```
cat /etc/fstab
```

---

### Post by abrari on 2009-08-29
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                                   0  0  
# / was on /dev/sda6 during installation
UUID=df5a169d-52ba-4440-b335-e5f6c91ff511  /              ext3         relatime,errors=remount-ro                                 0  1  
# swap was on /dev/sda7 during installation
UUID=d0626113-4bfd-4a1c-87e2-cf9602cd76c9  none           swap         sw                                                         0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                                      0  0  
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,group,users,umask=000,user,owner,uid=abrari  0  0 

I believe that adding option "exec" would solve the problem. But, how?

On pysdm, I can specify mounting options. But, not all of it worked.
There is an option "Permit execution of binary" on it (and already checked). But pysdm seems to just ignore it. A pysdm bug?

---

### Post by abhilashm86 on 2009-08-30
> **abrari said:**
> Hi all...

I wrote a very simple C program using Geany. I saved the source file outside my home directory (on windows' partition, mounted on /media/sda2, it's NTFS). **I can compile the source and build it**. But when I try to execute it, the output window (the black one) says something like permission denied. 

```

./geany_run_script.sh: 5: ./blahblah: Permission denied
```

Even when I execute it using terminal (sudo ./blahblah) it says the same thing.

```

bash: ./blahblah: Permission denied
```

But when I move those files to my home directory, I can execute it like a charm.

So, what permission of which file/directory I have to change? The binary file of the program (blahblah) already has -rwxrwxrwx permission.

can you output the status of the file attributes? is it executable by user?
normally it should be like this this....
```
abhilash@abhilash:~$ ls -l cp2
-rwxr-xr-x 1 abhilash abhilash 9467 2009-07-22 08:39 cp2
abhilash@abhilash:~$
```
you can see -rwx, meaning this file is an executable, check this and change your file to executable and try:) good luck

---

### Post by soltanis on 2009-08-30
NTFS does not have permissions the same way Linux filesystems do; so you must mount the partition with exec in order to be allowed to execute any files from it.

I would add a new entry to /etc/fstab like

```

/dev/whatever /mnt/directory ntfs rw,exec,user,auto,noatime,async 0 0

```

As for automounting, I have no idea :(.

EDIT:
Well I should say I do have an idea; write a script like this:

```

#!/bin/sh
mount -t ntfs -o rw,exec,user,auto,noatime,async /dev/whatever /mnt/directory && echo Filesystem mount ok

```

Ughh, what is the Ubuntu startup directory? Try placing it in /etc/init.d/rc5.d/ ... I think that is the right place (unfortunately, running Fedora right now, I can't really verify it myself -- Fedora has weird directory setups)

---

### Post by xpinguimx on 2012-03-29
Just a hint... It happened to me today when I tried to execute C programs from my pendrive. After I copied them to the HDD, the problem was solved! :)

---

