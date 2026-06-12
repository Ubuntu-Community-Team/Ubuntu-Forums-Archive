---
title: "[SOLVED] gtk+ programming"
date: 2008-09-03
forum: Programming Talk
---

### Post by luckydeveloper on 2008-09-03
i know kde was built in qt framework... but i want to try my hands on gtk+ programming.. i have kubuntu 8.04

is it possible to gtk+ programming in kde

---

### Post by Dojan5 on 2008-09-03
It should be possible to program GTK in KDE.

---

### Post by luckydeveloper on 2008-09-03
please throw me some points regarding that

---

### Post by cmay on 2008-09-03
yes. i have kubuntu (i replaced the desktops) and i can create gtk+ windows whit perl.you have to have the libraries installed .

---

### Post by dmizer on 2008-09-03
Moved to Programming Talk.

---

### Post by nvteighen on 2008-09-03
Install the libgtk2.0-dev package. If you don't have GTK+ installed, that will install it as a dependency.

Also install libgtk2.0-doc for the documentation.

---

### Post by luckydeveloper on 2008-09-03
> **nvteighen said:**
> Install the libgtk2.0-dev package. If you don't have GTK+ installed, that will install it as a dependency.

Also install libgtk2.0-doc for the documentation.


i wrote the program below.. 

#include <gtk/gtk.h>
int main (int argc,char *argv[])
{
  GtkWidget *window;
  /* Initialize GTK+ and all of its supporting libraries. */
  gtk_init (&argc, &argv);
  /* Create a new window, give it a title and display it to the user. */
  window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  gtk_window_set_title (GTK_WINDOW (window), "Hello World");
  gtk_widget_show (window);
  /* Hand control over to the main loop. */
  gtk_main ();
  return 0;
}


and tried to compile it with  
gcc new.c -o hello 'pkg-config --cflags gtk+-2.0' 'pkg-config --clibs gtk+-2.0'


but it is giving me the following error statements... 

gcc: pkg-config --cflags gtk+-2.0: No such file or directory
gcc: pkg-config --clibs gtk+-2.0: No such file or directory
new.c:1:21: error: gtk/gtk.h: No such file or directory
new.c: In function ‘main’:
new.c:4: error: ‘GtkWidget’ undeclared (first use in this function)
new.c:4: error: (Each undeclared identifier is reported only once
new.c:4: error: for each function it appears in.)
new.c:4: error: ‘window’ undeclared (first use in this function)
new.c:8: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)


please help:(

---

### Post by nvteighen on 2008-09-03
You'll laugh when you read what's your mistake... (A quite common one)

> **luckydeveloper said:**
> 
gcc new.c -o hello 'pkg-config --cflags gtk+-2.0' 'pkg-config --clibs gtk+-2.0'


Bad: don't use ' (quotes) use ` (backticks).

```

gcc new.c -o hello `pkg-config --cflags gtk+-2.0` `pkg-config --clibs gtk+-2.0`

```

That has to work.

---

### Post by luckydeveloper on 2008-09-03
> **nvteighen said:**
> You'll laugh when you read what's your mistake... (A quite common one)



Bad: don't use ' (quotes) use ` (backticks).

```

gcc new.c -o hello `pkg-config --cflags gtk+-2.0` `pkg-config --clibs gtk+-2.0`

```

That has to work.



thanks.. it worked...that was my mistake

---

