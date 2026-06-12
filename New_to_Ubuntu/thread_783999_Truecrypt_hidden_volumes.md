---
title: "Truecrypt hidden volumes"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by hopelessone on 2008-05-06
Hi All,

in:
[https://help.ubuntu.com/community/TruecryptHiddenVolume](https://help.ubuntu.com/community/TruecryptHiddenVolume)

it says:

8. Format the hidden volume with a filesystem recognised by mount8: 
```
sudo mkfs.xfs /dev/mapper/truecrypt0
```
so ext3 is ok? how can i find out what mount8 is?

thanks...

---

### Post by glennric on 2008-05-06
I am not sure why they have mount(8) on that page, but they just mean format the partition to a file system recognized by the mount utility.

Edit:  The 8 refers to the reference number of the man page.  I am not sure what those numbers mean though.

---

### Post by glennric on 2008-05-06
No one is probably interested, but I found out about these numbers in the man pages.  The following excerpt from
[Reading man pages]("http://linuxcommand.org/reading_man_pages.php")
explains it:
```
(In reference to LS(1))The (1) indicates that this page is found in section 1 of the manual. Section 1 traditionally contains pages for commands supplied with the operating system.

Man page sections are:
     (1)     User Commands
     (2)     System Calls
     (3)     Library functions
     (4)     Devices
     (5)     File formats
     (6)     Games and Amusements
     (7)     Conventions and Miscellany
     (8)     System Administration and Priveledged Commands
     (L)     Local. Some programs install their man pages into this section instead of (1)
     (N)     TCL commands

To get an introduction to each section you can try typing 'man, the section, intro' i.e., "man 1 intro".
```

---

