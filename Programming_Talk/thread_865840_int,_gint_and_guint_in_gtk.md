---
title: "int, gint and guint in gtk"
date: 2008-07-21
forum: Programming Talk
---

### Post by dexter.deepak on 2008-07-21
this is another nOOb question.
i couldnt get the point in understanding the difference between int, gint, and guint in gtk ...in what conditions should we use them and what are the advantages of using one over the other ?

---

### Post by scourge on 2008-07-21
[http://library.gnome.org/devel/glib/stable/glib-Basic-Types.html](http://library.gnome.org/devel/glib/stable/glib-Basic-Types.html)

int and gint should be the same thing, and guint is the same as unsigned int. I don't see any advantage to using one over the other. gint16, gint32, etc. can be useful though, if you need fixed-length integer types.

---

### Post by mike_g on 2008-07-21
I think **gint** is for consistencey, where as **guint32** is just shorthand for **unsigned long**. I cant see any other practical purpose for it.

---

### Post by scourge on 2008-07-21
> **mike_g said:**
> I think **gint** is for consistencey, where as **guint32** is just shorthand for **unsigned long**. I cant see any other practical purpose for it.

No, quint32 always has a size of 32 bits (4 bytes). unsigned long on the other hand isn't guaranteed to be 4 bytes. So these types can be very useful if one need a fixed-length integers (eg. for cross-platform binary file handling).

---

### Post by mike_g on 2008-07-21
Oh, I thought that long was 32bits whereas int was platform dependant. If thats wrong then how would you manually go about defining a 32bit unsigned integer?

---

### Post by scourge on 2008-07-21
> **mike_g said:**
> Oh, I thought that long was 32bits whereas int was platform dependant. If thats wrong then how would you manually go about defining a 32bit unsigned integer?

Long is usually 32 bits on 32-bit platforms, and 64 bits on 64-bit platforms. I wouldn't try to define my own 32-bit integer when I can use gint32 (GTK), qint32 (Qt), int32_t (C99), __int32 (MSC), etc.

---

### Post by bruce89 on 2008-07-21
Most of the g* types are just typedefs to the normal ones. They are just for consistancy with *gboolean* and *gpointer*.

These are actually defined in GLib, not GTK+.

---

