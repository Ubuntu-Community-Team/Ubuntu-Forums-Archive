---
title: "GTK+ link error"
date: 2010-10-03
forum: Programming Talk
---

### Post by ceclauson on 2010-10-03
Hello,

First, thanks in advance for any help you can provide.

I'm starting out with GTK+, and I'm getting a link error.

Here is the source code:

[PHP]
#include <gtk/gtk.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {

	GtkWidget *window;

	gtk_init(&argc, &argv);

	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_widget_show(window);
	
	gtk_main();

	return EXIT_SUCCESS;
}
[/PHP]

Here is the makefile:

[PHP]
BIN_NAME = test
GTKFLAGS = `pkg-config --cflags --libs gtk+-2.0`
CFLAGS += $(GTKFLAGS)

.PHONY: default run

default: $(BIN_NAME)

run: default
	./$(BIN_NAME)

$(BIN_NAME): $(patsubst %.c, %.o, $(wildcard *.c))

[/PHP]

Here's the output from **pkg-config --cflags --libs gtk+-2.0**:

> 
-D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  


Here's the result of make:
```

cc   test.o   -o test
test.o: In function `main':
test.c:(.text+0x1c): undefined reference to `gtk_init'
test.c:(.text+0x28): undefined reference to `gtk_window_new'
test.c:(.text+0x36): undefined reference to `gtk_widget_show'
test.c:(.text+0x3b): undefined reference to `gtk_main'
collect2: ld returned 1 exit status
make: *** [test] Error 1

```

My /usr/lib directory has a libgtk-x11-2.0.so file.

After playing with it, I found that even if you tell ld to link against a library that doesn't exists, it still won't warn about the problem.  Is there any way to make ld issue a warning in this case?  It may help do debug the problem.

Thanks,
Cooper

---

### Post by pbrane on 2010-10-03
make sure you have the dev files. like libgtk2.0-dev. Also add **-W -Wall** to your CFLAGS. This will show you all warnings too. Try to avoid using **test** as a program name. there is already a */usr/bin/test*

An easy way to compile that particular file is with
```

gcc -W -Wall -o myprog $(pkg-config gtk+-2.0 --cflags --libs) myprog.c

```
replacing *myprog* with the name of your source file.

---

### Post by Some Penguin on 2010-10-03
> **ceclauson said:**
> 
After playing with it, I found that even if you tell ld to link against a library that doesn't exists, it still won't warn about the problem.  Is there any way to make ld issue a warning in this case?  It may help do debug the problem.


Well, if the compilation command that is actually being invoked is

```

cc   test.o   -o test

```

I'd say that the problem lies in how arguments are (not) being passed to the compiler, not what the compiler is doing with the arguments.

Perhaps try something less fancy, like

```

test:  test.o
   gcc -o test test.o $(CFLAGS)

```

?

---

### Post by ceclauson on 2010-10-03
Figured out the problem--I added the correct flags to CFLAGS, but not to LDFLAGS, so ld never got the libraries.

Corrected Makefile:

[PHP]
BIN_NAME = test
GTKFLAGS = `pkg-config --cflags --libs gtk+-2.0`
CFLAGS += $(GTKFLAGS)
LDFLAGS += $(GTKFLAGS)

.PHONY: default run

default: $(BIN_NAME)

run: default
	./$(BIN_NAME)

$(BIN_NAME): $(patsubst %.c, %.o, $(wildcard *.c))

[/PHP]

Cooper

---

