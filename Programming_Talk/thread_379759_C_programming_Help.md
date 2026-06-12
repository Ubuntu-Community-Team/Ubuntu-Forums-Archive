---
title: "C programming Help"
date: 2007-03-08
forum: Programming Talk
---

### Post by MikeyRibbs on 2007-03-08
Okay, so I'm starting to learn C programming and I am using TCC to compile and Anjuta to code. Once I turn the files into .o files it wont let me open them? It's probably a n00b problem but can anyone help me out? I just want to know how to open .o files.

---

### Post by yabbadabbadont on 2007-03-08
You don't.  Those are compiled object files, not executables.  You need to link them before they will be executable.

---

### Post by MikeyRibbs on 2007-03-08
So how do I make it an executable?

---

### Post by yabbadabbadont on 2007-03-08
> **yabbadabbadont said:**
> You need to link them before they will be executable.

:D

---

### Post by MikeyRibbs on 2007-03-08
I feel like such a noob and I'm sorry that I have to ask but, how do I link them?

---

### Post by yabbadabbadont on 2007-03-08
[http://howtos.linux.com/howtos/HOWTO-INDEX/programming.shtml](http://howtos.linux.com/howtos/HOWTO-INDEX/programming.shtml)

Hopefully that will provide some of the information you will need.  Other than that, I would suggest searching for "linux programming tutorial" and possibly purchasing a book or two on the subject.  :D

---

### Post by monkeyking on 2007-03-08
just try to use some simple tools to start with.

open a plain old text editor, and write the following.
```

#include "stdio.h"
int main(){
    printf("Hello world \n");
}

```

save as firstProg.c

Go to a terminal and write

```

gcc -o myProg firstProg.c

```
now it compiles and makes an "exe".
and you can run it with
```

./myProg

```

I think these hi-end programming enviroments are a little too much for beginners.

---

### Post by Wybiral on 2007-03-08
> **monkeyking said:**
> I think these hi-end programming enviroments are a little too much for beginners.

I agree, in fact... I do a lot of complex programming and ALL of my compiling is done from either the command line or makefiles (which operate on the same principal as the command line).

---

### Post by cronholio on 2007-03-09
If you use Anjuta, just "Build all" and you will get an executable in your "src" sub-directory.

---

