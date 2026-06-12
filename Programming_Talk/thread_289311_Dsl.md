---
title: "Dsl"
date: 2006-10-30
forum: Programming Talk
---

### Post by moonraker808 on 2006-10-30
When I try to install the DSL library I keep getting this message. 
enviroment is out dated
and when I compile it, this is what I get.
Compiling...
dsl.cpp
d:\Visual Studio Projects\eviroment run time\dsl.cpp(1) : fatal error C1083: Cannot open include file: 'SDL/SDL.h': No such file or directory

Build log was saved at "file://d:\Visual Studio Projects\eviroment run time\Debug\BuildLog.htm"
eviroment run time - 1 error(s), 0 warning(s)

Does anyone who uses the DSL library with their visual basic C++ know how to fix this problem?
Here are the links:
[http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php)
[http://lazyfooproductions.com/SDL_tutorials/index.php](http://lazyfooproductions.com/SDL_tutorials/index.php)

---

### Post by amo-ej1 on 2006-10-31
a) SDL not DSL
b) visual basic C++ ? 

i guess you got a bit disoriented in space and time, but i'm almost 100% sure  you're asking this in the wrong place ;)

---

### Post by moonraker808 on 2006-10-31
I meant SDL, I guess I just typed it a little to fast. Any solutions to this though?

---

### Post by thoolihan on 2006-11-01
> **moonraker808 said:**
> I meant SDL, I guess I just typed it a little to fast. Any solutions to this though?

You should probably post this in an SDL forum or a Visual Studio forum, since you're trying to develop on Windows.  

But my quick stab at it is this: Check out your project paths.  Looks like your compiler doesn't know how to find your SDL files.  This is most likely a setting in Visual studio called something like include path...

---

### Post by moonraker808 on 2006-11-01
i'll try searching for the path, but it would be very helpful to know where to find some SDL forums, so I can submit my question there, and anything I may need to know about SDL in the future.

---

### Post by yabbadabbadont on 2006-11-01
> **moonraker808 said:**
> i'll try searching for the path, but it would be very helpful to know where to find some SDL forums, so I can submit my question there, and anything I may need to know about SDL in the future.

[http://www.libsdl.org/index.php](http://www.libsdl.org/index.php)

---

### Post by thoolihan on 2006-11-01
Mailing lists at:

[http://www.libsdl.org/mailman/listinfo/](http://www.libsdl.org/mailman/listinfo/)

---

