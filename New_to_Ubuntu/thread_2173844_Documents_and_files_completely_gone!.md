---
title: "Documents and files completely gone!"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by barakat2 on 2013-09-11
I have encountered that issue related to disappearing launcher, dash, places etc.
Upon forums searches, I did unity reset by trying several commands posted in this regard; however, I got back my dash, launcher and places, BUT
All documents and files simply gone, seems like I have installed fresh copy of ubuntu (13.04).
Apps are there, but all configurations has been reset also.
For example, Virtualbox is there, but my virtual machine simply vanished and I just trying to find out WHERE IS MY .VHD file?
Please help and advice.
Thanks

---

### Post by newb85 on 2013-09-11
Sounds to me like there's an issue with your /home directory. When you installed, did you put it on a separate partition? If so, are you sure that partition is mounted now? If not, what is the result of
```
 ls -al /home 
```

---

### Post by barakat2 on 2013-09-11
> **newb85 said:**
> Sounds to me like there's an issue with your /home directory. When you installed, did you put it on a separate partition? If so, are you sure that partition is mounted now? If not, what is the result of
```
 ls -al /home 
```

Installation was using entire disk (single partition, single admin user)
Yes, mounted partition, system is up and I'm using it right now.

well, it seems like I'm pointing to fresh /home directory (only installed apps as it is).
That's why I'm wondering, playing with unity is only affecting appearance no more.
Is it possible that, I'm having two different /home directories on the same partition (the entire disk is used)?
I really confused, all what I'm looking for just to recover my VHD file no more, it is my works machine.

---

### Post by barakat2 on 2013-09-11
ls -al /home code results in:

total 12
drwxr-xr-x 3 root
drwxr-xr-x 23 root
drwxr-xr-x 22 barakat (my username)

---

### Post by Bashing-om on 2013-09-11
barakat2; Hi !

To help and move things along a bit; in answer to your question:
> 
Is it possible that, I'm having two different /home directories on the same partition (the entire disk is used)?
I really confused,

Terminal codes:
```

cd / ##changes the present working directory to the top directory
ls -la ##gives a listing off all subdirectories under that top directory "/" (root)
cd ## to return to the '/home' directory
##then:
sudo fdisk -lu ##shows how the hard disk is layed out ..

```
If all is in order, we can address hunting up a particular file.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by ibarnon on 2013-10-04
I just hit the same problem. This is an** EXTREMELY SERIOUS ISSUE**. Never encountered this before and I've been using ubuntu since version 7. So far I don't see any resolution and at least 3 people have experienced this problem.

Seems like an identical problem posted by alreston 
[http://ubuntuforums.org/showthread.php?t=2155215](http://ubuntuforums.org/showthread.php?t=2155215)

---

