---
title: "Default Ubuntu image (decoding) library?"
date: 2012-02-25
forum: Programming Talk
---

### Post by t1497f35 on 2012-02-25
Hi,
I need to read and decode different image files (jpg, png, gif etc) to raw bytes and to be able to query for basic properties like if there's an alpha channel in the image etc.

Does Ubuntu ship **by default** with such a library that I could use from C++ or C?

---

### Post by Bachstelze on 2012-02-25
libjpeg, libpng, libgif. :)

---

### Post by t1497f35 on 2012-02-25
Thanks, I mean a **unified** library, so that I don't end up with a hard-coded list of library name -> image type. This isn't a good design imo.

---

### Post by alegomaster on 2012-02-25
If you can't find an unified libary, you make an unified libary. 

[http://stackoverflow.com/questions/13128/how-to-combine-several-c-c-libraries-into-one](http://stackoverflow.com/questions/13128/how-to-combine-several-c-c-libraries-into-one)

---

### Post by Bachstelze on 2012-02-25
He will still have to "hardcode" (whatever he means by that) the names of the functions. I fail to see the problem in using several libraries, that's how vritually every image manipulation program does it (just use ldd on them to see it).

---

### Post by alegomaster on 2012-02-25
I am guessing that he would want an universal library which contains functions which work with any image format. He does not want to use a separate function for each image type.

---

### Post by t1497f35 on 2012-02-25
> **alegomaster said:**
> I am guessing that he would want an universal library which contains functions which work with any image format. He does not want to use a separate function for each image type.
Bingo! (well, not necessarily _any_ image type).

For example Gdk :: Pixbuf when feeded a path to an image file decodes it no matter what type it is, then I can query the pixbuf for a few properties, like how many bits per channel and if it's got alpha.

---

### Post by Some Penguin on 2012-02-27
ImageMagick may not be _default_ necessarily, but it's very common.

---

