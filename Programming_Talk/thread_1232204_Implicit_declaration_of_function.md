---
title: "Implicit declaration of function"
date: 2009-08-05
forum: Programming Talk
---

### Post by swappo1 on 2009-08-05
I am getting the following errors and I am not sure what the problem is.
```
cc -O2 -Wall -Werror -ansi `pkg-config gtk+-2.0 gstreamer-0.10 --cflags` -c main.c
In file included from main.c:2:
file_menu.h:4: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
file_menu.h:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cc1: warnings being treated as errors
main.c: In function ‘main’:
main.c:40: error: implicit declaration of function ‘create_menu_bar’
main.c:40: error: assignment makes pointer from integer without a cast
make: *** [main.o] Error 1

```
In main.c I have a function call
```
menu_bar = create_menu_bar(window);
```
In file_menu.h I have the function prototypes
```
GtkActionEntry mainwindow_action_entries[];
GtkWidget *create_menu_bar(GtkWidget *window);
```
```
GtkActionEntry mainwindow_action_entries[] =
{
    Code goes here
};

GtkWidget *create_menu_bar(GtkWidget *window)
{
    Code goes here
}

```
What am I doing wrong?  Both main.c and file_menu.c have #include file_menu.h.

---

### Post by ibuclaw on 2009-08-05
You are doing nothing wrong, all what is happening is that the type **GtkWidget** has not been declared.


try adding:

```
#include <gtk/gtk.h>
```

Regards
Iain

---

