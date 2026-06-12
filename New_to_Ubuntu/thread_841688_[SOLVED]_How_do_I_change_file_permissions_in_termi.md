---
title: "[SOLVED] How do I change file permissions in terminal?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Lord Xeb on 2008-06-26
My brother wants to add brushs to gimp 2.0 but he can't since the permissions of gimp is root. How do I change the permissions over to him?

---

### Post by zmjjmz on 2008-06-26
It'd be safer to just add the brushes with sudo.
Or sudo su, if it's going to be a lot of commands.

---

### Post by cardinals_fan on 2008-06-26
```
man chmod
man chown
```

---

### Post by FuturePilot on 2008-06-26
I think it would be safer, not to mention easier, to put them in ~/.gimp-2.4/brushes/

---

### Post by Lord Xeb on 2008-06-26
No, really? It would be nice if he could be the permissions are in root! I do not understand the damn man files since they really do explain things in lamins. Besides I fixed it with Ubuntu Tweak and adding a script cadd "Browse as root"

---

### Post by cardinals_fan on 2008-06-26
chown changes file owner, chmod changes file permissions

---

### Post by schaefer.dj on 2008-06-26
chown -R *newowner* *file or directory*

this will change the owner to the *newowner* user for everything in the *file or directory*. note, don't use the asterisks.

---

### Post by Sinkingships7 on 2008-06-26
> **Lord Xeb said:**
> No, really? It would be nice if he could be the permissions are in root!

~ means your home directory. If you open nautilus and press ctrl+h, it'll show you hidden files and folders. Go to the folder that says .gimp2.4 and go to the 'brushes' subdirectory. He has permission to put them there, and they'll show up in GIMP, but only for him.

---

### Post by Lord Xeb on 2008-06-26
This is not what I mean... It is in /usr/share/gimp or something like that. I got it so  I don't need any help.

---

