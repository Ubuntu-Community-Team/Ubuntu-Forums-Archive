---
title: "Compiling openGL code, (where's -lX11?)"
date: 2006-07-12
forum: Programming Talk
---

### Post by sadscientist on 2006-07-12
Thanks in advance.. I've been able to get openGL code to compile without much of a problem in windows, using .NET... however, I *need* to get some openGL code working in linux :P


So, after a while, I've managed to get openGL *working*.. (screensavers run smoothly, and..)

```
andrew@deimos:~/programming$
andrew@deimos:~/programming$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)

andrew@deimos:~/programming$ glxinfo |grep rendering
direct rendering: Yes

```

Now I'm trying to learn openGL, and I'm following the Red Book as well as Nehe's tutorials..

I downloaded the Linux code (by Richard Campbell) at the bottom of [Lesson 2]("http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=02"), and unpacked it into /home/andrew/programming/lesson02/ ...

now, when I try to compile this source code...

```
andrew@deimos:~/programming/lesson02$ make
gcc -Wall -I/usr/include/   -c -o lesson2.o lesson2.c
lesson2.c: In function ‘keyPressed’:
lesson2.c:94: warning: implicit declaration of function ‘exit’
lesson2.c:94: warning: incompatible implicit declaration of built-in function ‘exit’
gcc -Wall -I/usr/include/ -o lesson2 -L/usr/X11R6/lib  lesson2.o -lX11 -lXi -lXmu -lglut -lGL -lGLU -lm
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
make: *** [lesson2] Error 1
rm lesson2.o

```

So I think I'm missing some X-development libraries.  I've read a few people say I should get the package "x-window-system-dev", but..

```
andrew@deimos:~/programming/lesson02$ sudo apt-get install x-window-system-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package x-window-system-dev

```

Here are my repositories:

```
andrew@deimos:/etc/apt$ cat sources.list
deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
andrew@deimos:/etc/apt$      
```

---

### Post by sadscientist on 2006-07-12
Ok, libx11-dev seems to have been the package I was looking for.  

Now I "cannot find -lXi", so I'm guessing I'll have to track down packages for -lX11 -lXi -lXmu -lglut -lGL -lGLU -lm... hehe.

---

### Post by sadscientist on 2006-07-12
After a..

```
sudo apt-get install X-dev libX11-dev libXi-dev libXmu-dev
```

..it just compiled.  Now I've got some sexy polygons rendering.


Yar!!

(p.s.  the window with the openGL drawing inside is fullscreen.. but.. my panel is "showing" overtop of it.. any idea why? (i'm using kde) )

---

### Post by sadscientist on 2006-07-12
> (p.s.  the window with the openGL drawing inside is fullscreen.. but.. my panel is "showing" overtop of it.. any idea why? (i'm using kde) )

I suppose because my openGL program just opens a new x-window, and the panel is allowed to cover them.  Configure Panel -> Hiding -> Hide Automatically will work out fine for now.

---

### Post by falseicon on 2007-11-11
Thanks for following up on your solution, I ran into the same problem

---

### Post by diegoful on 2008-05-06
Man! Thanks A LOT for following up on the solution. So many people leave just open problems...

---

### Post by JDiesel on 2008-10-12
Thanks a lot man.

---

