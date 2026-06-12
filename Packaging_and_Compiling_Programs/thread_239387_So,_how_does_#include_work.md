---
title: "So, how does #include work?"
date: 2006-08-19
forum: Packaging and Compiling Programs
---

### Post by kripkenstein on 2006-08-19
I can't find a good reference for this, so I figured I'd ask.

I don't quite understand how #include <X.h> works in Ubuntu (or Linux in general, I guess). For example, I wanted to play around with the Poppler PDF library, so I installed the dev package. I see in the installed files (of libpoppler-glib-dev) that the .h are in /usr/include/poppler/glib. So in my .cpp file, I do "#include <poppler/glib/poppler.h>".

This starts to compile, and indeed it does find the poppler.h file in the right place, but then inside poppler.h there is "#include <glib-object.h>", which causes an error. I **do** have the dev files for glib, it's just that they are in /usr/include/glib-2.0 - and therefore I get an error, that glib-object.h can't be found.

I must be missing something basic here. How do I get this sort of thing to work? Manually inserting /glib-2.0 into poppler.h (which isn't a file of mine, even) seems wrong.

---

