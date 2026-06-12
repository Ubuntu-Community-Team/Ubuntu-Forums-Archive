---
title: "unable to compile in GTK"
date: 2007-08-05
forum: Programming Talk
---

### Post by abadfish on 2007-08-05
I'm new to linux so please bear with me...

I successfully installed GTK 2.10.14 on Ubuntu 7.04.  I'm now going through the tutorial on GTK.org.  I'm trying to do the first program called base.c.  here is the code:

> 
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


I try to compile the program with the following (as per the tutorial):

> 
% gcc base.c -o base 'pkg-config --cflags --libs gtk+-2.0'


I get the following error messages:

> 
gcc: pkg-config --cflags --libs gtk+-2.0: No such file or directory
base.c:1:21: error: gtk/gtk.h: No such file or directory
base.c: In function ‘main’:
base.c:6: error: ‘GtkWidget’ undeclared (first use in this function)
base.c:6: error: (Each undeclared identifier is reported only once
base.c:6: error: for each function it appears in.)
base.c:6: error: ‘window’ undeclared (first use in this function)
base.c:10: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)


I'm assuming the problem is in the first line where its looking for pkgconfig.  I have pkgconfig stuff in two directories, /usr/local/lib/pkgconfig and /usr/lib/pkgconfig.  The pkgconfig in /usr/local/lib contains a folder called gtk+-2.0.

So I've added the following to my env:

> 
% export PKG_CONFIG_PATH=/usr/local/lib


I've also tried all of the following:

> 
% export PKG_CONFIG_PATH=/usr/local/lib

% export PKG_CONFIG_PATH=/usr/local/lib:/usr/lib

% export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

% export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig


None of those have allowed me to compile.


Can anybody shed some light on what I'm doing wrong?????

Thanks in advance.

---

### Post by abadfish on 2007-08-05
I found the problem.

I should be using backticks instead of single quote.  so instead of:

> 
gcc base.c -o base 'pkg-config --cflags --libs gtk+-2.0'


I should be doing:

> 
gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`


okay, so I'm one more step away from discarding my newb status  :)

---

### Post by SrdjaLinux on 2007-08-05
I have the same probl em..

Is there someone to know how to fix this?  :(

---

### Post by abadfish on 2007-08-05
> **SrdjaLinux said:**
> I have the same probl em..

Is there someone to know how to fix this?  :(

I just explained the solution in my last post.  Use backticks instead of single quotes when "encasing" the pkg-config part (see above - look very closely).

---

### Post by AlexThomson_NZ on 2007-08-05
> **SrdjaLinux said:**
> I have the same probl em..

Is there someone to know how to fix this?  :(

Have you got the gtk dev library installed?

---

### Post by vinutha on 2008-05-13
> **abadfish said:**
> I'm new to linux so please bear with me...

I successfully installed GTK 2.10.14 on Ubuntu 7.04.  I'm now going through the tutorial on GTK.org.  I'm trying to do the first program called base.c.  here is the code:



I try to compile the program with the following (as per the tutorial):



I get the following error messages:



I'm assuming the problem is in the first line where its looking for pkgconfig.  I have pkgconfig stuff in two directories, /usr/local/lib/pkgconfig and /usr/lib/pkgconfig.  The pkgconfig in /usr/local/lib contains a folder called gtk+-2.0.

So I've added the following to my env:



I've also tried all of the following:



None of those have allowed me to compile.


Can anybody shed some light on what I'm doing wrong?????

Thanks in advance.

i have same problem please help me

---

