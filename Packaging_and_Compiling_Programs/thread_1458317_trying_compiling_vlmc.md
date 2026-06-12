---
title: "trying compiling vlmc"
date: 2010-04-19
forum: Packaging and Compiling Programs
---

### Post by suoko on 2010-04-19
following this guide [http://www.frenssen.be/content/install-vlmc-video-editor-debian-and-ubuntu](http://www.frenssen.be/content/install-vlmc-video-editor-debian-and-ubuntu)

but end up with this error at vlmc making

make
g++ -Wl,-O1 -o vlmc     -L/usr/lib -L/usr/local/lib -lvlc -lQtGui -lQtCore -lpthread
/usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/crt1.o: In function `_start':
/build/buildd/eglibc-2.10.1/csu/../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [vlmc] Errore 1

using gnome karmic
here is the correctly compiled 1.2 version of vlc since first step was ok [i named it 1.1 but it's 1.2)
[http://www.box.net/shared/vjc99q93m1](http://www.box.net/shared/vjc99q93m1)

---

### Post by mc4man on 2010-04-20
maybe try this way

```
sudo apt-get install cmake
```

```
git clone git://git.videolan.org/vlmc.git
```
cd to vlmc source dir. and
```
cmake .
```
```
make
```

---

### Post by PFrenssen on 2010-05-09
I'm the author of that guide. Thanks for the solution, I have updated the guide. It now works fine with the latest VLMC source and under Lucid as well.

---

