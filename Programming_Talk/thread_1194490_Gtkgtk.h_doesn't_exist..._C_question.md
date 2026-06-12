---
title: "Gtk/gtk.h doesn't exist... C question"
date: 2009-06-22
forum: Programming Talk
---

### Post by proboardslol on 2009-06-22
source:

```
#include <gtk/gtk.h>

int main()
{
    g_print ("Hello World\n");
}

```

got this

```
collin@lappylol:~/Desktop$ gcc fun.c -o Funlol.out
fun.c:1:21: error: gtk/gtk.h: No such file or directory
collin@lappylol:~/Desktop$ 


```

---

### Post by Can+~ on 2009-06-22
Stick to a tutorial instead of trying to guess:

[http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)

You'll need to link manually to gtk.

---

### Post by proboardslol on 2009-06-22
thanks, i did use a tutorial, just not a very good one i guess :\

---

### Post by Paul Miller on 2009-06-22
Linking isn't the issue; it's not even finding the header file.  That tells me you probably need to install libgtk1.2-dev or libgtk2.0-dev (pick the appropriate one).

---

### Post by SledgeHammer_999 on 2009-06-22
you don't tell gcc where to find gtk
you should type this:
```
gcc fun.c `pkg-config --libs --cflags gtk+-2.0` -o Funlol.out
```
After you isntall libgtk2.0-dev

---

### Post by Axis Mann on 2012-11-12
If you use single quote (') instead of the backtick (`) in the GCC command parameters, it won't compile, even if you did everything else ok.  I was getting the message "helloworld.c:3:21: error: gtk/gtk.h: No such file or directory" before I realized that the compile command is suppose to be "gcc helloworld.c -o helloworld `pkg-config --cflags --libs gtk+-2.0`" and not "gcc helloworld.c -o helloworld 'pkg-config --cflags --libs gtk+-2.0'" as I mistakenly typed.  You have to look closely to see the difference.  Dog nabbit Jim, it's a backtick (`), not a single quote (').

---

### Post by pbrane on 2012-11-12
you can also replace the **`pkg-config --libs --cflags gtk+-2.0`** with 
```

$(pkg-config --libs --cflags gtk+-2.0)

```

easier to read as text

also for more up to date tutorials try here:
[http://developer.gnome.org/gnome-devel-demos/stable/c.html.en]("http://developer.gnome.org/gnome-devel-demos/stable/c.html.en")

---

### Post by pbrane on 2012-11-12
didn't mean to post twice.

---

