---
title: "Can't #define ushort"
date: 2012-09-03
forum: Programming Talk
---

### Post by bird1500 on 2012-09-03
Hi,
I define this:
#define ushort unsigned short

in shared.h and when I include it in a class header like this:

//class Server.h
#include "shared.h"
...
ushort port;

I get errors when trying to compile:

> 
make
[ 25%] Building CXX object CMakeFiles/ufbio.dir/Server.cpp.o
In file included from /usr/include/stdlib.h:320:0,
                 from /media/docs/dev/ufbio/Server.cpp:4:
/usr/include/x86_64-linux-gnu/sys/types.h:152:1: error: duplicate &#8216;unsigned&#8217;
/usr/include/x86_64-linux-gnu/sys/types.h:152:1: error: duplicate &#8216;short&#8217;
/usr/include/x86_64-linux-gnu/sys/types.h:152:28: error: declaration does not declare anything [-fpermissive]
make[2]: *** [CMakeFiles/ufbio.dir/Server.cpp.o] Error 1
make[1]: *** [CMakeFiles/ufbio.dir/all] Error 2
make: *** [all] Error 2

What am I doing wrong?


EDIT: for some reason including <sys/types.h> **after** including "shared.h" causes these errors.

---

### Post by ofnuts on 2012-09-03
> **bird1500 said:**
> Hi,
I define this:
#define ushort unsigned short

in shared.h and when I include it in a class header like this:

//class Server.h
#include "shared.h"
...
ushort port;

I get errors when trying to compile:

What am I doing wrong?


EDIT: for some reason including <sys/types.h> **after** including "shared.h" causes these errors.
Maybe that should be a typedef and not a #define anyway.

---

### Post by bird1500 on 2012-09-03
> **ofnuts said:**
> Maybe that should be a typedef and not a #define anyway.
Thanks, I have completely forgotten about typedef. As far as I understand, typedef is basically a better #define.

---

### Post by trent.josephsen on 2012-09-03
> **bird1500 said:**
> Hi,
I define this:
#define ushort unsigned short

For the love of $deity, WHY?

I agree that the feature you really want is typedef, but why would you want to typedef a built-in type WITH A SLIGHTLY SHORTER VERSION OF THE SAME NAME?

While you're at it, why don't you

```
typedef int i;
typedef char c;
typedef short s;
...
```

And since that's so repetitive, maybe we can make it even shorter and less readable:

```
#define t typedef
t int i;
t char c;
...
```

Oh, while we're at it, why don't we throw in some extra #defines, you know, just to save keystrokes:

```
#define f for
#define w while
#define p printf
```

Sorry to be rude, but unless your goal is to make C look like APL, why don't you use the names that are provided?

---

### Post by bird1500 on 2012-09-03
To me "ushort" is much shorter than "unsigned short", just as "uint" is much shorter than "unsigned int".
Vala and D did the same thing, there's also gnu's guchar, so it's hardly a pedantic idea.

---

### Post by trent.josephsen on 2012-09-03
> **bird1500 said:**
> To me "ushort" is much shorter than "unsigned short", just as "uint" is much shorter than "unsigned int".
Conciseness is a poor excuse for making code *more complex* and *less readable*.
> Vala and D did the same thing, there's also gnu's guchar, so it's hardly a pedantic idea.

Vala and D are different languages from C and are free to name their types however they want. As for [GLib's basic types](http://developer.gnome.org/glib/stable/glib-Basic-Types.html), well, I can think of one or two weak justifications for why they would do that, but "so-and-so did it" is an equally poor excuse for typedef abuse. Justify yourself, don't point to what other people did.

---

### Post by bird1500 on 2012-09-03
> **trent.josephsen said:**
> Conciseness is a poor excuse for making code *more complex* and *less readable*.


Vala and D are different languages from C and are free to name their types however they want. As for [GLib's basic types]("http://developer.gnome.org/glib/stable/glib-Basic-Types.html"), well, I can think of one or two weak justifications for why they would do that, but "so-and-so did it" is an equally poor excuse for typedef abuse. Justify yourself, don't point to what other people did.

It doesn't matter if Vala and D are different languages - you  don't get the point, and I can do with C++ whatever I want cause C++ is no less "free" than Vala and D, and it certainly doesn't have to obey your angry pedantic dogmas. And I don't care if you like it or not, trust me, I don't care what is more readable to you, just like the gnu/Vala/D/whatever folks did - we don't care about random people ranting around. If you're in a bad mood take a hike, but don't try teaching us about your naive worldview.

---

### Post by trent.josephsen on 2012-09-03
...

---

### Post by ofnuts on 2012-09-04
> **bird1500 said:**
> I don't care what is more readable to you, just like the gnu/Vala/D/whatever folks did - **we** don't care about random people 
Just love that "we"...

---

### Post by the_unforgiven on 2012-09-04
> **bird1500 said:**
> Hi,
I define this:
#define ushort unsigned short

in shared.h and when I include it in a class header like this:

//class Server.h
#include "shared.h"
...
ushort port;

I get errors when trying to compile:

What am I doing wrong?


EDIT: for some reason including <sys/types.h> **after** including "shared.h" causes these errors.
That's because they're **already** typedefed in <sys/types.h>

You're not the only one with this requirement - standard C library has had a lot of lazy users already :p

I'd rather trust the standard libraries because their designers are a lot more careful in writing portable code ;)

---

### Post by Bachstelze on 2012-09-04
> **the_unforgiven said:**
> That's because they're **already** typedefed in <sys/types.h>

You're not the only one with this requirement - standard C library has had a lot of lazy users already :p

I'd rather trust the standard libraries because their designers are a lot more careful in writing portable code ;)

ushort is not mandated by any standard, and is probably there only so as to not break old and bad code. There is zero excuse for using it nowadays, and in general anything that comes from the GNU folks should be treated with great suspicion.

*EDIT:* But then again, OP is doing C++, not C, and you know what Linus said about C++...

---

### Post by bird1500 on 2012-09-04
> **Bachstelze said:**
> 
*EDIT:* But then again, OP is doing C++, not C, and you know what Linus said about C++...
Linus said arrogant stuff about C++ as a kernel dev, which makes sense.

Desktop apps are a completely different area.
Doing desktop apps in C to me is a pain, I tried it, it's verbose, lots of casting back and forth cause it doesn't have inheritance, lots of crazy code just to extend a class and  you have to use third party libs or invent the wheel yourself for things like stringstream.

Anyway, as a language for desktop apps, I hate C with a passion, but for low level stuff like kernel & drivers - C is more natural.

Of course, even if you write the sky is blue, someone in the internet won't agree, so please let's keep off the talks about which language is the best, it's been argued a gazillion times.

---

