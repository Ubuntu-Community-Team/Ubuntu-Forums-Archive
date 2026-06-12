---
title: "save a pixbuf as a string"
date: 2010-04-18
forum: Programming Talk
---

### Post by giuspen on 2010-04-18
Hi,
actually to serialize and deserialize a pixbuf image I found this only way:

[PHP]def get_png_encoded_string_from_pixbuf(pixbuf):
   """Pixbuf To PNG Encoded String"""
   pixbuf.save(IMG_PATH, "png")
   fd = open(IMG_PATH, "rb")
   png_encoded_string = base64.b64encode(fd.read())
   fd.close()
   return png_encoded_string

def get_pixbuf_from_png_encoded_string(png_encoded_string):
   """PNG Encoded String To Pixbuf"""
   fd = open(IMG_PATH, "wb")
   fd.write(base64.b64decode(png_encoded_string))
   fd.close()
   pixbuf = gtk.gdk.pixbuf_new_from_file(IMG_PATH)
   return pixbuf[/PHP]

but this is slow as I always have to write each image to disk before saving it as a string/before obtaining the pixbuf again from the encoded string, then is probably reducing the disk life cause of multiple write times.
Is there another way to obtain the same result that would avoid going through the writing to disk?
Thanks in advance.

---

### Post by Bachstelze on 2010-04-18
You can probably do that using a file-like object (e.g. a StringIO):

[http://docs.python.org/library/stringio.html](http://docs.python.org/library/stringio.html)

---

### Post by soltanis on 2010-04-18
Let me get this straight, you want to turn a binary pixbuf to base64, right?

Also, reading and writing to a disk a lot doesn't necessarily reduce its life (unless it's flash media) -- I would be more worried about the performance penalty you incur, since disks are generally slow.

Have you tried maybe using shared memory?

---

### Post by giuspen on 2010-04-18
> **Bachstelze said:**
> You can probably do that using a file-like object (e.g. a StringIO):

[http://docs.python.org/library/stringio.html](http://docs.python.org/library/stringio.html)

It seems to me that I can't use this workaround as the functions that I need require a file path and not a file descriptor

---

### Post by giuspen on 2010-04-18
> **soltanis said:**
> Let me get this straight, you want to turn a binary pixbuf to base64, right?

Also, reading and writing to a disk a lot doesn't necessarily reduce its life (unless it's flash media) -- I would be more worried about the performance penalty you incur, since disks are generally slow.

Have you tried maybe using shared memory?

Yes I want to save a pixbuf to a string (and vice versa), the only way I found was to go through the conversion to binary PNG and subsequent serialization through base64 (and viceversa load again to pixbuf from PNG).

Can you write me something more about shared memory, I don't have any knowledge in this.

Thank you.

---

### Post by Mathew Roy on 2010-04-19
Hi giuspen. U seem to know how to handle PNG files in C programming. That is exactly what i want to know. Though u could help me .
Plz visit this thread [http://ubuntuforums.org/showthread.php?p=9147036](http://ubuntuforums.org/showthread.php?p=9147036)
Thanks in advance.

---

