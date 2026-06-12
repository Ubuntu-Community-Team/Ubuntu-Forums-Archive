---
title: "[OpenGL] Which statement is correct?"
date: 2011-07-27
forum: Programming Talk
---

### Post by t1497f35 on 2011-07-27
Hi,
I'm learning GL, on screenshot the author seems to say glReadPixels reads data _from_ the PBO, but then he seems to say that glReadPixels reads data _to_ the PBO.

Any clue which statement is correct?

Looks like he's contradicting himself there and I can't figure out what's up.

---

### Post by slavik on 2011-07-28
it depends on how the PBO is attached, see here for more details: [http://www.songho.ca/opengl/gl_pbo.html](http://www.songho.ca/opengl/gl_pbo.html)

---

### Post by t1497f35 on 2011-07-28
Thanks,
My point is that the author says glReadPixels reads the data _from_ a PBO (first underlined words on screenshot).

Afaik, glReadPixels can only read data from the framebuffer (and write that data to the PBO or client). It cannot read _from_ a PBO. Am I wrong?

---

### Post by slavik on 2011-07-28
either one, from the page I linked to, direct quote:

> For example, glReadPixels() and glGetTexImage() are "pack" pixel operations, and glDrawPixels(), glTexImage2D() and glTexSubImage2D() are "unpack" operations. When a PBO is bound with GL_PIXEL_PACK_BUFFER_ARB token, glReadPixels() reads pixel data from a OpenGL framebuffer and write (pack) the data into the PBO. When a PBO is bound with GL_PIXEL_UNPACK_BUFFER_ARB token, glDrawPixels() reads (unpack) pixel data from the PBO and copy them to OpenGL framebuffer. 

basically, what it says is that it moves pixels between PBO and OpenGL framebuffer.

---

### Post by t1497f35 on 2011-07-28
Thanks,
but as I said and as your quote says glReadPixel() is not used to copy to the PBO (unlike what the quote from screenshot from 1st post says), instead, another function is used, like glDrawPixels() (with an appropriate target obviously), that's why I started the thread to find it out..

---

