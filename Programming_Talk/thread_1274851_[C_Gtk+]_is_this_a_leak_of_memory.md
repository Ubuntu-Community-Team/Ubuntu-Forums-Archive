---
title: "[C Gtk+] is this a leak of memory?"
date: 2009-09-25
forum: Programming Talk
---

### Post by froggyswamp on 2009-09-25
Folks, it's a snippet of Gtk using C:
```

//gpointer "data" is a GtkWindow
static void titleChanged(GObject *obj, GParamSpec *property, gpointer data) {
	gchar *value;
	g_object_get(data, "title", &value, NULL);
	g_message("new title is %s", value);
//without next line do I produce a memory leak? 
	g_free(value);
}

```
I'm learning C and trying to avoid memory leaks from the beginning. Any ideas?

---

### Post by PmDematagoda on 2009-09-25
The GTK+ reference manual has this to say:-

> Gets properties of an object.

In general, a copy is made of the property contents and the caller is responsible for freeing the memory in the appropriate manner for the type, for instance by calling g_free() or g_object_unref().
So yes, you do need that line in order to prevent a memory leak.

---

### Post by froggyswamp on 2009-09-25
Thanks!! I thought that since it's inside a function the function might take care of that, apparently it's not the case since uh.. I'm not sure why, perhaps cause the pointer is "filled" with contents from another place.

---

### Post by MadCow108 on 2009-09-25
in C the function cannot take care of that because C has no kind of garbage collection or RAII
so you always have to free results where you gave a pointer and receive something bigger than a pointer. (which is from my limited experience with gtk nearly always the case)

you should always use valgrind to check if there are any memory leaks.

I recommend using c++ and gtkmm (or any other higher language with gtk bindings) for gtk gui development.
It makes live a lot easier, especially memory management.

---

### Post by froggyswamp on 2009-09-25
Thanks, I actually started learning C++/gtkmm in the past (I'm a Java dev) but I found the gtkmm tutorial too basic and when googling for stuff I always landed either to a C or Python reference which made me in the end go straight to C.
There's no Gtk tutorial such as "The Java tutorial" which is several hundred pages which also covers advanced stuff with lots of screenshots and full working examples. I even suggested it on brainstorm but the idea is still "awaiting moderation", oh well..

---

