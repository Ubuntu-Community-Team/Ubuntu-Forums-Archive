---
title: "[C] compilation problem"
date: 2009-03-18
forum: Programming Talk
---

### Post by sujoy on 2009-03-18
I wrote a bare minimal gtk code, just to open and close the window. Instead of writing the callback functions in the same file, I put it in another file. However, now I cant seem to be able to compile the program.

main.c
```
#include <gtk/gtk.h>
#include "callback.h"

int main (int argc, char *argv[])
{
  GtkWidget *main_window;

  gtk_init (&argc, &argv); //edited later
  main_window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  gtk_window_set_title (GTK_WINDOW (main_window), "Contacts");

  g_signal_connect (G_OBJECT (main_window), "destroy", G_CALLBACK (on_main_window_destroy), NULL);

  gtk_widget_show_all (main_window); //edited later
  gtk_main ();
  return 0;
}
```

callback.h
```

static void on_main_window_destroy (GtkWidget *, gpointer);
```

callback.c
```
#include <gtk/gtk.h>
#include "callback.h"

static void on_main_window_destroy (GtkWidget *main_window, gpointer data)
{
  gtk_main_quit();
}
```

Makefile
```

CC = gcc

INCLUDE = `pkg-config --cflags gtk+-2.0` 

LIB = `pkg-config --libs gtk+-2.0` 

all: sample

callback.o:	callback.c callback.h
	$(CC) -c callback.c -o callback.o $(INCLUDE)

main.o: main.c
	$(CC) -c main.c -o main.o $(INCLUDE)

sample: main.o callback.o
	$(CC) -o sample main.o callback.o $(LIB)

.PHONY: clean

clean:
	rm callback.o main.o sample
```


and here is what I get on running 'make'
```
[sujoy::intel][~/work/PROJECT_CONTACTS]% make
gcc -c main.c -o main.o `pkg-config --cflags gtk+-2.0` 
callback.h:1: warning: &#8216;on_main_window_destroy&#8217; used but never defined
gcc -c callback.c -o callback.o `pkg-config --cflags gtk+-2.0` 
gcc -o sample main.o callback.o `pkg-config --libs gtk+-2.0` 
main.o: In function `main':
main.c:(.text+0x46): undefined reference to `on_main_window_destroy'
collect2: ld returned 1 exit status
make: *** [sample] Error 1
[sujoy::intel][~/work/PROJECT_CONTACTS]% 
```

any help is appreciated :)

---

### Post by the_unforgiven on 2009-03-18
Remove the static from the callback function declaration in callback.h - instead, make it extern.
callback.h:
```

#ifndef __CALLBACK_H
#define __CALLBACK_H

extern void on_main_window_destroy (GtkWidget *, gpointer);

#endif /* __CALLBACK_H */

```
This should work - hopefully :p.

---

### Post by WW on 2009-03-18
You have declared the function in callback.c to be 'static', so this function will not be visible outside of callback.c (even if you declare it your header file).

---

### Post by the_unforgiven on 2009-03-18
> **WW said:**
> You have declared the function in callback.c to be 'static', so this function will not be visible outside of callback.c (even if you declare it your header file).
I was about to reply with that :)

static access modifier makes the definition local to the translation unit. So, it's not visible outside of the translation unit.

---

### Post by sujoy on 2009-03-18
thanks for the help guys. yes i didnt know about static making things local. :P
it works great now :)

EDIT: i figured out, i also forgot to call gtk_init and gtk_widget_show

---

### Post by dwhitney67 on 2009-03-18
> **the_unforgiven said:**
> Remove the static from the callback function declaration in callback.h - instead, make it extern.
callback.h:
```

#ifndef __CALLBACK_H
#define __CALLBACK_H

extern void on_main_window_destroy (GtkWidget *, gpointer);

#endif /* __CALLBACK_H */

```
This should work - hopefully :p.
I do not believe the 'extern' is required.

---

### Post by the_unforgiven on 2009-03-18
> **dwhitney67 said:**
> I do not believe the 'extern' is required.
Yes, it's not *necessary*, but good to keep it consistent with standard headers :)
I missed out that it was defined static in the C file as well - which was the real cause of the problem.

---

