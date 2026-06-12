---
title: "write permission denied on mount"
date: 2014-08-24
forum: New to Ubuntu
---

### Post by fibberts on 2014-08-24
I made an ext2 partition which I want to mount on startup with fstab.  Here's the fstab I'm using:
```

[SIZE=2]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7e2b9034-442a-4156-aebc-c6763d09d154 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c3ca5e55-1c25-4a58-9cd1-24d2f825f38e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=daf4986b-d7e6-481b-992c-8e660030f44d       /media/pocket   ext2    user,rw,auto      0       0[/SIZE]

```
It mounts without error but if I try
```

[SIZE=2]peter@compy:~$ **touch /media/pocket/a.txt**
touch: cannot touch `/media/pocket/a.txt': Permission denied
peter@compy:~$ **ls -la /media/**
total 16
drwxr-xr-x  4 root root 4096 Aug 24 01:03 .
drwxr-xr-x 24 root root 4096 Aug 23 15:57 ..
lrwxrwxrwx  1 root root    7 Aug  9 14:51 floppy -> floppy0
drwxr-xr-x  2 root root 4096 Aug  9 14:51 floppy0
drwxr-xr-x  3 root root 4096 Aug 23 22:49 pocket[/SIZE]

```
Permission denied?! :evil:

I'd like to be able to write/modify files on the partition without being root.
Is there some way to give ownership of the mount to the 'peter' user, or to make the share publicly available?
I could probably use some combination of chown and chmod to accomplish this after boot but I want it to be set up properly immediately after boot.  How can I make my dreams come true?

---

### Post by deadflowr on 2014-08-24
You should only need to chmod(own) once, since the partition will already be mounted at boot.
At least that how it works for me...

---

### Post by Bashing-om on 2014-08-24
fibberts; Hello;

Simpler really is better,
As presently all you want is user access to the partition, all that is required at this time is to change the access from root to "you".
```

sudo chown peter:peter /media/pocket

```
Also in line with this "simpler" ideal; Do you really have and use a floppy drive  (/dev/fd0) that is reflected in the fstab file ?
If there is no need of 'fd0' you can disable the device in bios and make a significant decrease in the boot-up time. Then remove the reference in the /etc/fstab file.
If you require advanced access to 'media/pocket' say in using the terminal .. then we can further discuss editing "/etc/fstab" to mount that partition at boot.

[INDENT][INDENT]keep it simple
[/INDENT][/INDENT]

---

### Post by fibberts on 2014-08-24
```
sudo chown peter:peter /media/pocket
```
This worked perfectly and persisted after a reboot exactly as I wanted!
Thanks, deadflowr and Bashing-om :D!!

> **Bashing-om said:**
> 
If there is no need of 'fd0' you can disable the device in bios and make  a significant decrease in the boot-up time. Then remove the reference  in the /etc/fstab file.

Done.  Boot time is down to 32 seconds.  Nice!

> **Bashing-om said:**
> 
If you require advanced access to 'media/pocket' say in using the  terminal .. then we can further discuss editing "/etc/fstab" to mount  that partition at boot.

I'm trying to turn this machine into a server, so I do intend to mostly access this mount over ssh from other computers.
Is there some different (better) way I should have set up my fstab?

---

### Post by deadflowr on 2014-08-24
> [COLOR=#000000]Is there some different (better) way I should have set up my fstab?[/COLOR]

Your mount point can really be anywhere you want, and not restricted to /media folder or /mnt, or even /srv(which most people would normally use.)

I've actually mounted partitions into a folder within my home folder.
Simply so I have quicker access, as the folder is listed with my home folders.
But that's just me, you can mount 'em wherever you like.

---

### Post by Bashing-om on 2014-08-24
fibberts; Pleased

Things are working out for you.
As to :
> 
I'm trying to turn this machine into a server, so I do intend to mostly access this mount over ssh from other computers.
Is there some different (better) way I should have set up my fstab?

Nope, not really, BUT each use case is different. Depending on 'how' 'you' want to do something. Where you set the mount point has a lot to do with how the file manager (GUI) relates in an autonomous manner. The CLI or SSH will not care. But you must know what that mount point is and be able to tell the system . And when you manually mount a file system it is on you to also manually UN-mount that file system. Even though ubuntu is  journaled file system by default, a failure to properly Unmount can and does lead to file system failures.

[INDENT][INDENT]a never ending process is learning
[/INDENT][/INDENT]

---

