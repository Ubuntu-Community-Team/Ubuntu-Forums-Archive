---
title: "acsess windows hard drive"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by ktodac3298 on 2008-07-31
i had windoxs xp running and it crashed i put in ubuntu as a live cd and i want to access the files (i noe that they are there as i saw them in puppy linux) but ubuntu says i dont have the permissions all i want to do is copy the files to an external hard drive how do i get this permission

---

### Post by shanepardue on 2008-07-31
When you open a terminal and type "gksudo nautilus" then navigate to the windows drive, do you have permissions that way?

---

### Post by halitech on 2008-07-31
are you getting the no permission eror when you are trying to navigate to where the files are or when you try to copy them to the external drive?

---

### Post by ktodac3298 on 2008-07-31
when i try to open where the files are

---

### Post by halitech on 2008-07-31
open a terminal and run
```
gksu nautilus
``` and it should allow you to read the drive, it may be mounted as no permissions at all

---

### Post by ktodac3298 on 2008-07-31
i get this response 

(nautilus:6534): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by shanepardue on 2008-07-31
> **ktodac3298 said:**
> i get this response 

(nautilus:6534): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Do you not see a window pop up with files and folders showing? That's our focus.

---

### Post by ktodac3298 on 2008-07-31
ya but the folder is empty

---

### Post by shanepardue on 2008-07-31
> **ktodac3298 said:**
> ya but the folder is empty
Try navigating to the folder you need permissions for. The command you are typing simply opens the file manager (nautilus) with all permissions you will need.

---

### Post by halitech on 2008-08-01
the folder is empty cause it opens in the folder /Root which normally will be empty. Just browse to where you need to go and the files should (hopefully) show up

---

