---
title: "python &quot;fast&quot; filename"
date: 2009-11-25
forum: Programming Talk
---

### Post by giuspen on 2009-11-25
hi,
I need to serialize a binary content going through a function that writes a file name:
[PHP]pixbuf.save("image_temp.png", "png")
fd = open("image_temp.png", "rb")
image_string = base64.b64encode(fd.read())
fd.close()[/PHP]
Does anybody know if it is possible somehow to skip the writing to disk?
The function pixbuf.save(...) described [here]("http://www.pygtk.org/docs/pygtk/class-gdkpixbuf.html#method-gdkpixbuf--save") is the only one that allows me to obtain the binary data I need and takes a filename, but is there a kind of cached, fast way without going through the writing to disk or that's the only way?
thanks in advance.

---

### Post by Paul Miller on 2009-11-25
Sure.  Save the data to a cStringIO object rather than a file.

---

### Post by giuspen on 2009-11-25
> **Paul Miller said:**
> Sure.  Save the data to a cStringIO object rather than a file.

but the function 
[PHP]pixbuf.save("image_temp.png", "png")[/PHP]
requires a filename as first parameter, not a file object (like fd).
can you please modify my code introducing the StringIO as I don't understand how to implement it.
thanks a lot.

---

### Post by Can+~ on 2009-11-25
The following method on that documentation does what you want: gtk.gdk.Pixbuf.save_to_callback.

---

### Post by giuspen on 2009-11-26
> **Can+~ said:**
> The following method on that documentation does what you want: gtk.gdk.Pixbuf.save_to_callback.

I tried it but after encoding it to base64 I had only few letters out of a very big image... and I can't understand what's wrong :(

---

