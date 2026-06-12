---
title: "[SOLVED] sdl"
date: 2008-03-06
forum: Programming Talk
---

### Post by vikasmk on 2008-03-06
hi, i'm i installed the sdl library using synaptic but how do i include them in my program , i dont know where they go once downloaded.

---

### Post by irrdev on 2008-03-06
The main SDL .a and .so files can be found at **/usr/lib/libSDL.a** and **/usr/lib/libSDL.so** respectively. The SDL include files can be found in the folder **/usr/include/SDL/**

---

### Post by mike_g on 2008-03-06
To include SDL in your program:
```
#include "SDL/SDL.h"
```
To Link SDL to your project:
```
gcc -Wall main[COLOR="DarkRed"].c -lSDL[/COLOR]
```

---

### Post by hod139 on 2008-03-06
> **mike_g said:**
> To include SDL in your program:
```
#include "SDL/SDL.h"
```To Link SDL to your project:
```
gcc -Wall main[COLOR=DarkRed].c -lSDL[/COLOR]
```

This is not the [recommended]("http://www.libsdl.org/faq.php?action=listentries&category=2#19") way.  To include SDL in your program:
```

#include "SDL.h"

```

To build
```

 gcc -Wall `sdl-config --cflags --libs` main.c

```

---

### Post by vikasmk on 2008-03-06
thanx i also saw all the other libraries i had previously installed but didnt know where they went

---

### Post by kaens on 2008-03-06
> **vikasmk said:**
> thanx i also saw all the other libraries i had previously installed but didnt know where they went

For future reference, if you ever need to know what files got put where by a package you can do the following:

```

dpkg --contents /var/cache/apt/archives/packagename

```

---

