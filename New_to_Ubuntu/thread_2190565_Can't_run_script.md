---
title: "Can't run script"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by guilhermeleobas on 2013-11-27
Hi,

I have a second partition in my HD (/media/drive) and I'm trying to run a .cpp script in this partition but the terminal is giving me *Denied Access*:

> guilherme@guilherme-Inspiron-N5010:/media/drive$ ./mainbash: ./main: Permission denied


I already try to use chmod +x/+r/+w in main file but this doesn't worked.

Can anyone help me?

Ps: Sorry for any language mistakes that I made. English is not my primary language.

---

### Post by steeldriver on 2013-11-27
Hello and welcome to the forum

Is the /media/drive HDD formatted for Windows (e.g. NTFS)? if so, you won't be able to set execute permissions using chmod - the easiest solution is to move the script to somewhere in the regular filesystem e.g. into your home directory

---

### Post by guilhermeleobas on 2013-11-27
No, the file system is EXT4.

---

### Post by Lars Noodén on 2013-11-28
.cpp is usually used for C++ source code and not scripts.  It has to be run through a compiler first, such as g++.  

```

g++ hello.cpp -o hello 

```

Then you should be able to run the resulting binary.

```

./hello

```

---

### Post by Lars Noodén on 2013-11-28
By the way, what does the first line of the file say?  That should tell if it is a script or not.  If it is a script, it will point to an interpreter such as /usr/bin/perl, /bin/sh, /usr/bin/python, etc.

---

### Post by guilhermeleobas on 2013-11-29
> **Lars Noodén said:**
> .cpp is usually used for C++ source code and not scripts.  It has to be run through a compiler first, such as g++.  

```

g++ hello.cpp -o hello 

```

Then you should be able to run the resulting binary.

```

./hello

```
Hi,

I know that .cpp files needs to be compiled and I did that before I try to run the binary file. 

> [COLOR=#000000]That should tell if it is a script or not. If it is a script, it will point to an interpreter such as /usr/bin/perl, /bin/sh, /usr/bin/python, etc.
I didn't know that. 

For some reason, I change the mount point of the driver from /media/sda5 to /home/drive and now the binary is running without any problems. [/COLOR]:)

---

### Post by Lars Noodén on 2013-11-30
> **guilhermeleobas said:**
> For some reason, I change the mount point of the driver from /media/sda5 to /home/drive and now the binary is running without any problems. :)

Perhaps the other mount point was mounted as noexec.  That would block you from running anything there.  You can try again and run [mount](http://manpages.ubuntu.com/manpages/saucy/en/man8/mount.8.html) to see how it was mounted.

---

