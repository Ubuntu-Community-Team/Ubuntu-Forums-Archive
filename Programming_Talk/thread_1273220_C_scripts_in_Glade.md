---
title: "C scripts in Glade"
date: 2009-09-23
forum: Programming Talk
---

### Post by carlosgs91 on 2009-09-23
.

---

### Post by Linteg on 2009-09-23
> **carlosgs91 said:**
> 
1. How to add "links" to C functions from Glade, for example in a button called download I want it to refer to download(); function.

Take a look at the signals tab in Glade and create a handler for an appropriate signal (for example clicked for a button). As long as you have a function with the same name as the handler you specified in Glade accessible from the function where you create/load your window the call to gtk_builder_connect_signals should connect the signal to the function.

> **carlosgs91 said:**
> 
2. I want to know how to change the values of the objects. For example I have a statusbar called statusbar and I'd like to change its value from C language, how I do that?

You'll need to use gtk_builder_get_object to get a pointer to your object:
```

GtkWidget *my_button;
// gtk_builder_add_from_file etc.
my_button = GTK_WIDGET(gtk_builder_get_object(builder, "my_button"));

```
my_button can now be used like any other GtkButton. Using g_signal_connect it's of course possible to connect the button's clicked signal to a handler here too:
```

g_signal_connect(G_OBJECT(my_button), "clicked", G_CALLBACK(on_my_button_clicked), NULL);

```

---

