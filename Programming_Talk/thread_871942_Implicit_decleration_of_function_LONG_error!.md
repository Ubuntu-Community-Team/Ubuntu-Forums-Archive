---
title: "Implicit decleration of function LONG error?!"
date: 2008-07-27
forum: Programming Talk
---

### Post by .neo on 2008-07-27
Hello,
  I had a piece of source code for my touchscreen kernel module (itmtouch.c) that used to compile OK on Ubuntu 7.10, but now on 8.04 it gives me an error "Implicit decleration of function 'LONG'"...
  If I take out LONG(), the code compiles but I think that is what is making my Ubuntu 8.04 (here's the original line - *input_dev->keybit[LONG(BTN_TOUCH)] = BIT(BTN_TOUCH);*) not want to respond to touch events...so what does LONG in fact do in C/C++ and how do I get it back in 8.04, please?
  Thanks

P.S.
  On a side (and not really programming related) note on 7.10 the kernel module worked with version 0.8.7 of evtouch driver. On 8.04 that (and any other version of precompiled evtouch [I can't figure out how to compile evtouch from source] available from [http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html) doesn't work). It only works  with evtouch driver that Ubuntu 8.04 installs itself (pointer movement by touch at least minus click/double click touch events). Could that be my problem? Evtouch driver?! Anyone knows how to check plz?! TIA

---

### Post by LaRoza on 2008-07-27
> **.neo said:**
> Hello,
  I had a piece of source code for my touchscreen kernel module (itmtouch.c) that used to compile OK on Ubuntu 7.10, but now on 8.04 it gives me an error "Implicit decleration of function 'LONG'"...

That means their is no prototype (assuming the error message was spell properly)

> If I take out LONG(), the code compiles but I think that is what is making my Ubuntu 8.04 (here's the original line - *input_dev->keybit[LONG(BTN_TOUCH)] = BIT(BTN_TOUCH);*) not want to respond to touch events...so what does LONG in fact do in C/C++ and how do I get it back in 8.04, please?
  Thanks


LONG does what it is programmed to do. It isn't a standard function. It looks like it does type conversion. You should check out what this program needs.

---

### Post by DavidBell on 2008-07-27
Near the top of your file try adding the line 
```
typedef long LONG;
```

This is was probably in one of the header files of your old version but not in the new one. LONG(...) is probably just a cast but when the compiler sees the brackets it looks like a function that has no definition anywhere.

I agree over evtouch, it changes every time xorg is changed so you need correct version of xorg sources to compile it.

HTH DB

---

### Post by WW on 2008-07-27
DavidBell's suggestion will likely give you a syntax error.  My guess is LONG is a macro something like this:
```

#define LONG(x)  ((long) x)

```
It just casts its argument to a long.

---

### Post by .neo on 2008-07-28
Thanks all for all of your helpful comments.

However even with that long casting, either via macro, or done directly, I still get the exact same error as before. No clicks are detected?! I do get detection of movement when using evtouch_drv.so file that came installed with Ubuntu 8.04, but no clicks (although there is a hack to send clicks when ever mouse stops via assistive tech :P but that's a really bad working hack)...If I try to use the precompiled evtouch_drv.so file that I used back on version 7.10 I get the following error lines in xorg's log:

> (II) LoadModule: "evtouch"
(II) Loading /usr/lib/xorg/modules/input//evtouch_drv.so
(II) Module evtouch: vendor="Kenan Esau"
       compiled for 4.3.99.902, module version = 0.8.7
       Module class: X.Org XInput Driver
       ABI class: X.Org XInput driver, version 0.7
(EE) module ABI major version (0) doesn't match the server's version (2)
(II) UnloadModule: "evtouch"
(II) Unloading /usr/lib/xorg/modules/input//evtouch_drv.so
(EE) Failed to load module "evtouch" (module requirement mismatch, 0)

So, my guess is I need to see about how to compile evtouch drivers available from [http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html) myself. 
Unfortuantelly, I don't have much (almost any) experience in compiling/writing driver stuff, so I'm stuck on an error after running "./configure" on the 0.8.7 sources that says I'm missing *xorg-server* and *xponto* packages.

The problem is that even after doing apt-get update those two packages can not be found or installed for that matter :(

Any help would be greatlly appreciated! TIA

P.S.
Since the evtouch that comes with Ubuntu itself is partially working maybe another option would be to see what is it expecting from itmtouch (kernel module that handles my touchscreen LG's 1510SF) and change itmtouch.c accordingly... But how and where to start off that quest from?!
I thought of maybe finding a tool somewhat like Windows Spy to check weather or not the clicks are getting through to X, but without any luck googling for it (or doing something like that, trying to debug X/kernel messages) - plz don't laugh if this was stupid, I'm still learning about how linux drivers work :)))

---

### Post by DavidBell on 2008-07-29
As noted above you must find the correct Xorg sources to compile this. I don't know if ubuntu adjusts sources like that but if they do you would need their version. 

Been ages since I played with this but my memory is evtouch is an xorg driver that takes input from kernel drivers like usbtouchkit. In my case someone else managed to compile evtouch, I was just playing with usbtouchkit.

DB

---

### Post by DavidBell on 2008-07-29
@WW using that typedef is pretty common, problem with the macro is it will fail if someone does
```
LONG x;
```

---

### Post by WW on 2008-07-29
> **DavidBell said:**
> @WW using that typedef is pretty common, problem with the macro is it will fail if someone does
```
LONG x;
```
Yes, it will fail in that case, but that is not the use that .neo showed.  He showed
```

input_dev->keybit[LONG(BTN_TOUCH)] = BIT(BTN_TOUCH);

```
LONG(BTN_TOUCH) appears to be a cast; it is definitely not a declaration.

---

### Post by dwhitney67 on 2008-07-29
Can't go wrong with the following, unless LONG() is indeed a function doing something wild/bizarre:
[PHP]#define LONG(x) ((long)(x))
typedef long LONG;[/PHP]

---

