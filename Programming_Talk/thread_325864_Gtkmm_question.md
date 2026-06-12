---
title: "Gtkmm question"
date: 2006-12-26
forum: Programming Talk
---

### Post by Absurd on 2006-12-26
For some reason, I am not able to use normal C datatypes in Gtkmm. For example, char* has to be ustring and short has to be guint16. Which header must I include to in order to use ustring, guint16, and the like?

---

### Post by maddog39 on 2006-12-26
You cant I dont believe. The C datatypes are only for regular GTK, GTKMM uses different ones and the C ones are not compatible with C++.

---

### Post by Absurd on 2006-12-26
You sure about that? I've always been able to use int, unsigned int, unsigned char, etc in C++. I'm talking about the API specific datatypes of gtkmm.

Should I just include glib.h?

---

### Post by maddog39 on 2006-12-26
Well not the standard data types, but the custom ones created by the GTK library. like gint for C and stuff. Those dont work in C++ as far as I know. Try glib.h I suppose. Never tried using glib.h but worth a try.

---

### Post by Absurd on 2006-12-29
I included "glibmm.h" instead and everything worked fine.

However, I have one more question.

How do I assign a formatted string to a glib::ustring object? I've tried assigning a formatted string of formatted gchars to a glib::ustring, but that doesn't seem to work.

---

