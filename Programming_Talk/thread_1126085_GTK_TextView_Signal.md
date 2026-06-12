---
title: "GTK TextView Signal"
date: 2009-04-15
forum: Programming Talk
---

### Post by sekinto on 2009-04-15
I was wondering if there was a TextView signal that triggers an event every time the TextView buffer is changed (example: user deletes or inserts text).

I only see signals that are really specific like "backspace", "insert-at-cursor". "delete-from-cursor", "paste-clipboard", "button-press-event", etc.

If there really is no on-buffer-change type event I might just have to use a combination of "key-press-event", "cut-clipboard" and "paste-clipboard" (those are the only ways to edit text in a TextView box, right?).

---

### Post by cabalas on 2009-04-15
The TextView does not have a signal for this, but the text buffer which you get through

```

GtkTextBuffer *gtk_text_view_get_buffer(GtkTextView *text_view);

```

does have thew signal "changed" which is fired when the contents of the text buffer changes

Appropriate links to documentation:

[LIST]
[*][http://library.gnome.org/devel/gtk/stable/GtkTextBuffer.html#GtkTextBuffer-changed](http://library.gnome.org/devel/gtk/stable/GtkTextBuffer.html#GtkTextBuffer-changed)
[*] [http://library.gnome.org/devel/gtk/stable/GtkTextBuffer.html](http://library.gnome.org/devel/gtk/stable/GtkTextBuffer.html)
[*] [http://library.gnome.org/devel/gtk/stable/TextWidgetObjects.html](http://library.gnome.org/devel/gtk/stable/TextWidgetObjects.html)
[/LIST]

---

### Post by sekinto on 2009-04-15
I'm pretty clueless when it comes to GTK. I'm using Python (and Glade to build the interface), in Glade I can set a handler for a certain event like "on_clear_clicked" and then in the Python code inside my application class I can define what it does like
```
def on_clear_clicked(---some args---):
    ---some code---
```
How would I give this buffer event a handler so I can define what it does?

Thanks for the help by the way.

---

### Post by cabalas on 2009-04-15
> **sekinto said:**
> I'm pretty clueless when it comes to GTK. I'm using Python (and Glade to build the interface), in Glade I can set a handler for a certain event like "on_clear_clicked" and then in the Python code inside my application class I can define what it does like
```
def on_clear_clicked(---some args---):
    ---some code---
```
How would I give this buffer event a handler so I can define what it does?


Unfortunately you can't connect to the Text buffer signals via glade, what you will need to do is after you load the glade file grab the text view extract the text buffer and connect the signal manually, the code should look something similar to this

[PHP]
ui_file = new Gtk.Builder()
ui_file.add_from_file(file_name)
ui_file.connect_signals(some_object, None)

my_text_view = ui_file.get_object("my_text_view")
buffer = my_text_view.get_buffer()

buffer.connect("clicked", some_function, None)
[/PHP]

and then elsewhere declare the function as you normally would.  I have to ask you to excuse my code I'm a little rusty in python and haven't done much Gtk programming with it.

> **sekinto said:**
> Thanks for the help by the way.

No worries.

---

### Post by sekinto on 2009-04-15
You are the most awesome person ever!
I'd give you cookies or something if I knew you. :p

---

