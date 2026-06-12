---
title: "Linking SDL_image problem"
date: 2008-07-30
forum: Programming Talk
---

### Post by projectgonewrong on 2008-07-30
I assume that this will be a fairly easy fix.

Okay I installed "libsdl-image" automatically.

Then when I compiled my program and included it, it said it did not exist.

So I downloaded it manually and just put the header file into the SDL directory.

So now it can locate the header file but when I try to link it, it says this:

/usr/bin/ld: cannot find -lSDL_image
collect2: ld returned 1 exit status


How do I go about fixing this manually since I already tried reinstall of SDL, SDL-imageimage, SDL-all, gcc, g++.  And that did not help.

---

### Post by Zugzwang on 2008-07-30
Did you also install the package "libsdl-image1.2-dev"? Installing the -dev packages is required for compilation.

---

### Post by dwhitney67 on 2008-07-30
Also take a look at this post:  [http://ubuntuforums.org/showpost.php?p=5228252&postcount=9](http://ubuntuforums.org/showpost.php?p=5228252&postcount=9)

---

### Post by projectgonewrong on 2008-07-30
Aha that was it I didn't install the Dev files.  Now I feel dumb.

I haven't installed it in so long I have always just had it so I didn't remember that.

---

### Post by bourriquet42 on 2009-02-15
Hum, i have installed the libsdl-image1.2-dev package but i still get the "/usr/bin/ld: cannot find -lSDL_Image" error.
Is there another thing i forgot?

---

### Post by PythonPower on 2009-02-15
I'm not on Ubuntu to test this at the moment... but I think you need to compile with either:

> -lSDL_image
> -lSDL_Image

Worth a try I guess. ;)

---

### Post by dwhitney67 on 2009-02-15
> **bourriquet42 said:**
> Hum, i have installed the libsdl-image1.2-dev package but i still get the "/usr/bin/ld: cannot find -lSDL_Image" error.
Is there another thing i forgot?

Show us the GCC compile/link statement you were using to build your app.  Maybe the problem lies there?

---

### Post by bourriquet42 on 2009-02-15
```
g++ -Wall -I/usr/include/   -c -o lesson3.o lesson3.c
g++ -Wall -I/usr/include/ -o lesson3 -L/usr/X11R6/lib  lesson3.o -lX11 -lXi -lXmu -lglut -lGL -lGLU -lm -lSDL -lSDL_Image  
/usr/bin/ld: cannot find -lSDL_Image
collect2: ld a retourné 1 code d'état d'exécution
make: *** [lesson3] Erreur 1
rm lesson3.o

```

---

### Post by dwhitney67 on 2009-02-15
Did you reference the link in this [post]("http://ubuntuforums.org/showpost.php?p=5488871&postcount=3")?

Try using `pkg-config sdl --libs` in lieu of specifying the SDL library yourself.

When compiling your file, you may need to specify `pkg-config sdl --cflags`.

Btw, many people seem to make the mistake of thinking that their CFLAGS are going to make a difference during the link stage of building their application; it won't.  Thus you can leave out the -Wall -I/usr/include when you are linking your object files with the libraries.

Try:
```

g++ -Wall -I/usr/include/ `pkg-config sdl --cflags` -c -o lesson3.o lesson3.c
g++ -o lesson3 -L/usr/X11R6/lib  lesson3.o -lX11 -lXi -lXmu -lglut -lGL -lGLU -lm `pkg-config sdl --libs`

```
You may want to verify if you really need to specify all of those other libraries.

---

### Post by bourriquet42 on 2009-02-15
```
 pkg-config sdl --libs --cflags
-D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/SDL  -lSDL  
```

Should i conclude that sdl-image has not been installed correctly?

---

### Post by dwhitney67 on 2009-02-15
You should look for the library in /usr/lib.  Run this command:
```

ls /usr/lib/*SDL*

```
I bet you need to specify SDL_image, not SDL_Image.

---

### Post by bourriquet42 on 2009-02-15
Well done!

```
3$ ls /usr/lib/*SDL*
/usr/lib/libSDL-1.2.so.0            /usr/lib/libSDL_image.la
/usr/lib/libSDL-1.2.so.0.11.1       /usr/lib/libSDL_image.so
/usr/lib/libSDL.a                   /usr/lib/libSDL.la
/usr/lib/libSDL_image-1.2.so.0      /usr/lib/libSDLmain.a
/usr/lib/libSDL_image-1.2.so.0.1.5  /usr/lib/libSDL.so
/usr/lib/libSDL_image.a

```

I tried -lSDL_image and it works!
But what should I do to make the pkg-config sdl see the SDL_image? Rename the files?...:confused:

---

### Post by dwhitney67 on 2009-02-15
You have three options.

1)  Specify the library directly when linking.

2)  Modify the /usr/lib/pkgconfig/sdl.pc file to include -lSDL_image

3)  Create your own pkgconfig file, calling it sdl_image.pc.  Use sdl.pc as a template.


If you choose option 1 or 2, you may need/want to create a symbolic link in /usr/lib.  For example:
```

cd /usr/lib
sudo ln -s libSDL_image-1.2.so.0 libSDL_image.so

```

P.S.  The version of your SDL_image library may differ from that shown above.

---

