---
title: "C++ help (problem is probably simple)"
date: 2009-04-13
forum: Programming Talk
---

### Post by Wug on 2009-04-13
EDIT: FULLY RESOLVED

The class declaration was coming after the prototype, so the compiler wasnt recognizing it as valid.  Typical...

---

### Post by kjohansen on 2009-04-13
well you are probably going to have provide more code and some more details like what compiler.

from what i see DLLIMPORT is a microsoft specific thing:
[http://msdn.microsoft.com/en-us/library/3y1sfaz2(VS.71).aspx](http://msdn.microsoft.com/en-us/library/3y1sfaz2(VS.71).aspx)

---

### Post by Zugzwang on 2009-04-13
> **drag0nfur said:**
> my compiler is gagging over this line:

It is giving me "syntax error before '('"
bmp_image is a defined class, as is DLLIMPORT.
the line above it ends in a semocolon.
I cant think of any other reason it should choke.
HELP!?

Which compiler are you using? DLLIMPORT is not a class but a compiler directive for calling conventions. Try removing "DLLIMPORT" and see if it compiles.

---

### Post by Wug on 2009-04-13
I tried all that stuff.  It still doesnt compile correctly, but the syntax error goes away (and is replaced by other more explainable ones) if i remove 'bmp_image' from the src.
on in interesting note, there are two functions declared successively:
> extern "C" DLLIMPORT double CheckMandel(double r, double i, int d);
extern "C" DLLIMPORT bmp_image RenderMbrot(double xmin, double xmax, double ymin, double ymax, int wpix, int hpix, int depth);

and only the second is having trouble.  (Seems like a problem with the class name, although I checked it about 10 times)

Other Details:
I am using winXP right now.
My IDE is Dev-C++, which is a frontend for the MinGW compiler.

---

### Post by cabalas on 2009-04-13
Are you linking with the win32 library? as I am pretty sure that is where the dll import stuff is declared. I am not 100% sure of the name of the library but you will need to add it to your link options it should be something like this

```
-lw32
```

Again I'm not sure on the name of the library so you should check.

---

