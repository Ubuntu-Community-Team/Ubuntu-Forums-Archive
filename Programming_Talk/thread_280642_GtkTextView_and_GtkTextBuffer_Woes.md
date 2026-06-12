---
title: "GtkTextView and GtkTextBuffer Woes"
date: 2006-10-19
forum: Programming Talk
---

### Post by dean703 on 2006-10-19
I'm having trouble inserting text into a GtkTextBuffer taken from a GtkEntry (as in a chat program). I can get gtk_text_buffer_set_text() to work fine, but that overwrites what is already there. How do I get gtk_text_buffer_insert and GtkTextIter to work, and or insert text and retain what is already there? Help, I'm going round in circles.

---

### Post by Keith Hedger on 2007-01-16
download the docs from:
[http://www.gtk.org/api](http://www.gtk.org/api)

you need to get a start and end textiter and do:

gtk_text_buffer_insert          (GtkTextBuffer *buffer,
                                             GtkTextIter *iter,
                                             const gchar *text,
                                             gint len);

---

