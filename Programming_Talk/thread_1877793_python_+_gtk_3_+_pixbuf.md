---
title: "python + gtk 3 + pixbuf"
date: 2011-11-08
forum: Programming Talk
---

### Post by cdar07 on 2011-11-08
Hi!

I have GdkPixbuf's and I want to convert them to string and backwards.
Is there a simple way to accomplish this?

Python GdkPixbuf object only have these methods:
'save_to_bufferv', 'save_to_callbackv', 'save_to_stream_finish', 'savev',
but i don't know how to use them.

Documentation: [http://developer.gnome.org/gdk-pixbuf/unstable//gdk-pixbuf-File-saving.html#gdk-pixbuf-save]("http://developer.gnome.org/gdk-pixbuf/unstable//gdk-pixbuf-File-saving.html#gdk-pixbuf-save")

---

### Post by crdlb on 2011-11-09
This seems like an area that has been neglected so far. In C (or Vala), you have save, save_to_stream, save_to_buffer, and save_to_callback. Each of those use varargs, so they should all have 'v' variants to replace them in language bindings. Of those, only savev seems to work in python: ```
pixbuf.savev("foo.png", "png", [], [])
``` save_to_streamv is missing entirely, save_to_bufferv appears to be unusable, and it looks like save_to_callback's data is being truncated on NUL.

To go the other way, you can use a GdkPixbuf.PixbufLoader, or load the image data into a Gio.MemoryInputStream and use GdkPixbuf.Pixbuf.new_from_stream.

(All of that is assuming you want an image format like png or jpeg. If you want the raw pixel data, I'm not sure.)

---

### Post by cdar07 on 2011-11-09
Thanks!

Yes, Loader works, but saving is still a problem.

I want to just store pixbufs at the end of a program to a xml file, and load them at startup. Raw/jpg - I don't care.

---

