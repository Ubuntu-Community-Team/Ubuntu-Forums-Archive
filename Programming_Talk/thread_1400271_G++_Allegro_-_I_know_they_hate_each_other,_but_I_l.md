---
title: "G++ Allegro - I know they hate each other, but I love g++"
date: 2010-02-06
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-06
Bearing in mind the title, I want to compile C++ executables with Allegro in order to start making basic (very basic) games. 

One major problem, is that g++ can't seem to find it. I don't use Dev C++ mainly because the last time I installed it on Windows it gave me a BIOS virus. (And that was from the main site). 

On the other hand, how do I link the allegro libraries to g++. 

I have installed a number of Allegro packages from syn apt, and that's as far as I'm going at the moment.

If someone has a link to an online tutorial for this I'd be much appreciated as the Allegro site is very unclear.

---

### Post by dwhitney67 on 2010-02-06
"I pity the fool"  that use Windows with Dev C++ or even cygwin.  If you are using Ubuntu, then the allegro library should be installed within /usr/lib.  Header files within /usr/include.

What exactly is the problem you are having?  Please don't put the blame on g++ or Allegro.

---

### Post by Ravenshade on 2010-02-07
Oh I'm not blaming either. It's just g++ can't find Allegro. 

I insert the code and try to compile but for some reason G++ can't find the file. For instance 

#include <allegro.h> 

It can't find it.

---

### Post by gusnan on 2010-02-07
try something like
```

g++ myprogram.cpp -o myprogram `allegro-config --libs --cflags`

```(These are backticks (`), not standard ticks (').)

---

### Post by Ravenshade on 2010-02-07
Would I have to use that every time (I haven't tried it just yet, not on the same computer)

---

### Post by gusnan on 2010-02-07
> **Ravenshade said:**
> Would I have to use that every time (I haven't tried it just yet, not on the same computer)

If compiling from a command-line using g++, yes. - That is what we have makefiles for - adding it to a makefile gives us the option to compile with a simple "make" command and still get all necessary compile-flags set, but this is a bigger topic.

---

