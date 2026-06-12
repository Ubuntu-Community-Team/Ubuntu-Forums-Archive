---
title: "[SOLVED] using the C++ preprocessor glut"
date: 2007-12-16
forum: Programming Talk
---

### Post by troxy18 on 2007-12-16
Dilemma: I have an Imac and a laptop that runs ubuntu.  Programming opengl and glut in these environments and in windows visual studio require different #include statements, mainly different syntax and capitalization.

Mac xcode
```
#include <OpenGL/gl.h>
#include <OpenGL/glu.h>
#include <GLUT/glut.h>
```

Ubuntu
```
#include <GL/gl.h>
#include <GL/glu.h>
#include <GL/glut.h>
```

Windows
```
#include <windows.h> //suitable when using Windows 95/98/NT/2000/XP
#include <gl/Gl.h>
#include <gl/Glu.h>
#include <gl/glut.h>
```

What is the best way to wrap these together in #ifdef statements so my professor can just run the code on his windows visual studio machine?

---

### Post by Majorix on 2007-12-16
That is what the devs of today talk about: Portability. Some libraries are only available to some specific OS, some have different names on each (like in your case) etc. To overcome this, I would try an approach like this.
-Use a code to get the OS info from the computer that the program is running on. Store the info you got in a global variable.
-Make the code search in that variable for familiar words like POSIX, UNIX, Windows, DarwinOS etc.
-Then do something like this:
#ifdef Windows
//Include Windows headers
#endif

These lines will hopefully give you an idea. Improve on it and include it in your code. Good luck!

---

### Post by LaRoza on 2007-12-16
> **troxy18 said:**
> 
What is the best way to wrap these together in #ifdef statements so my professor can just run the code on his windows visual studio machine?

Have the Windows code be the default.

When you submitt it, just make sure the LINUX and MAC defines don't exist.

```

#if LINUX 
    //Linux headers
#elif MAC
    //Mac headers
#else        
    //Windows headers
#endif


```

---

### Post by Auria on 2007-12-16
I know that for OS X headers you can check #ifdef __APPLE__
There must be similar defines for linux and windows that are always defined

---

### Post by Majorix on 2007-12-16
^Yes they also come pre-defined I think. So no need to fetch on your own. But then you have to learn the macro names by heart. It's your choice.

---

### Post by troxy18 on 2007-12-16
Playing around I got this to work. I found the original parts in the header for glut.h in xcode and tested on my mac, my ubuntu laptop, and a friends windows visual studio.

```
#if defined(_WIN32)
#  include <windows.h>
#include <gl/Gl.h>
#include <gl/Glu.h>
#include <gl/glut.h>
#endif

#if defined(__APPLE__) || defined(MACOSX)
#include <OpenGL/gl.h>
#include <OpenGL/glu.h>
#include <GLUT/glut.h>
#else //linux as default
#include <GL/gl.h>
#include <GL/glu.h>
#include <GL/glut.h>
#endif
```

edit: Marking thread as solved

---

### Post by Majorix on 2007-12-17
Hi, glad you got it working.

I have a question, are the parentheses around the OS variables necessary? C++ Preprocessor speaks a different language than C++, so I don't think they would be necessary. I am pointing this out so you realize that fact :)

---

### Post by moma on 2007-12-17
Study also this list of pre-defined operating system macros
[http://predef.sourceforge.net/preos.html](http://predef.sourceforge.net/preos.html)

Outras guias importantes
[http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)

Merry xmas,
$ sudo apt-get install xsnow
$ xsnow # on your desktop

---

