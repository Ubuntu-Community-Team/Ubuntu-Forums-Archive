---
title: "Problems Running Fortran 95 programs off flash drive"
date: 2011-01-25
forum: Programming Talk
---

### Post by Kaneda on 2011-01-25
I've just started a Fortran class, and I do a lot of my work on the windows machines at the school, but it's nice to work on my ubuntu machine from time to time as well.

After I compile a program and try running it with:
```
./ast2
```

I get the following error:
```
bash: ./ast2: Permission denied
```

So, I tried changing the permissions:
```
chmod a+x ast2
```

But, no luck.  It still didn't work.  (sudo didn't work, either)  However, the file is on a flash drive, so I copied it to my home folder.  I tried running it again there, and it didn't work, but then I changed the permissions there and ran again, and it worked.

I even tried going in through the GUI file manager and changing the permissions, but when I check the "Allow executing file as program" box, it just unchecks itself right after.

Output of ls -l, by the way is:
```
$ ls -l
total 73352
-rw-r--r-- 1 zen zen      223 2011-01-20 16:53 a1out.txt
-rwxr-xr-x 1 zen zen   875078 2011-01-20 16:53 ast1.exe
-rw-r--r-- 1 zen zen     2436 2011-01-24 18:11 ast1.f95
-rw-r--r-- 1 zen zen     2592 2011-01-20 16:53 ast1.f95~
-rw-r--r-- 1 zen zen   138894 2011-01-19 17:13 ast1hnd.pdf
-rw-r--r-- 1 zen zen    11751 2011-01-25 11:35 ast2
-rwxr-xr-x 1 zen zen   878809 2011-01-24 18:08 ast2.exe
-rw-r--r-- 1 zen zen     2127 2011-01-24 18:07 ast2.f95
-rw-r--r-- 1 zen zen     2120 2011-01-24 18:05 ast2.f95~

```
(The .exe files are from when I compiled the programs on a windows machine)

So, here's my question:  How do I get it so I can run the file off of the flash drive?

And a second question: Assuming I get to where I can run off the flash drive, it's still kind of annoying to have to change the permissions for each program I write before I can execute it.  Is there anyway I can automate the process or get around it?

Thanks a lot!

---

### Post by Some Penguin on 2011-01-25
You're probably having the USB drive mounted as noexec.

---

### Post by Kaneda on 2011-01-25
Here's my /etc/fstab
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=badd1fab-2e69-41d1-a48b-f7111323065b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4008a6b9-fe01-4bb9-b782-095038fde496 none            swap    sw              0       0

```

and here's my mtab:
```
$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/zen/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=zen 0 0
/dev/sdc /media/SD vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush 0 0
/dev/sde /media/40A2-2ABC vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush 0 0

```
The drive I'm trying to use is the /media/40A2-2ABC one... I'm not sure exactly what I need to change, and I don't want to just randomly go in and mess with stuff and end up not being able to boot my machine.

Help?

Thanks!

---

### Post by Queue29 on 2011-01-25
Are you recompiling after plugging into the linux machine? Code compiled for Windows won't run on your Ubuntu machine. And if you are successfully re-compiling, the compiler should be setting the correct execute bits automatically.

---

### Post by Some Penguin on 2011-01-25
You're using VFAT.  Read

[http://www.mail-archive.com/cooker@linux-mandrake.com/msg75400.html](http://www.mail-archive.com/cooker@linux-mandrake.com/msg75400.html)

---

### Post by Kaneda on 2011-01-25
> **Queue29]Are you recompiling after plugging into the linux machine? Code compiled for Windows won't run on your Ubuntu machine. And if you are successfully re-compiling, the compiler should be setting the correct execute bits automatically.[/QUOTE]
Well, I compiled it on the usb drive using linux.  The .exe files I compiled in windows obviously don't work, and when I moved the file I compiled in linux from the usb drive to the HDD and changed the permissions, it ran okay.  I'm guessing that when I compiled it, it probably wasn't able to set the permissions right because of the noexec/showexec status on the drive, and that when I get that sorted out, it won't be a problem.

[QUOTE=Some Penguin said:**
> You're using VFAT.  Read

[http://www.mail-archive.com/cooker@linux-mandrake.com/msg75400.html](http://www.mail-archive.com/cooker@linux-mandrake.com/msg75400.html)
Thanks for all your input, Penguin! :D

So for vfat, showexec = noexec.  

I went in and edited the mtab file to change showexec to exec and then rebooted my machine... but when I mounted my usb drive back up, it just automatically set it to showexec again.  How do I set things up so the default is to allow executables?

---

### Post by Kaneda on 2011-01-25
So!  I solved the problem by setting a manual entry for the usb drive by its uuid in fstab.  Here's what I put:
```
/dev/disk/by-uuid/40A2-2ABC	/media/PNY	vfat	users,exec,noauto,defaults,umask=000	0	0
```
I'm still really new to fstab, though, so if anyone has any comments about this fix (like if there's anything I should add and/or take out), I'd really appreciate it!

But!  With this fix, I can compile and run my fortran programs from the usb drive. :D

---

