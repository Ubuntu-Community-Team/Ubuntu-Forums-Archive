---
title: "ld Can't Find OpenGL Libraries"
date: 2008-04-27
forum: Programming Talk
---

### Post by GenuineXP on 2008-04-27
I'm a bit confused here, but suddenly I can't link my own project because it needs to link with libGL.so* and ld reports that it can't find it!
```

sean@harpuia:~/Projects/mocha/trunk/guarana$ make
g++ -nostdlibs -shared -rdynamic -Wl,-soname,libguarana.so -olibguarana.so gl_sdl_graphics_impl.o gl_texture.o guarana.o il_image.o sdl_event_queue_impl.o sdl_input_impl.o sdl_timer_impl.o -L../ -lGL -lIL -lILU -lILUT -lSDL -lSDLmain -lmocha -lgcc
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [guarana] Error 1
sean@harpuia:~/Projects/mocha/trunk/guarana$ 

```
This has never happened before, and ldconfig --print-cache shows an entry for libGL.so.1! So what's going on here? This was working a few days ago without any problems.

I'm running Ubuntu Hardy x86. Any incite is appreciated. Thanks!

---

### Post by GenuineXP on 2008-04-27
It seems that adding a symbolic link called libGL.so pointing to libGL.so.1 did the trick (libGL.so.1 is actually a symbolic link to the fully versioned library anyway).

I hope this is safe. I wonder what broke it in the first place?

---

### Post by jalirious on 2008-09-22
To do this:

sudo su
cd /usr/lib
ls -ltr *GL*
[if libGL.so ~0 bytes]
rm libGL.so [<- edit, unnecessary] 
ln -s libGL.so.1.2 libGL.so

(replace 1.2 with yours)

---

