---
title: "mixing c with c++?"
date: 2008-02-07
forum: Programming Talk
---

### Post by 25an on 2008-02-07
Hi
I am having some problems linking a c library with my c++ application. I have written the c library on my own and managed to link it with a c application now I would like to link it with my c++ application. I have included in the c library h-file the syntax 

#ifdef __cplusplus
extern "C" {
#endif
..
...
.....
...
#ifdef __cplusplus
}
#endif

so the entire contents of the h-file is inside the extern "C" declaration according to tutorials on the net. Next step is the compilation and linking, the commands I am using is 

g++ -o framebuffer.o  -c -Wall -L./lib -I./include framebuffer.cc
g++ -o fb_main.o -c -Wall -L./lib -I./include fb_main.cc
gcc framebuffer.o  fb_main.o -lstdc++ -lmikrofb -o fb_main 

but I can't link it with gcc I always get the error 

gcc framebuffer.o  fb_main.o -lstdc++ -lmikrofb  -o fb_main 
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make: *** [fb_main] Error 1

If I use g++ instead I get the error

-lstdc++ -lmikrofb -o fb_main
/usr/bin/ld: cannot find -lmikrofb
collect2: ld returned 1 exit status

Any help is appreciated

---

### Post by hod139 on 2008-02-07
> **25an said:**
> 
gcc framebuffer.o  fb_main.o -lstdc++ -lmikrofb  -o fb_main 
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make: *** [fb_main] Error 1

Did you install the package build-essential?

> 
If I use g++ instead I get the error

-lstdc++ -lmikrofb -o fb_main
/usr/bin/ld: cannot find -lmikrofb
collect2: ld returned 1 exit status

That error means it cannot find the library libmikrofb.so  You can specify the location of this library using the -L flag.

---

### Post by stroyan on 2008-02-07
You used the '-L./lib' option when using 'g++ -c' to create .o files.
But it is only effective when using g++ for linking a program (or shared library).
You can remove it from the '-c' line and add it to the link line before '-lmikrofb'.
You should use g++ for linking.
The gcc command does not necessarily look in all the right places for c++ system libraries.

---

### Post by 25an on 2008-02-11
So what you are saying is that I should run the commands

g++ -o framebuffer.o -Wall -L./lib -I./include framebuffer.cc
g++ -o fb_main.o -Wall -L./lib -I./include fb_main.cc
g++ framebuffer.o fb_main.o -c -lstdc++ -lmikrofb -o fb_main 

did I understand it correct?

When I run this I get allot of errors when trying to compile the framebuffer.cc


(.text+0x20): undefined reference to `main'
/tmp/ccxWFmfP.o: In function `MFrameBuffer::MFrameBuffer()':
framebuffer.cc .text+0x41 undefined reference to `fb_init'
....
..
....
...
.....'
/tmp/ccxWFmfP.o: In function `MFrameBuffer::circle(int, int, int)':
framebuffer.cc .text+0x31d undefined reference to `draw_circle'
collect2: ld returned 1 exit status
make: *** [framebuffer.o] Error 1

---

### Post by stroyan on 2008-02-11
The -L option needs to be on the links the program.
In your case that is the third line.
That assumes that there is a ./lib/libmikrofb.so library to link to.
```

g++ -o framebuffer.o -Wall -I./include framebuffer.cc
g++ -o fb_main.o -Wall -I./include fb_main.cc
g++ framebuffer.o fb_main.o -c -L./lib -lstdc++ -lmikrofb -o fb_main 
```

---

### Post by DougB1958 on 2008-02-11
It also looks like somewhere along the way the "-c" switch (meaning "compile but don't link yet") has moved into your link command (the third line of the example). It should stay with the two compile commands, so the sequence should look like

```
g++ -o framebuffer.o -c -Wall -I./include framebuffer.cc
g++ -o fb_main.o -c -Wall -I./include fb_main.cc
g++ framebuffer.o fb_main.o -L./lib -lstdc++ -lmikrofb -o fb_main
```

---

