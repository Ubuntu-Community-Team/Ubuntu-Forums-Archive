---
title: "How do I point to another drive?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by y0diggity on 2008-05-11
I have 7.10 installed. I also have another drive in my system that is 250gb and is still formatted in NTFS that I use to put stuff on. It doesn't have an OS on it, it's just storage.
My problem is that I have an application that creates files and I'd like it to use this drive as its output drive. 
[LIST]
[*]How do I automatically mount this drive at startup?
[/LIST]
[LIST]
[*]Also, what path do I use to point to it? It's called "Fat Boy" and it mounts in /media but if I try to cd /media/Fat Boy, I get told it doesn't exist. Is it because of the space in the name?
[/LIST]
[LIST]
[*]If I wanted to format this drive to a regular Linux filesystem, how would I go about that?
[/LIST]Sorry for all the questions, thanks for your time.

---

### Post by dondad on 2008-05-11
> **y0diggity said:**
> I have 7.10 installed. I also have another drive in my system that is 250gb and is still formatted in NTFS that I use to put stuff on. It doesn't have an OS on it, it's just storage.
My problem is that I have an application that creates files and I'd like it to use this drive as its output drive. 
[LIST]
[*]How do I automatically mount this drive at startup?
[/LIST]
[LIST]
[*]Also, what path do I use to point to it? It's called "Fat Boy" and it mounts in /media but if I try to cd /media/Fat Boy, I get told it doesn't exist. Is it because of the space in the name?
[/LIST]
[LIST]
[*]If I wanted to format this drive to a regular Linux filesystem, how would I go about that?
[/LIST]Sorry for all the questions, thanks for your time.

If you want to reformat it to a linux filesystem, run gparted and use that to format the drive. You might want to do this from the ubuntu CD because you cannot format a drive while it is mounted.

---

### Post by Aearenda on 2008-05-11
It should be automatically mounted. You could try cd /media/Fat\ Boy to make the space in the name work - or cd "/media/Fat Boy".

---

### Post by freebeer on 2008-05-11
As for accessing it, yes, the space is causing the problem.  You can get around that by "escaping" the space.  (This works for all files with spaces in them, btw.)

So if you wanted to cd to that drive, you would type:

```

cd /media/Fat\ Boy

```

The "\" is an escape character, and tells the command line interpreter that the next character is part of the name.

---

### Post by ejpyle on 2008-05-11
You need to create another directory under disk with that name "fat boy"

the spacing is not an issue...i have a drive called "Go Drive" and runs under NTFS and it works perfect of course I am not in terminal changing directories.....

anyway once u create that directory you will need to edit your /ETC/FSTAB file so it mounts when u boot up.

---

### Post by y0diggity on 2008-05-11
Thanks. The "escape" method worked. Now I've reformatted the drive. I've gone with a fat32 format though, because I would still like Windows compatibility in the event of sharing it on my network.
It still doesn't mount on startup and I'm not sure about fstab. I do have a link to a site that is supposed to go over this process, but if there's a simpler way, I'd appreciate it. My goal now is to have it mount at startup for all users that log into this computer and be accessible to them.

---

### Post by snooptodd on 2008-05-11
if you are using mount to "mount" the drive after startup then you already have figgured out everything you need for the fstab entry.

lets say that your mount command looks like this:
```
mount -t msdos /dev/hdb2 /meda/shared
```

your fstab entry would look like this

```

/dev/hdb2     /media/shared     msdos        user,auto
^block device ^mount point      ^filesystem  ^options: user mount,auto mount
```
man fstab is your friend

---

