---
title: "Trying to learn vala... need help"
date: 2009-06-20
forum: Programming Talk
---

### Post by | MM | on 2009-06-20
Hi,

I am trying to learn Vala having used python.

I was wondering if someone could help me with the following:

```
str_renderer.set_property ("ellipsize", Pango.EllipsizeMode.END);
```
produces the following compile error
```
error: Argument 2: Cannot convert from `Pango.EllipsizeMode' to `GLib.Value'
        str_renderer.set_property ("ellipsize", Pango.EllipsizeMode.END);
                                                ^^^^^^^^^^^^^^^^^^^^^^^

```

Also, i want to build a flat list of subdirs... i am using a gio enumerator and appending files to a ListStore.  I want to do something like the following:

```
while ((finfo = enumerator.next_file (null)) != null) {
                type = finfo.get_file_type ();
                if (type == FileType.DIRECTORY) {
                    // append dir to liststore
                }
}
```

But i dont know how to equality test the file type. 


Any help much appreciated!  :)

---

### Post by arkashkin on 2009-09-10
I am a beginner in Vala too, it is better to ask questions on Valas' mailing list:
[http://mail.gnome.org/mailman/listinfo/vala-list]("http://mail.gnome.org/mailman/listinfo/vala-list")

---

