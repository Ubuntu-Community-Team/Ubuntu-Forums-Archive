---
title: "problem Smart media card access"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Primefalcon on 2008-06-29
Ok I have a problem with my smart media camera card. I don't seem to have any access to it.

I've tried sudoing to change permissions.

under Sudo I can view and look at the pictures on the card, but even then It says I don't have any permission to copy the photo's from the card or anything like that.

I've also tried wiping the card with still no luck

---

### Post by Primefalcon on 2008-06-29
I tried to chmod form the terminal and got this

```
primefalcon@blackbeard:~$ sudo chmod -R 777 /media/disk
[sudo] password for primefalcon: 
chmod: changing permissions of `/media/disk': Read-only file system
chmod: cannot access `/media/disk/100OLYMP': Input/output error
chmod: changing permissions of `/media/disk/*&#9578;*ß\027&#9508;ex.if': Read-only file system
chmod: changing permissions of `/media/disk/\003': Read-only file system
chmod: changing permissions of `/media/disk/ympus di.GIT': Read-only file system
chmod: changing permissions of `/media/disk/ympus op.TIC': Read-only file system
chmod: changing permissions of `/media/disk/l.\001': Read-only file system
chmod: changing permissions of `/media/disk/0:00:00.\030': Read-only file system
chmod: cannot access `/media/disk/\a.\003': Input/output error
chmod: cannot access `/media/disk/\a': Input/output error
chmod: changing permissions of `/media/disk/00\001á\003': Read-only file system
chmod: cannot access `/media/disk/\a': Input/output error
chmod: changing permissions of `/media/disk/00:00': Read-only file system
chmod: changing permissions of `/media/disk/.\003': Read-only file system
chmod: changing permissions of `/media/disk/&#963;': Read-only file system
chmod: changing permissions of `/media/disk/OLYMP.\v': Read-only file system
chmod: changing permissions of `/media/disk/\002': Read-only file system
chmod: changing permissions of `/media/disk/mera inf.o]': Read-only file system
chmod: changing permissions of `/media/disk/ympus di.GIT': Read-only file system
primefalcon@blackbeard:~$ 

```

---

### Post by Primefalcon on 2008-06-29
no idea what do with this dang thing, it was working, I checked it in my wifes xp machine and it's working fine there.....

---

### Post by Primefalcon on 2008-06-29
I cant think of anything else to try

---

### Post by clive littlewood on 2008-06-29
Hi

Simple but have you tried changing permissions by right clicking each file in turn in a file browser

Clive L

---

### Post by Primefalcon on 2008-06-29
Unfortunately, that was the first thing I tried :-(

I even tried gk nautlius to open the window up and then tried it

in just standard mode I couldn't see anything

in gkl sudo I could look, but not copy/ move or anything else

---

### Post by Primefalcon on 2008-06-29
in which gk sudo was no better than just sudo

---

