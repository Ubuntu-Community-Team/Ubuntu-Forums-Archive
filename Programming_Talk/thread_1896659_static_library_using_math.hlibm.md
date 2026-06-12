---
title: "static library using math.h/libm"
date: 2011-12-17
forum: Programming Talk
---

### Post by SGFzc2U= on 2011-12-17
I have made a static library, which needs sin() and cos() for rotating 3d coordinates. It needs math.h/libm. I think it is pretty annoying to compile like this: 
```

gcc main.c -o program -lmylibrary -lm.
```It would be a lot more obvious if it was without the "-lm", so how do I do it or is it even possible?

---

### Post by gateway67 on 2011-12-17
Have you tried specifying the -lm when you build the library?  After all, it is your library that is dependent on the math library, not your main.c module.

```

gcc -c -fPIC MyLibrary.c

gcc -shared -o libmylibrary.so MyLibrary.o -lm

gcc -L./ main.c -lmylibrary -o program

```

---

### Post by SGFzc2U= on 2011-12-18
Does that also work for static libraries? I don't want to make a shared library.
What about this:
```

ld -r -o mylibrary.o mylibrarypart_A.o mylibrary part_B.o -lm
```

So that the library would have only one object file and it would be partially linked.
Sadly, it didn't work:
```

ld: cannot find -lm
```

When i take the "-r" option away, it finds "-lm" just normally.:confused:

---

### Post by MadCow108 on 2011-12-18
the only way to not have to type -lm is by compiling with the C++ compiler g++ which always links with libm, the C compiler gcc does it only on request

there are two ways to static link only libm:

give the full path of the static library:
```
gcc test.c /usr/lib/x86_64-linux-gnu/libm.a
```
x86_64-linux-gnu is the output of dpkg-architecture -qDEB_HOST_MULTIARCH

as this is debian specific, this is not recommended

better let the compiler find the library:
```
gcc test.c -Wl,-Bstatic -lm -Wl,-Bdynamic
```
this tells the linker to look for a static libm and the rest should stay dynamic

you can test your result with:
```
$ ldd ./a.out 
	linux-vdso.so.1 =>  (0x00007fe9c1831000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fe9c1461000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fe9c1832000)
```


on debian based systems you need libc6-dev installed for the static libm.

---

### Post by 3Miro on 2011-12-18
I would advise against doing that. gateway67's solution should work, but I wouldn't do something like that. There is a reason why -lm is needed. The library that comes with gcc is not always optimal, this if you were to give my your library without including cos() and sin(), then I would be able to link to my ow n version of libmath that may be optimized for my machine. If you give me static versions of cos() and sin() I would be unable to improve them.

Why does -lm bother you. It is not like you have to write it over and over again, if you have a make file then all you need to do is write "make" and it will automatically call all the right commands.

---

### Post by SGFzc2U= on 2011-12-18
The library is a helper/wrapper library for my friend, who's just starting programming in C. It confuses him if using a library means that you have to link -lmylibrary -lm -lpthread etc..

Should i write my own functions for sin() and cos()? They're the only math functions that i need currently.

---

### Post by MadCow108 on 2011-12-18
give him a shared library like gateway67 suggested or a static one with libm compiled in (see my post)
then he does not need to link libm unless he uses it himself.

but he will have to learn this anyway, dealing with libraries and symbols is an essential part of C programming.

---

### Post by 3Miro on 2011-12-18
> **SGFzc2U= said:**
> The library is a helper/wrapper library for my friend, who's just starting programming in C. It confuses him if using a library means that you have to link -lmylibrary -lm -lpthread etc..

Should i write my own functions for sin() and cos()? They're the only math functions that i need currently.

You can certainly write your own sin() and cos() functions, however, your friend should learn how to work with libraries. If it is confusing to him, then he should take the time to understand it, especially what it means to "link".

---

### Post by SGFzc2U= on 2011-12-18
I decided to make sin() and cos() myself. I anyways need as fast as possible implementation for 60fps, so lookup table is good enough.

And yeah, he should learn about linking, but even some easy code-stuff confuses him, so I think he shouldn't try to learn compiler things before he can even make function calls.

Thanks for answers, I will mark this as solved.:D

---

