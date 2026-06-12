---
title: "GTK, C issue"
date: 2006-10-22
forum: Programming Talk
---

### Post by anti-net on 2006-10-22
I am trying out with GTK and C/C++ and i am trying some tutorials on [www.gtk.org/tutorial](www.gtk.org/tutorial) but having some issues with gtk.h 

I have had this problem before and I install libgtk2.0-dev([http://packages.ubuntu.com/dapper/libdevel/libgtk2.0-dev](http://packages.ubuntu.com/dapper/libdevel/libgtk2.0-dev)) which i was informed will sort my little problem but has't, not sure where to look now, Anyone able to help?

Thanks, Greg

---

### Post by Jessehk on 2006-10-22
You're are going to have to post the exact problems you're having in order for us to have any idea what the problem is.

---

### Post by anti-net on 2006-10-22
Opps Sorry the code I was trying was:
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
```
the errors I get when I compile it from Anjuta I get
"error: gtk/gtk.h"
"error: gtkWidget undeclared(first use in this function)
"error: (Each undeclared identifier is reported only once
"error: for each function it appears in.)
"error: 'window undeclard (first use in this function)
"error: 'GTK_WINDOW_TOPLEVEL' undeclared (frist use in this function)

I hope that is enough information to work out my problem.

---

### Post by po0f on 2006-10-22
anti-net,

What's the compiler command Anjuta is using to compile your program?  And try this from the command line:
```
$ gcc -Wall `pkg-config gtk+-2.0 --cflags --libs` -o mybinary mysource.c
```

---

### Post by mike41 on 2006-10-23
what is 'pkg-config'? How come without that cc option, it won't compile even though the header files are in fact in the include directory?

---

### Post by anti-net on 2006-10-23
I tryed what Po0f suggested and I get 
```
gtk2.c: In function ‘main’:
gtk2.c:6: error: ‘gtkWidget’ undeclared (first use in this function)
gtk2.c:6: error: (Each undeclared identifier is reported only once
gtk2.c:6: error: for each function it appears in.)
gtk2.c:6: error: ‘window’ undeclared (first use in this function)

``` 
from GCC. ](*,)

---

### Post by High|ander on 2006-10-24
paste the whole compiler output, not just the error

---

### Post by flerchjj on 2007-12-10
I have 2 actions that worked for me:

1. Make sure the glib dev packages are installed.
2. In Anjuta o to Project->Properties->Packages
   - add a module
   - add the gtk package

Hope this helps

---

### Post by geirha on 2007-12-10
> **anti-net said:**
> I tryed what Po0f suggested and I get 
```
gtk2.c: In function ‘main’:
gtk2.c:6: error: ‘gtkWidget’ undeclared (first use in this function)
gtk2.c:6: error: (Each undeclared identifier is reported only once
gtk2.c:6: error: for each function it appears in.)
gtk2.c:6: error: ‘window’ undeclared (first use in this function)

``` 
from GCC. ](*,)

It is called GtkWidget, not gtkWidget.

---

