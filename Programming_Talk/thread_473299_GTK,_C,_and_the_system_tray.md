---
title: "GTK, C, and the system tray"
date: 2007-06-13
forum: Programming Talk
---

### Post by ceeg on 2007-06-13
Is there any example code for a GTK skeleton in C that serves as a system tray application?

---

### Post by Izkata on 2008-01-28
~bump~ because I'm wondering the same

(This thread is currently the second result on Google for "Linux System Tray C")

---

### Post by lnostdal on 2008-01-28
have you seen [http://library.gnome.org/devel/gtk/stable/GtkStatusIcon.html](http://library.gnome.org/devel/gtk/stable/GtkStatusIcon.html) ..?

edit: well, you did ask for an example, but it should be simple to figure out based on that doc .. if you insist (after trying and failing, ofc.) i could create a short example

---

### Post by Izkata on 2008-01-29
I haven't seen that...

After a quick Google search for an init error, this is what I came up with so far:

```
#include <gtk/gtk.h>
#include <stdlib.h>

void Testing()
{
   printf("Clicked");
}

int main(int argc, char *argv[])
{
   gtk_init(&argc, &argv);
   struct GtkStatusIcon *MyIcon;
   MyIcon = gtk_status_icon_new_from_file("/home/izkata/TestIcon.png");
   gtk_status_icon_set_visible(MyIcon, TRUE);

   gtk_main();
}
```

Although it compiles with 2 warnings that I'm not sure about, it shows up just fine on Gnome's Notification Area, but not trayer (which I use on Enlightenment).

```
SystrayTest.c: In function ‘main’:
SystrayTest.c:13: warning: assignment from incompatible pointer type
SystrayTest.c:14: warning: passing argument 1 of ‘gtk_status_icon_set_visible’ from incompatible pointer type
```

Unfortunately, I can't figure out how to make it actually *do* something...  My guess is with the "activate" and "popup-menu" signals, but I don't understand their descriptions.

---

### Post by a sandwhich on 2011-02-22
~bump~
I find this interesting and somewhat related to a project I am doing now.

---

### Post by PaulM1985 on 2011-02-24
I found this:

[http://blog.sacaluta.com/2007/08/gtk-system-tray-icon-example.html](http://blog.sacaluta.com/2007/08/gtk-system-tray-icon-example.html)

Good luck

Paul

---

### Post by a sandwhich on 2011-02-24
I converted izkatas sample above to c++ and it returned no errors when compiling.  I found that sacaluta post a while after reading this. It returned the same errors as above when I compiled it in c, yet when I switched it to c++ there were no errors.

---

