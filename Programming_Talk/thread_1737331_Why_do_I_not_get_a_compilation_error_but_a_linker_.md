---
title: "Why do I not get a compilation error but a linker error?"
date: 2011-04-23
forum: Programming Talk
---

### Post by Hetepeperfan on 2011-04-23
Hello, 

I'm trying to learn a bit of GTK+. While I was trying to compile :
```
#include <stdlib.h>
#include <stdio.h>
#include <signal.h>
#include <gtk/gtk.h>

void quit (int rc)
{
    fprintf( stderr, "oops, ended prematurely %d\n", rc);
    exit(rc);
}

int main( int   argc,
          char *argv[] )
{
    /*Features added by me to handel kill and Ctrl-C signals.*/
    void (*prev_fn)(int);
    signal( SIGTERM, quit);
    signal( SIGINT, quit);
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_window_set_title (GTK_WINDOW(window), "Center default size = 400*300");
    gtk_window_set_default_size(GTK_WINDOW(window), 400,300);
    gtk_window_set_positon(GTK_WINDOW(window), GTK_WIN_POS_CENTER);

    g_signal_connect_swapped(G_OBJECT(window), "delete-event", G_CALLBACK(gtk_main_quit),NULL);

    gtk_widget_show (window);
    
    gtk_main ();
    
    return 0;
}
```I typed a typo :

 ```
   gtk_window_set_positon(GTK_WINDOW(window), GTK_WIN_POS_CENTER);

```This should have been :

 ```
   gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
 
```notice the 'i' ommision by me, stupid error, but once I figured it out I could deal with it.

My question is therefore the following: Why do I not get a compilation error, but only a error when the linker starts to work

```
$ gcc -o win_cent_400_by_300 main_cent.c `pkg-config --cflags --libs gtk+-2.0`
/tmp/ccDEvpPn.o: In function `main':
main_cent.c:(.text+0xf4): undefined reference to `gtk_window_set_positon'
collect2: ld returned 1 exit status

```
So once I corrected the typo the code worked exquisitly. However I want to understand why I didn't got a compilation error.

I hope anyone can explain this to me

Kind regards, maarten

---

### Post by r-senior on 2011-04-23
In older variants of C (C89/90), it is legal to use a function before it is defined. It assumes that it is declared *somewhere* and that it returns int. If you don't specify a standard (with the -std flag), gcc compiles as a GNU dialect of C90, hence this behaviour: You'll only find out when you link.

If you compile with the -Wall flag (warn all), it should give you a warning. If you compile with a C99 variant, e.g. -std=C99, it should give an error.

If you always compile with C99 of course, you run the risk of silently introducing features that don't exist in older standards. I tend to use the default standard with gcc and use -Wall.

---

### Post by Hetepeperfan on 2011-04-23
> **r-senior said:**
> In older variants of C (C89/90), it is legal to use a function before it is defined. It assumes that it is declared *somewhere* and that it returns int. If you don't specify a standard (with the -std flag), gcc compiles as a GNU dialect of C90, hence this behaviour: You'll only find out when you link.

If you compile with the -Wall flag (warn all), it should give you a warning. If you compile with a C99 variant, e.g. -std=C99, it should give an error.

If you always compile with C99 of course, you run the risk of silently introducing features that don't exist in older standards. I tend to use the default standard with gcc and use -Wall.


Hello r-senior,

Thanks for you answer, with warings on it indeed tells me that I'm using an implicitly defined function, for which the object code is not found while linking, but when I switch to either -std=c99 or -std=gnu99 it still compiles but with those flags it will print the same waring as with -Wall. 

Thanks!!

---

### Post by r-senior on 2011-04-23
Oh, OK. My mistake. I expected an error with -std=C99. I'll play around with that when I get time.

---

