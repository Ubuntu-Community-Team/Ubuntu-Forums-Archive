---
title: "gtk programming"
date: 2010-02-21
forum: Programming Talk
---

### Post by nagaraj dr on 2010-02-21
hai.. plz help me 


i just started with this gtk stuff so i just wanted to make sure all d headers r proper r not, so i just keyed these lines in test.c
 #include<gtk/gtk.h>
#include<gdk/gdk.h>
#include<gtk/gtkwidget.h>
int main()
{

    GtkWidget *form;
    return 0;
}

compiled no errors  but when i tried to include gtkform.h,   gtkmainwindow.h  and some more   it is showing error...
it is obvious because there is no gtkform.h in my gtk 2.0 directory ... how do i fix this

---

### Post by SledgeHammer_999 on 2010-02-21
Have you downloaded through synaptic the appropriate dev files? The package name for gtk+ headers is **libgtk2.0-dev**.

---

### Post by dwhitney67 on 2010-02-21
> **SledgeHammer_999 said:**
> Have you downloaded through synaptic the appropriate dev files? The package name for gtk+ headers is **libgtk2.0-dev**.

Correct; then one also needs to specify the locations of the header files and the library files.  Something like:

```

gcc `pkg-config gtk+-2.0 --cflags` -c MyFile.c

gcc MyFile.o 'pkg-config gtk+-2.0 --libs` -o myapp

```

Of course, for a single module, this would probably work:
```

gcc MyFile.c `pkg-config gtk+-2.0 --cflags --libs` -o myapp

```

---

### Post by nvteighen on 2010-02-21
Hm... you should need just to #include <gtk/gtk.h>... Everything else is automatically included, save really unusual stuff, IIRC.

---

### Post by SledgeHammer_999 on 2010-02-21
> **dwhitney67 said:**
> Correct; then one also needs to specify the locations of the header files and the library files.  Something like:

```

gcc `pkg-config gtk+-2.0 --cflags` -c MyFile.c

gcc MyFile.o 'pkg-config gtk+-2.0 --libs` -o myapp

```

Of course, for a single module, this would probably work:
```

gcc MyFile.c `pkg-config gtk+-2.0 --cflags --libs` -o myapp

```

Yeah I already told him that [here](http://ubuntuforums.org/showthread.php?t=1050070&page=13) before urging him to create a new thread...

---

### Post by nagaraj dr on 2010-02-21
In our classes we were thought about mobile gui framework of samsung linux..& we are using ecllipse ide were in we include headers like gtkmainwindow.h ,gtkform.h.. so i was after those headers in my system...  
i checked some examples which dont have those headers  they all worked fine i got absolute result.. so, my conclusion is, there is nothing called as mainwindow , forms in pc world they are all mobile OS APIs  

correct me if i am wrong..

---

### Post by nagaraj dr on 2010-02-21
thank u every one it helped me a lot..

---

