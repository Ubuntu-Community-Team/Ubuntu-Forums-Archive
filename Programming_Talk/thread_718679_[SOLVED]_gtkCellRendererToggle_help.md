---
title: "[SOLVED] gtkCellRendererToggle help"
date: 2008-03-08
forum: Programming Talk
---

### Post by derrick81787 on 2008-03-08
Hello everyone,

Can someone please tell me how to check/uncheck the togglebutton in a gtkCellRendererToggle?  It seems that I can either set all the values in a column as active/inactive, or I can't do any.  I'm programming in C, and there seems to be surprisingly little documentation about how to do this, and the examples I have found don't work.  Here is my current callback function that runs but doesn't work, just in case it helps:

```
void buttonToggled(GtkCellRendererToggle* renderer, gchar* pathStr, gpointer data)
{
   GtkTreeIter iter;
   gboolean enabled;
   GtkTreePath* path = gtk_tree_path_new_from_string(pathStr);
   gtk_tree_model_get_iter(GTK_TREE_MODEL (data), &iter, path);
   gtk_tree_model_get(GTK_TREE_MODEL (data), &iter, 0, &enabled, -1);
   enabled = !enabled;
   gtk_tree_store_set(GTK_TREE_STORE (data), &iter, 0, &enabled, -1);
}
```

Also, I'm passing a pointer to the GtkTreeModel as the user data.

Thanks in advance for the help.

Derrick

---

### Post by Can+~ on 2008-03-08
It's pretty dumb actually. You should connect the cell renderer event "toggled" to a function that inverts the value.

I don't know about C++/C, I use python and it's something like:

self.trees = the tree store
self.cell = the cell toggle renderer
[PHP]
#Connection
#object("event", function, user_data)
self.cell.connect("toggled", self.event_togg, self.trees)

#Event toggle:
#self is the reference to the class which is in, it's not needed in your case
#cell and path are given by the same cell on the event toggled.
#model is the tree store model which I added above
def event_togg(self, cell, path, model):
	model[path][0] = not model[path][0]
[/PHP]

---

### Post by derrick81787 on 2008-03-08
> **Can+~ said:**
> It's pretty dumb actually. You should connect the cell renderer event "toggled" to a function that inverts the value.

I don't know about C++/C, I use python and it's something like:

self.trees = the tree store
self.cell = the cell toggle renderer
[PHP]
#Connection
self.cell.connect("toggled", self.event_togg, self.trees)

#Event toggle:
def event_togg(self, cell, path, model):
	model[path][0] = not model[path][0]
[/PHP]

I do.  The function that I posted is ran when cell renderer receives the toggle event.  The part that I don't know how to do is the model[path][0] = not model[path][0].  I tried to invert the value in that function, but something must be wrong because it doesn't seem to update when I invert it.

---

### Post by Can+~ on 2008-03-08
Oh yeah, I forgot about that:

[PHP]self.column.add_attribute(self.cellrenderer, "active", 0)[/PHP]

You must add the attribute "active" for self updating on value change. And maybe setting an attribute to the cell renderer of "activatable" but I'm not sure if that's necessary, since I have a working code without that.

---

### Post by derrick81787 on 2008-03-08
> **Can+~ said:**
> Oh yeah, I forgot about that:

You must add the attribute "active" for self updating on value change. And maybe setting an attribute to the cell renderer of "activatable" but I'm not sure if that's necessary, since I have a working code without that.


For me, setting the renderer as active causes every toggle button in that column to become checked, and setting it to be inactive causes them all to be unchecked.  This is almost what I want, but I want it to only be for the one button that is actually clicked.  I have the renderer set as activatable, but I think that just allows it to recieve the "activate" event when clicked, which causes the callback function to be ran, but the problem is within the callback function.  I don't know if I'm not updating the value correctly or what.  It's possible because I only have a little experience with GTK and practically none with GtkTreeViews.

---

### Post by Can+~ on 2008-03-08
The thing is that tree model stores data in an array form:

treemodel[m][n] you can access the element at the row m, column n.

I think your problem of everything toggling on/off is the use of iterators. You should be able to switch the element of the treemodel just by

treemodel[path][column] = not treemodel[path][column]

Try making some hard examples, like, on your main code, making the treemodel[2][0] (or any other) true or false and see if it works.

---

### Post by derrick81787 on 2008-03-08
> **Can+~ said:**
> The thing is that tree model stores data in an array form:

treemodel[m][n] you can access the element at the row m, column n.

I think your problem of everything toggling on/off is the use of iterators. You should be able to switch the element of the treemodel just by

treemodel[path][column] = not treemodel[path][column]

Try making some hard examples, like, on your main code, making the treemodel[2][0] (or any other) true or false and see if it works.

Well, in C it's different.  It's actually way more complicated than I think it should be.  I'll work with it, though, and see what I can get.

---

### Post by derrick81787 on 2008-03-08
Well, I finally solved the problem with help from an email I found from the [email]gtk-app-devel-list@gnome.org[/email].  The message can be found here. [http://www.mail-archive.com/gtk-app-devel-list@gnome.org/msg09642.html](http://www.mail-archive.com/gtk-app-devel-list@gnome.org/msg09642.html)
Basically, I had to set the GtkTreeViewColumn as active, not the cell renderer.  Once I did that, my callback function worked with the exception of the last line which should be
```
gtk_tree_store_set(GTK_TREE_STORE (data), &iter, 0, enabled, -1);
```
The gboolean should be passed by value, not as a pointer.  If you use the function as I have it above (in my first post), it will always cause the box to be checked because the address of "enabled" is always non-zero.

Anyway, thanks for the help, and I'm marking this thread as solved.

---

### Post by derrick81787 on 2008-03-08
> **Can+~ said:**
> Oh yeah, I forgot about that:

[PHP]self.column.add_attribute(self.cellrenderer, "active", 0)[/PHP]

You must add the attribute "active" for self updating on value change. And maybe setting an attribute to the cell renderer of "activatable" but I'm not sure if that's necessary, since I have a working code without that.

Actually, it looks like you had it right.  I misread that as setting the GtkCellRendererToggle as active, and doing that is what caused all the cells to be checked.  It was a little odd because I didn't actually create a column object.  I just used the gtk_tree_view_insert_column_with_attributes() function which basically creates the column and inserts it all in one step, without the need to create stand alone column objects. All I had to do was make one of those attributes be the "active" attribute, and everything worked out though.

---

### Post by Can+~ on 2008-03-09
> **derrick81787 said:**
> Actually, it looks like you had it right.  I misread that as setting the GtkCellRendererToggle as active, and doing that is what caused all the cells to be checked.  It was a little odd because I didn't actually create a column object.  I just used the gtk_tree_view_insert_column_with_attributes() function which basically creates the column and inserts it all in one step, without the need to create stand alone column objects. All I had to do was make one of those attributes be the "active" attribute, and everything worked out though.

Great that it worked for you. You should paste the code for future C/C++GTK+ programmers.

---

### Post by derrick81787 on 2008-03-09
Here's where I insert the column.  Notice that the "active" property is set.  That's the part that I was missing:

```
   renderer = gtk_cell_renderer_toggle_new();
   gtk_tree_view_insert_column_with_attributes(
            GTK_TREE_VIEW (view), -1, "Selected", renderer,
            "active", NULL);
   g_object_set(renderer, "activatable", TRUE, NULL);
   g_signal_connect(renderer, "toggled", (GCallback) buttonToggled, model);
```

Here's the revised version of the callback.  The only difference between this and my first post is the last line.

```
void buttonToggled(GtkCellRendererToggle* renderer, gchar* pathStr, gpointer data)
{
   GtkTreeIter iter;
   gboolean enabled;
   GtkTreePath* path = gtk_tree_path_new_from_string(pathStr);
   gtk_tree_model_get_iter(GTK_TREE_MODEL (data), &iter, path);
   gtk_tree_model_get(GTK_TREE_MODEL (data), &iter, 0, &enabled, -1);
   enabled = !enabled;
   gtk_tree_store_set(GTK_TREE_STORE (data), &iter, 0, enabled, -1);
}
```

I've also attached my main.c and callbacks.c files so you can see how I set everything up.  The interface was made using glade, but the GtkTreeModel had to be created and set to the GtkTreeView by hand because it's not really supported in Glade.  The files are renamed to .txt just so I can attatch them because .c is not allowed.

I hope this helps, and let me know if there's anything else anyone needs.

Derrick

---

### Post by Can+~ on 2008-03-09
Here's in python, with an editable column and toggle button

[PHP]self.treecolv.add_attribute(self.cellrv, "text", 0)
self.treecolb.add_attribute(self.cellrb, "active", 1)

#Set properties
self.cellrv.set_property("editable", True)
self.cellrb.set_property("activatable", True)[/PHP]

Events
[PHP]self.cellrb.connect("toggled", self.event_toggle, self.trees)
self.cellrv.connect("edited", self.event_edit, self.trees)[/PHP]

And Functions called
[PHP]def event_toggle(self, cell, path, model):
	"""Inverts the boolean value on the tree store, thus making it
	toggeable."""
	model[path][1] = not model[path][1]
	
def event_edit(self, cell, path, new_text, model):
	"""Inserts the new text on the edited column"""
	model[path][0] = new_text
[/PHP]

Attached the treeview.py and the glade file.

---

