---
title: "problem with qt creator"
date: 2017-02-04
forum: Programming Talk
---

### Post by hmiersch on 2017-02-04
hi.
after installing 16.04 (i know, several months late) i installed qt creator. the problem is that when i create a new project and then try to build it, i get an error: :-1: error:  cannot find -lGL. when i right-click on it and select show output, i get this:

 ```
[COLOR=#0000aa]
17:36:32: Running steps for project test...[/COLOR]

 [COLOR=#0000aa]17:36:32: Configuration unchanged, skipping qmake step.[/COLOR]
 [COLOR=#0000aa]17:36:32: Starting: "/usr/bin/make" [/COLOR]
 [COLOR=#000000]g++ -Wl,-rpath,/home/harry/Qt/5.7/gcc_64/lib -o test main.o mainwindow.o moc_mainwindow.o   -L/home/harry/Qt/5.7/gcc_64/lib -lQt5Widgets -L/usr/lib64 -lQt5Gui -lQt5Core -lGL -lpthread [/COLOR]
 [COLOR=#aa0000]/usr/bin/ld: cannot find -lGL[/COLOR]
 [COLOR=#aa0000]collect2: error: ld returned 1 exit status[/COLOR]

 [COLOR=#000000]Makefile:220: recipe for target 'test' failed[/COLOR]
 [COLOR=#aa0000]make: *** [test] Error 1[/COLOR]
 [COLOR=#aa0000]17:36:34: The process "/usr/bin/make" exited with code 2.[/COLOR]
 [COLOR=#aa0000]Error while building/deploying project test (kit: Desktop Qt 5.7.1 GCC 64bit)[/COLOR]
 [COLOR=#aa0000]When executing step "Make"[/COLOR]
 [COLOR=#0000aa]17:36:34: Elapsed time: 00:03.[/COLOR]

```

the thing is that i haven't made any changes to the project, and still i get this error. what is wrong here, and what can i do about it?

---

### Post by dragonfly41 on 2017-02-04
You should find plenty of links if you search ..
Here is just one I found ...


[http://stackoverflow.com/questions/30321980/usr-bin-ld-cannot-find-lgl](http://stackoverflow.com/questions/30321980/usr-bin-ld-cannot-find-lgl)


run
ldconfig -p | grep libGL.so


This is what I see (mind you I have older setup, Ubuntu 14.04 32 bit with Qt 5.7 Creator)


```

libGL.so.1 (libc6) => /usr/lib/nvidia-340/libGL.so.1
libGL.so (libc6) => /usr/lib/nvidia-340/libGL.so
libGL.so (libc6) => /usr/lib/i386-linux-gnu/libGL.so

```

Also browse the Qt forum.

---

### Post by cariboo on 2017-02-04
Moved

---

### Post by aurquiel on 2017-02-06
Install mesa-dev and other mesa packet i can't remember

---

