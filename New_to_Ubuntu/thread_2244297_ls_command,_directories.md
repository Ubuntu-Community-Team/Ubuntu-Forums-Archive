---
title: "ls command, directories"
date: 2014-09-15
forum: New to Ubuntu
---

### Post by wannbenixdude on 2014-09-15
> 
a301-3@a3013-desktop:~$ ls
abcd             Desktop    Downloads         Music     Public     Videos
Calibre Library  Documents  examples.desktop  Pictures  Templates
a301-3@a3013-desktop:~$ ls T*
a301-3@a3013-desktop:~$ 

a301-3@a3013-desktop:~$ ls P*
Pictures:
Selection_001.png  Selection_002.png  Selection_003.png

Public:
a301-3@a3013-desktop:~$ ls -l
total 48
-rw-r--r-- 1 a301-3 a301-3    0 Sep 15 08:37 abcd
drwxr-xr-x 3 a301-3 a301-3 4096 Sep  3 08:35 Calibre Library
drwxr-xr-x 2 a301-3 a301-3 4096 Sep 15 07:43 Desktop
drwxr-xr-x 2 a301-3 a301-3 4096 Sep  8 08:13 Documents
drwxr-xr-x 2 a301-3 a301-3 4096 Sep 10 09:09 Downloads
-rw-r--r-- 1 a301-3 a301-3 8980 Aug 27 13:27 examples.desktop
drwxr-xr-x 2 a301-3 a301-3 4096 Aug 27 13:35 Music
drwxr-xr-x 2 a301-3 a301-3 4096 Sep  3 09:18 Pictures
drwxr-xr-x 2 a301-3 a301-3 4096 Aug 27 13:35 Public
drwxr-xr-x 2 a301-3 a301-3 4096 Aug 27 13:35 Templates
drwxr-xr-x 2 a301-3 a301-3 4096 Aug 27 13:35 Videos
a301-3@a3013-desktop:~$ 



Im not sure whats going on here. Why doesnt "ls T*" return Templates ?

---

### Post by sisco311 on 2014-09-15
Because there is nothing to be listed in Templates, it's empty. 


```

[sisco@acme xtmp]$ mkdir foo
[sisco@acme xtmp]$ ls foo
[sisco@acme xtmp]$ ls -d foo
foo
[sisco@acme xtmp]$ mkdir files
[sisco@acme xtmp]$ ls foo files
files:

foo:
[sisco@acme xtmp]$ ls f*
files:

foo:

```

As you can see, the name of the directory is printed only when you list multiple directories. When you list the content of a single directory, the name of the directory is not displayed.

---

### Post by wannbenixdude on 2014-09-15
:) 

Ddddduuuuuuuuhhhhhhhhhhhhhhhhhhhhh  !

Thanks for the help ! Sheez .. gotta look past my nose huh :)

---

