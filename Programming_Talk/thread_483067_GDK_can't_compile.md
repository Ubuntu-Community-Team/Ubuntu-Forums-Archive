---
title: "GDK: can't compile"
date: 2007-06-24
forum: Programming Talk
---

### Post by taipoh on 2007-06-24
I wrote a simple GDK program to set a window to always on bottom.  However, when I try to compile it (g++ main.cpp), I get a zillion errors:

"xxxx was not declared in this scope", etc

```

  1 #include "/usr/include/gtk-1.2/gdk/gdk.h"
  2 
  3 int main()
  4 {
  5         GdkWindow* gwnd = gdk_window_at_pointer();
  6 
  7         gdk_window_set_keep_below( gwnd, true );
  8  
  9         return 0;
 10 }

```


Also, is it possible to get a GdkWindow* by name?

---

### Post by geraldm on 2007-06-25
Hello,
The command
g++ main.cpp

will never work for a GDK program.  Learn to use a Makefile.

Enter into the Makefile the locations of the include directories, and 
libraries when linking, and all your compiler-directing flags.
For a simple starter GDK application, a search of the web should
provide some examples.

Best regards,
Gerald

---

### Post by moshy on 2007-06-27
Did you get this working, I'm having the same problem, could you post your Makefile please

---

### Post by leibowitz on 2007-06-27
Doublepost: See next msg.

---

### Post by leibowitz on 2007-06-27
I don't know what you are trying to do in the first Post.

Anyway, I will try to explain some things so you can both understand how it works.

taipoh: 
First it's better to include with <file.h>, not "file.h". The last one is to include your headers file. If you put <file.h>, then it will look in other include paths to try to find the files.

It means you don't need the full path anymore.

```
#include <gdk/gdk.h> 
```

Next, don't try to g++ it. It's only C, so gcc will be fine. This means you need to rename your main.cpp to main.c because gcc will refuse to compile any .cpp

Then you can use pkg-config to get information about gdk package

This will do the trick:
> gcc `pkg-config --libs --cflags gdk` main.c -o outputfile.bin

Also you can add more package, if you intend to use anything more than just gdk.

For example, a GTK application:
> gcc `pkg-config --libs --cflags gtk+-2.0` main.c -o outputfile.bin


I can't help you more. I know it reports error about gdk_window_at_pointer so I would suggest you go look the gdk documentation first, and try to get your hand on a good tutorial. It would help a lot.


moshy: look at gcc string I just pasted. with pkg-config you can compile things. No need of makefile here. 

If you still want a makefile, than paste this:
```
all:
	gcc `pkg-config --libs --cflags gtk+-2.0` main.c -o outputfile.bin
```

This need to be called "Makefile" and be in the source directory. Note that there is a tabulation after any "target:" line. Otherwise it will complain.

That's it.

If you want a better Makefile, you will see that it's more complicated and you must stay away from them at least in the beginning.

```
CC=gcc
LDFLAGS=`pkg-config --libs gtk+-2.0`
CFLAGS=-c `pkg-config --cflags gtk+-2.0`
SOURCES=main.c
OBJECTS=$(SOURCES:.c=.o)
EXECUTABLE=output.bin

all:	$(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

.c.o:
	$(CC) $(CFLAGS) $< -o $@

```

I don't understand everything in it. It just works on every SOURCES files. So if you add another file to your project, just add the name:
> SOURCES=main.c otherfile.c onemore.c

And adapt this to what you want:
> EXECUTABLE=output.bin

---

