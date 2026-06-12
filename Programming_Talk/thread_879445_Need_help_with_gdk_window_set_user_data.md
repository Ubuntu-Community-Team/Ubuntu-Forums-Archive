---
title: "Need help with gdk_window_set_user_data"
date: 2008-08-04
forum: Programming Talk
---

### Post by dosh on 2008-08-04
I'm trying to be able to place a pointer to some data to be associated with a window. For example say I have a number of windows open and when the focus is on one window I want to be able to get the data that is associated with that. I was thinking about using gdk_window_set_user_data and gdk_window_get_user_data though I notice it has been depreciated. Can anybody help me out with an example of how I might go about it. Lets say a point to an integer. And window A has the number 5 linked to it and window B has the number 8 linked to it. Can any help me Thanks. I can't seem to get it to work.

---

### Post by nvteighen on 2008-08-04
It seems gdk_window_set_user_data is replaced by a Glib routine. Look for g_object_set_data, which works like a dictionary.

(Ah, today I discovered GNOME's devhelp. It's a nice HTML documentation browser: install package devhelp and then libgtk-2.0-doc, libglib-2.0-doc)

---

### Post by dosh on 2008-08-04
Thanks nvteighen 
I was looking at that g_object_set_data(GObject *object, const gchar *key, gpointer data); 

I notice though if I make the object the window, and data the data ( :) ) whats the key for? Is that just a reference variable.
I'm a little confused on that one.

---

### Post by nvteighen on 2008-08-05
I think the idea is this:
The first argument is obviously the object.
That object has an attribute, which is the data.
The key is a way to access the data.

So, then you do g_object_get_data(g_object *object, const char *key) to retrive the data (it returns a gpointer).

In other words, is a hidden dictionary data type, like Python's:
```

a = {"greeting" : "Hello", "year" : 2008}

```

a["greeting"] will return "Hello" and a["year"], 2008. So, "greeting" and "year" are the keys, "Hello" and 2008 the data.

I suggest you to install packages devhelp, libgtk-2.0-doc and also libglib-2.0-doc to access the API in an easy way and offline.

---

