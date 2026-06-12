---
title: "LD_PRELOAD does not work :("
date: 2009-02-05
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-02-05
I'm trying to make a simple cheat, for gnomine.

Goal is modify hint function to not raise timer.


But before doing anything, I want to see if it works. It doesn't. No any effect.

I downloaded gnome-games source, and added cheat.c in gnomine directory. Here's cheat.c:
```

#if 0
#!/bin/sh
gcc -std=gnu99 -I../libgames-support `pkg-config --cflags --libs gtk+-2.0` cheat.c -shared -fPIC -o cheat.so
exit
#endif

#include <stdio.h>
#include "minefield.h"

gint gtk_minefield_hint( GtkMineField * mfield )
{
    printf( "Sorry, no hint function\n" );
    return 123;
}

```
As you can see, making cheat.c executable and executing it will compile itself.

Now I got cheat.so. But it doesn't do anything:
```

$ LD_PRELOAD=./cheat.so gnomine

```
I just get gnomine, with fully-functioning hint function.


I read about that LD_PRELOAD thing from here: [http://neworder.box.sk/newsread.php?newsid=13857](http://neworder.box.sk/newsread.php?newsid=13857)

What's wrong? Why hint function still works, instead of printing "Sorry, no hint function"?

---

### Post by snova on 2009-02-05
I'm not entirely certain of the mechanisms behind shared libraries, but I don't think LD_PRELOAD will do you any good if the function is defined in the program itself- only if it were in a shared library.

---

