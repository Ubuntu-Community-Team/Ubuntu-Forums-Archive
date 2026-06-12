---
title: "WINE Drive Mapping problems?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by TKMR on 2008-11-12
I am having some trouble with a program that is Windows Specific, that I am using Wine to emulate. 

I have Rosetta Stone (Whether it has compatibility for multiple operating systems or not, I do not know, but the version I have is most definitely a Windows installer) and whenever it tries to look for the language data, which is on a CD, it cannot find it. Not knowing precisely how this program works, I am assuming that it looks for the language data in D: or E: (depending on which is the CD-ROM drive).

In Wine I have the drives mapped correctly, I think, but the program still is not finding the data on the CD. Any ideas as to what could be causing this? Are my drives mapped correctly.?

This is the way the drives are mapped in Wine:
```
Letter    |   Drive Mapping
C:        |   ../drive_c
D:        |   /media/cdrom0/
E:        |   /cdrom/ (I tried this one to see if D was mapped incorrectly)
H:        |   /home/user_name,
```

EDIT: When I open the Application in WINE, the CD in my drive spins up, but it is like it just does not read it correctly. Also the WINE AppDB has my version of Rosetta Stone in the "Gold" Category...

---

