---
title: "Some trouble with linking OpenAL"
date: 2007-09-25
forum: Programming Talk
---

### Post by Vorticon on 2007-09-25
Hello everyone.

I've recently started a bit of Linux C programming. I have some basic knowledge of C++ but what i don't get is the following linking problem.

I am following this tutorial to play a sound file with OpenAL:
[http://www.devmaster.net/articles/openal-tutorials/lesson1.php](http://www.devmaster.net/articles/openal-tutorials/lesson1.php)

and even if i use the package on the bottom of the page (this one:  [http://www.devmaster.net/articles/openal-tutorials/lesson1_linux.tar.bz2](http://www.devmaster.net/articles/openal-tutorials/lesson1_linux.tar.bz2) ) and then try to build it i get the following output:

```
me@my pc:~/Desktop/lesson1$ make
g++ -o lesson1 main.o -lopenal
main.o: In function `KillALData()':
main.cpp:(.text+0x23): undefined reference to `alutExit'
main.o: In function `LoadALData()':
main.cpp:(.text+0xb5): undefined reference to `alutLoadWAVFile'
main.cpp:(.text+0xe2): undefined reference to `alutUnloadWAV'
main.o: In function `main':
main.cpp:(.text+0x212): undefined reference to `alutInit'
collect2: ld returned 1 exit status
make: *** [lesson1] Error 1
me@my pc:~/Desktop/lesson1$ 
```

I assume it isn't linking correctly or some sort? How can this go wrong if it says "-lopenal" to link the openal library to the compiler..? Is the makefile wrong?

I am using Ubuntu Feisty AMD64 for your information.
If anyone can help me with this problem i'd be much obliged :)

p.s. I have the openal dev packages installed

---

### Post by Vorticon on 2007-09-25
Solved.

Found the solution here:

[http://www.nabble.com/Bug-357835:-Missing-library-flag-for-ALUT-from-openal-config-t1307770.html](http://www.nabble.com/Bug-357835:-Missing-library-flag-for-ALUT-from-openal-config-t1307770.html)

Let's hope this post can still help more people who have this problem :)

---

### Post by ownsuall on 2010-06-09
Thanks for posting this was looking everywhere to fix this error.

---

