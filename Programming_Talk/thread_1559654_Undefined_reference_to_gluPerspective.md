---
title: "Undefined reference to gluPerspective"
date: 2010-08-23
forum: Programming Talk
---

### Post by FattyOwl on 2010-08-23
I am trying to learn OpenGL using these tutorials:
[http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup_linux/video.php](http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup_linux/video.php)

They told me to download a source file and compile it. It should result in a spinning cube.

However when I try to compile it it gives me the following error:
```
kobe@kobe-laptop:~/Tutorials/Cube$ make
g++ -Wall -o cube main.cpp imageloader.cpp -lglut
imageloader.cpp: In function ‘Image* loadBMP(const char*)’:
imageloader.cpp:141: warning: suggest parentheses around ‘&&’ within ‘||’
/tmp/ccDxFyfp.o: In function `handleResize(int, int)':
main.cpp:(.text+0x18b): undefined reference to `gluPerspective'
collect2: ld returned 1 exit status
make: *** [cube] Error 1

```

I have got all the header files installed. How do I solve this problem?

Thanks in advance!

---

### Post by ju2wheels on 2010-08-23
You need to install the "dev" version of the libraries you are linking against as well...

freeglut3 and freeglut3-dev.

```

sudo apt-get install freeglut3 freeglut3-dev

```

---

### Post by Zugzwang on 2010-08-24
@FattyOWL: The Makefile in that project is outdated - it does not contain the information to also link against the "libGLU" library. So change the corresponding line in the Makefile to:
```

	LIBS = -lglut -lGLU

```

@ju2wheels: Note that "undefined reference to..." errors are linker errors, thus a missing package can never be the source of the problem (missing -dev packages are normally witnessed by the *compiler* error that some header could not be found or a linker error that a *specified* library could not be found, but "undefined reference to ..." can never be the *first* error occurring in the compiling/linking process in case of a missing package).

---

### Post by damnated on 2010-11-03
-lGLU was needed indeed, thank you for the solution. Someone should mark this thread as solved ;)

---

### Post by lesca on 2010-11-22
Thanks!

---

### Post by poo_22 on 2011-03-24
Thank you!

---

### Post by fantom1210 on 2011-05-04
Thank You also :)

---

### Post by Spirit of Yggdrasill on 2011-05-28
Thanks. This is my first contact with c++ so this helped a lot.

---

### Post by Deverone on 2011-05-29
I also wanted to express my thanks to Zugzwang for solving this issue.

---

### Post by narutokage on 2011-07-20
thank you !! :popcorn:

---

### Post by LiteDrive on 2011-08-31
Thanks.

---

### Post by KreshDev on 2011-09-14
What exactly am I supposed to edit?

---

### Post by podmod101 on 2011-10-30
Thanks worked for me too!:D

---

### Post by rocky7 on 2012-02-07
Thank you. This post saved my time.

---

### Post by tapin13 on 2012-03-30
> **damnated said:**
> -lglu was needed indeed, thank you for the solution. Someone should mark this thread as solved ;)

Thank you.

---

### Post by otttx33 on 2012-04-11
Maybe to say just 'Thank you' is outdated too.........
By the way thgank you very much

---

