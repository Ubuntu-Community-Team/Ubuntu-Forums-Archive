---
title: "Permission denied - Trying to access an ntfs drive 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by spookyct on 2008-04-26
Hey Guys,

I just upgraded to 8.04, and now I can not access my ntfs drive.  Any ideas?  It says "Permission Denied".

---

### Post by Joeb454 on 2008-04-26
Have you cleanly shutdown the NTFS drive :) and if you do it through the GUI - it should prompt you to enter your password

---

### Post by grannyw on 2008-04-26
dont mind

---

### Post by spookyct on 2008-04-26
> **Joeb454 said:**
> Have you cleanly shutdown the NTFS drive :) and if you do it through the GUI - it should prompt you to enter your password

Cleanly shutdown?  Can I have directions for this?  Windows is not installed on the drive, it is just media.

---

### Post by spookyct on 2008-04-26
I have restarted Kubuntu, and I still get the same result.

When I try to open sda1 in Dolphin, I get a "Permissions Denied" error on the bottom of the GUI.

---

### Post by TeoBigusGeekus on 2008-04-26
Have you installed ntfs-3g and ntfs-config through synaptic?

---

### Post by Joeb454 on 2008-04-26
Sorry, cleanly unmounted the drive I meant :)

And I'm not 100% familiar with Kubuntu, I'll pass the thread on to some other members of the beginners team :)

---

### Post by spookyct on 2008-04-26
Yes to ntfs-3g and config, that did not help.

---

### Post by spookyct on 2008-04-26
Got it to work by executing...

```
 sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
```

---

### Post by Lux Perpetua on 2008-04-26
Could it be that your NTFS drive is owned by root, and root isn't letting you in? 

Type **stat <mount point>** in a terminal, where <mount point> is wherever your drive is mounted. Post the output here. 

You could also try **sudo su** in a terminal (become root temporarily), and then try to access the directory. Make sure to **exit** after you find out whether it works.

**Edit:** didn't see your post. Glad you figured it out.

---

### Post by TeoBigusGeekus on 2008-04-26
You should go to applications->system tools->ntfs configuration
Then choose your partition and check all the permissions' buttons.

---

### Post by itismike on 2011-09-07
Sorry to resurrect this ancient thread but I'm stumped by reading an NTFS drive with some archived Windows files on it. My system is a fully updated Ubuntu Server 10.04 LTS.

The goal of my efforts is to move the files from this NTFS drive to a larger drive. I've mounted it via UUID and am getting 'Permission Denied' errors when trying to [FONT="Courier New"]cp[/FONT] or [FONT="Courier New"]mv[/FONT] files. I can write to the drive, and can rename the files I'm trying to copy, but cannot move, copy, or read them. 

As a test I attempted to cat a simple .log file:```
$ sudo cat WS-FTP.LOG 
cat: WS-FTP.LOG: Permission denied

```However this is the same file that I am able to rename. Here are the file permissions:```
$ ls -aFl WS*
-rwxrwxrwx 1 root root 864 2005-01-23 21:54 WS-FTP.LOG*
```

Thinking that 'root' was a different 'root' than my current 'root' (can that happen?), I [FONT="Courier New"]chown[/FONT]'d it:
```
$ sudo chown root:root WS-FTP.LOG
```Still the same errors. Now attempting to [FONT="Courier New"]chown[/FONT] it to my user account:```

$ sudo chown michael:michael WS-FTP.LOG 
$ cat WS-FTP.LOG 
cat: WS-FTP.LOG: Permission denied
$ ls -aFl WS-FTP.LOG 
-rwxrwxrwx 1 root root 864 2005-01-23 21:54 WS-FTP.LOG*

```It is ignoring my efforts to chown or chmod the file, but not returning any error. :confused:

I've tried mounting it as 'ntfs' and 'ntfs-3g' but it doesn't make a difference. This is my manual 'mount' command line:
```
sudo mount -t ntfs-3g UUID="11891C1DD5454341" /media/sda2
```
I've also mounted it via fstab:```
UUID=11891C1DD5454341 /media/sda2 ntfs-3g defaults 0 0
```

The result of the above mount commands is:```
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=1024)
```which looks fine to me. What am I missing?

---

