---
title: "Can't Understand Terminal Mousepoll Install Error Output Text...Can Someone Explain?"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by iaskedalice09 on 2008-09-18
I'm trying to install mousepoll for ezoom (YAY!):

But it's not working. So I am hope some kind soul can interpret for me please?

```

tom@dell-desktop:~/compiz$ git clone git://anongit.compiz-fusion.org/fusion/plugins/mousepoll
Initialized empty Git repository in /home/tom/compiz/mousepoll/.git/
remote: Counting objects: 42, done.
remote: Compressing objects: 100% (39/39), done.
remote: Total 42 (delta 20), reused 0 (delta 0)
Receiving objects: 100% (42/42), 11.01 KiB | 5 KiB/s, done.
Resolving deltas: 100% (20/20), done.
tom@dell-desktop:~/compiz$ cd mousepoll/
tom@dell-desktop:~/compiz/mousepoll$ make
Makefile:152: [WARNING] This plugin might be needed by other plugins. Install it with "BUILD_GLOBAL=true sudo make install" 
convert   : mousepoll.xml.in -> build/mousepoll.xml
schema    : build/mousepoll.xml -> build/compiz-mousepoll.schema
compiling : mousepoll.c -> build/mousepoll.lomousepoll.c: In function ‘mousepollAddPositionPolling’:
mousepoll.c:171: warning: passing argument 2 of ‘compAddTimeout’ makes pointer from integer without a cast
mousepoll.c:171: error: too many arguments to function ‘compAddTimeout’
mousepoll.c: In function ‘mousepollSetDisplayOption’:
mousepoll.c:278: warning: passing argument 2 of ‘compAddTimeout’ makes pointer from integer without a cast
mousepoll.c:278: error: too many arguments to function ‘compAddTimeout’
make: *** [build/mousepoll.lo] Error 1
tom@dell-desktop:~/compiz/mousepoll$ BUILD_GLOBAL=true sudo make install
Makefile:152: [WARNING] This plugin might be needed by other plugins. Install it with "BUILD_GLOBAL=true sudo make install" 
compiling : mousepoll.c -> build/mousepoll.lomousepoll.c: In function ‘mousepollAddPositionPolling’:
mousepoll.c:171: warning: passing argument 2 of ‘compAddTimeout’ makes pointer from integer without a cast
mousepoll.c:171: error: too many arguments to function ‘compAddTimeout’
mousepoll.c: In function ‘mousepollSetDisplayOption’:
mousepoll.c:278: warning: passing argument 2 of ‘compAddTimeout’ makes pointer from integer without a cast
mousepoll.c:278: error: too many arguments to function ‘compAddTimeout’
make: *** [build/mousepoll.lo] Error 1

```

I think it means that the source was incorrect (too many arguments??).

The kind soul that solves this will get a Thanks and a plate of cookies. :)

Off to bed but I promise I'll respond. :)

---

