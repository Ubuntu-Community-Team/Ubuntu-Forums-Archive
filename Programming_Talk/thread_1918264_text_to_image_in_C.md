---
title: "text to image in C"
date: 2012-01-31
forum: Programming Talk
---

### Post by conradin on 2012-01-31
I want to read a read a text file and dump the file to a bitmap image. Any thoughts on how I might do that?

---

### Post by Hetepeperfan on 2012-01-31
> **conradin said:**
> I want to read a read a text file and dump the file to a bitmap image. Any thoughts on how I might do that?


You could checkout the following link:

[http://cairographics.org/pycairo_pango/](http://cairographics.org/pycairo_pango/)

This is an example of writing a text to an image file .png in this case.
This comes from the cairo library which is used very much as the renderer for gui icons etc. Cairo specializes in vector graphics, and pango which is a different library that specializes more in textrendering in all kinds of languages like chinese. Both can do the job I think. Of course you probably have to write some glue code that takes care of lines etc. The example is in python however writing a similar program in C is also perfectly possible.

succes!

---

