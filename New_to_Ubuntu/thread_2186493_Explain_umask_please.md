---
title: "Explain umask please?"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by rubensaurus on 2013-11-07
I'm reading a Linux Bible book I bought and ran across unmask. I've looked online at various sites and videos to explain it, but I must have a hard time grasping the concept.  I know it's a default used to set permissions for files and folders when created, and I understand rwx=421 and the ugo ad well. 

I just don't understand why its set as 022 and 755.. Maybe I need diagrams and formulas lol.

---

### Post by papibe on 2013-11-07
Hi rubensaurus.

Just in case (to cover the basics):
```
--x = 1
-w- = 2
r-- = 4

```then
```

rw- = 6
r-x = 5
rwx = 7
```
Does that help?
Regards.

---

### Post by Kevin_Arnold on 2013-11-07
umask is like a filter they run permissions through. So full permissions is 777 and then the subtract the umask from it so a umask of 022 gives you a default of 755 (777 - 022)

---

### Post by rubensaurus on 2013-11-07
So if I want to have the default be  777 would I have  a umask of 000? Or if I want rwxrw-rw- I would be  011?

---

### Post by papibe on 2013-11-07
> **rubensaurus said:**
> So if I want to have the default be  777 would I have  a umask of 000? Or if I want rwxrw-rw- I would be  011?
Yes, but note that file creation by default won't include execution bit.

For instance:
```
$ umask 000
$ touch thisfile
$ ls -l thisfile
-rw-rw-rw- 1 pablo pablo 12 Nov  7 16:30 thisfile
```
However, with directories will be exactly that:
```
$ umask 000
$ mkdir thisdir
$ ls -ld thisdir
drwxrwxrwx 2 pablo pablo 4096 Nov  7 16:29 thisdir/
```
Does that help?
Regards.

---

### Post by rubensaurus on 2013-11-07
> **Kevin_Arnold said:**
> umask is like a filter they run permissions through. So full permissions is 777 and then the subtract the umask from it so a umask of 022 gives you a default of 755 (777 - 022)

> **papibe said:**
> Yes, but note that file creation by default won't include execution bit.

For instance:
```
$ umask 000
$ touch thisfile
$ ls -l thisfile
-rw-rw-rw- 1 pablo pablo 12 Nov  7 16:30 thisfile
```
However, with directories will be exactly that:
```
$ umask 000
$ mkdir thisdir
$ ls -ld thisdir
drwxrwxrwx 2 pablo pablo 4096 Nov  7 16:29 thisdir/
```
Does that help?
Regards.


thanks guys!

---

### Post by bab1 on 2013-11-07
> **papibe said:**
> Yes, but note that file creation by default won't include execution bit.

For instance:
```
$ umask 000
$ touch thisfile
$ ls -l thisfile
-rw-rw-rw- 1 pablo pablo 12 Nov  7 16:30 thisfile
```
However, with directories will be exactly that:
```
$ umask 000
$ mkdir thisdir
$ ls -ld thisdir
drwxrwxrwx 2 pablo pablo 4096 Nov  7 16:29 thisdir/
```
Does that help?
Regards.

For completeness:  The reason for the difference between files and directories is that that default file creation is 666 (with 002 umask it's 664) and the default file creation is 777 (with the same umask you get 775).

The default in not the only method to set umask.  The last setting is in force however.  You can set umask at the CLI (it will disappear when the terminal is closed) and you can set umask in a script (which is in effect only during that script's execution.

---

