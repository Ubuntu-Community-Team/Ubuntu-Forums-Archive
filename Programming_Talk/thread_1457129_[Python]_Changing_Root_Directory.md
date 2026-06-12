---
title: "[Python] Changing Root Directory"
date: 2010-04-18
forum: Programming Talk
---

### Post by dodle on 2010-04-18
I've tried using the os.chroot() method to change the root directory, but I get an error:  
[php]import os

os.chroot("/home/dodle/Desktop")
file = open("/myfile", "w")
file.close()[/php]> OSError: [Errno 1] Operation not permitted: '/home/dodle/Desktop'

If I try os.system("chroot /home/dodle/Desktop"):> chroot: cannot change root directory to /home/jordan/Desktop: Operation not permitted

I must be doing something terribly wrong.  

This is what I would like it to be doing:
1) make "/home/dodle/Desktop" a generic/temporary root directory
2) create a file called "myfile" in "/" (/home/dodle/Desktop)

Does anyone know the right way to do this?  Should I not be messing with the chroot command?

---

### Post by Bachstelze on 2010-04-18
Only root can use the chroot()system call (unless you want to dig into user capabilities). What do you want to do, exactly? Using chroot() just to create a file seems overkill.

---

### Post by dodle on 2010-04-18
There's more to it than just writing a file, that was just an example.  I'm trying to write a script that creates md5sums for a deb package.  

The md5sums were turning out like this:```
3d47b8e895a71930bda5d4f3d8fc8589 */home/dodle/Desktop/temp/usr/share/test/executable2
d41d8cd98f00b204e9800998ecf8427e  /home/dodle/Desktop/temp/usr/share/test/new file
6e43dcdd4be5bf300cba7b481e9d745e */home/dodle/Desktop/temp/bin/python script (executable).py
3d47b8e895a71930bda5d4f3d8fc8589 */home/dodle/Desktop/temp/bin/executable1
```
When they needed to look like this:```
3d47b8e895a71930bda5d4f3d8fc8589 */usr/share/test/executable2
d41d8cd98f00b204e9800998ecf8427e  /usr/share/test/new file
6e43dcdd4be5bf300cba7b481e9d745e */bin/python script (executable).py
3d47b8e895a71930bda5d4f3d8fc8589 */bin/executable1
```
I did figure out a way to create them correctly, but it uses split() and join() methods.  It works, but I thought there might be a better way.

---

### Post by ssam on 2010-04-18
try:
```

os.chdir("/home/dodle/Desktop")

```
you just need to change the working directory, not the root directory

---

### Post by dodle on 2010-04-18
Thanks ssam, that does answer my question.

---

