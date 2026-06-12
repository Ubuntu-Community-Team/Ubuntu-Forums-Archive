---
title: "GTK problem"
date: 2012-05-14
forum: Programming Talk
---

### Post by cragwolf on 2012-05-14
After doing a clean install of 12.04 (and then downloading the necessary development packages) I'm having problems compiling the following simple gtk program:

```
#include <gtk/gtk.h>

int main( int   argc,
          char *argv[] )
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show  (window);
    
    gtk_main ();
    
    return 0;
}
```It works fine if I do the compiling and linking all at once:

```
gcc test.c -o test `pkg-config --cflags --libs gtk+-2.0`
```But if I try to compile only, with this:

```
gcc -c test.c `pkg-config --cflags gtk+-2.0`
```it fails with the following error message:

```
/tmp/ccLYcDS0.o: In function `main':
test.c:(.text+0x17): undefined reference to `gtk_init'
test.c:(.text+0x23): undefined reference to `gtk_window_new'
test.c:(.text+0x33): undefined reference to `gtk_widget_show'
test.c:(.text+0x38): undefined reference to `gtk_main'
collect2: ld returned 1 exit status

```This was never an issue in 11.04, so I wonder what I'm missing.

---

### Post by cragwolf on 2012-05-14
Sorry, ignore the above post. I'm an idiot. Works fine after all.

---

### Post by steeldriver on 2012-05-14
hmm yes I think that's the normal behavior for gcc - with no explicit target it will attempt to link and produce an executable with the default name "a.out" (failing in this case because of the missing libs)

in order to suppress the link phase you have to give it an explicit object file name e.g. "-o test.o"

---

