---
title: "can't compile a simple c gtk in Kdevelop?"
date: 2006-08-31
forum: Programming Talk
---

### Post by loell on 2006-08-31
i installed kdevelop and copy paste this in
main.c inside a project

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

from [here]("http://www.gtk.org/tutorial/c39.html")

yes the code does compile successfuly if compiled from the command line with this

gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`

i've read a little about the kdevelop docs, but i can't seem to compile this from Kdevelop IDE

i keep geting this error

```
 error: gtk/gtk.h: No such file or directory

```

and yes i have the gtk-dev installed. perhaps some of you know a little bit about makefiles?

---

### Post by Bob Unitt on 2006-12-06
Loell, I have exactly the same problem - did you ever find the answer ?

---

### Post by Bob Unitt on 2006-12-06
> **Bob Unitt said:**
> Loell, I have exactly the same problem - did you ever find the answer ?

I've now found the answer - so, for anybody else whose desperate search leads them to this thread:-

[INDENT]Select the KDevelop menu item 'Project Options',
Select the tab 'Configure Options',
Copy the string **`pkg-config --cflags --libs gtk+-2.0`** into the fields 'CCPFLAGS' and 'LDFLAGS'.
Repeat for all three configurations (drop down list at top of window).[/INDENT]

HTH

---

### Post by loell on 2006-12-07
its been a while since i posted this, :) 

but with anjuta , its more easier, just select gtk project , and all makefiles and configuration will be handled by anjuta.

---

### Post by Bob Unitt on 2006-12-07
> **loell said:**
> its been a while since i posted this, :) but with anjuta , its more easier, just select gtk project , and all makefiles and configuration will be handled by anjuta.

Thanks, I'll give it a try; but I'm not clear if these IDE's can interfere with each other - do I need to uninstall KDevelop first, or will they co-exist peacefully ?

---

### Post by loell on 2006-12-07
yeah they can coexist with each other , but are you on edgy or dapper? cause if you're in dapper its good to go , but if your on edgy the version of anjuta on edgy is trash ,

you can install the older version of anjuta on edgy by following this [Thread]("http://www.ubuntuforums.org/showthread.php?t=288480&highlight=edgy+anjuta")

---

### Post by Bob Unitt on 2006-12-07
> **loell said:**
> yeah they can coexist with each other , but are you on edgy or dapper? cause if you're in dapper its good to go , but if your on edgy the version of anjuta on edgy is trash

I'm on Dapper, so I'll give it a try (but probably not till the weekend).

---

