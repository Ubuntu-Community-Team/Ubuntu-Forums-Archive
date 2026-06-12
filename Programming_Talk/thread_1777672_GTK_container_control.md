---
title: "GTK container control"
date: 2011-06-08
forum: Programming Talk
---

### Post by Altainia on 2011-06-08
I'm having a problem with GTK. I want to create a label that auto-wraps its text and its text can change. But I do not want the label to grow HORIZONTALLY IN THE SLIGHTEST. I would rather it grow VERTICALLY ONLY and shrink back as necessary. The label reaches its own horizontal limit but I do not like it nor have the means to change it to my design.

---

### Post by JupiterV2 on 2011-06-08
This can be controlled by how you pack your widget. Pack it into a vertical box with EXPAND|FILL turned on. You'll need to check the GTK+ documentation but I think labels automatically wrap when the widget expands. I could be wrong though, in which case you may need to explicitly turn on the feature. Look for something like 'gtk_label_set_text_wrap(GtkWidget*, gboolean);' or similar.

---

### Post by Altainia on 2011-06-08
Nope, still growing horizontally.

---

### Post by Petrolea on 2011-06-08
> **Altainia said:**
> Nope, still growing horizontally.

I'm pretty sure that you can set something with one of these functions: [http://developer.gnome.org/gtk/2.24/GtkLabel.html](http://developer.gnome.org/gtk/2.24/GtkLabel.html)

This maybe: gtk_label_set_line_wrap(). There are many functions that handle the look, try them out.

---

### Post by JupiterV2 on 2011-06-08
The other way you can do it is by requesting a specific size for your widget. gtk_widget_set_size_request() will clamp the widget to a specific size. I don't personally like doing this because it prevents the normal behaviour of a window from re-sizing your widget when its parent widget is re-sized.

---

### Post by Altainia on 2011-06-09
I ended up forcing sizes per set_size_request. Then I ran into a spot of trouble with the labels that were supposed to wrap not recognizing their new constraints, so I had to enforce the same set_size_request for each of them. Luckily there weren't that many. Anyway, this feels a little hackish and I wish GTK supported setting max widths or heights, but it's working now.

---

### Post by tbastian on 2011-06-09
I believe that if you call set_size_request and enter a width for the width, but -1 for the height it will always grow vertically. I would have to check some code I wrote recently though, I wasn't actually looking specifically for that behaviour.

---

