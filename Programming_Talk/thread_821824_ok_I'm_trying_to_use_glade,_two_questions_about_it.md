---
title: "ok I'm trying to use glade, two questions about it..."
date: 2008-06-07
forum: Programming Talk
---

### Post by davbren on 2008-06-07
Hey, I'm trying to start a project which will include *a form* of word processor. I've attached what I've done so far in glade. The first of my questions is, how do I do the main programming once I've finished? The second is more to do with the layout. In the middle I want a blank page like in any word processor. How do I get that and type on it??

Cheers for the help...

---

### Post by -grubby on 2008-06-07
In the middle I'm pretty sure you'd just put a text input space, it should cover the whole area

---

### Post by davbren on 2008-06-08
Ok thats great! I've done that and now I can type in my program! woohoo! 

I now have the issue of not knowing how to communicate the C code to the glade layout. for instance, how do I get the "new document" button to actually create a new document?

Theres also more functionality I would like from the text box in the middle but I don't know where to put my procedure, or what identifier I should be using in my code.

---

### Post by slavik on 2008-06-08
you need to set up callbacks on buttons and then register them within the code.

---

### Post by MicahCarrick on 2008-06-09
Yes it sounds like you need to work through a very basic tutorial ([_GTK+ and Glade3 GUI Programming Tutorial_]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")).

In short, you are going to specify a "handler" (in the Signals tab) in Glade for the "activated" signal of the 'New' menu item. Then in C, you will use glade_xml_signal_connect or gtk_builder_connect_signals (depending on if you're using GtkBuilder or Libglade) to connect that handler to your callback function of the same name. 

So, if you specify 'on_new_menu_activate' as the handler name for the New menu's "activate" signal, you should have a C function that looks like:

```
void on_new_menu_activate (GtkMenuItem *menuitem, gpointer user_data)
{
    g_debug("Create new document here...");
}
```

I know this is what the function should look like because the GKT+ manual lists the prototype of callback functions for every signal.

---

### Post by Can+~ on 2008-06-09
You're using Glade2, which generates C code along the file, you can extract the .glade, but try to keep updated and use Glade3 (and check the tutorial of Micah). Glade3 only produces a .glade file, you can read it with python with gtk.glade library.

---

### Post by davbren on 2008-06-09
I'm using glade 3.4.5 the C code came from Anjuta.

---

