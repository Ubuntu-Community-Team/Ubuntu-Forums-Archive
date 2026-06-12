---
title: "building firefox 3.0 with antialiasing (ubuntu 7.10)"
date: 2008-07-01
forum: Packaging and Compiling Programs
---

### Post by chochem on 2008-07-01
I'm trying to make a build of firefox 3.0 with antialiasing. Here's my mozconfig:

```
mk_add_options MOZ_CO_PROJECT=browser
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/objdir
mk_add_options MOZ_MAKE_FLAGS=-j4
ac_add_options --enable-application=browser
ac_add_options --enable-default-toolkit=cairo-gtk2
ac_add_options --enable-xft
ac_add_options --disable-crashreporter
ac_add_options --disable-tests
ac_add_options --disable-mochitest
ac_add_options --enable-optimize=-O2

```
(I'm sorry to say that I don't actually know what the MAKE_FLAGS line is for - it seems to have been part of the template i copied)

The build completes successfully but either I'm misjudging what XFT is or there isn't any. Compared to any other browser, text looks blocky and thin. There are some anti-aliasing effects but nowhere near as smooth as that in other browsers.  Am I doing something wrong? At first, I had set "ac_add_options --enable-default-toolkit=gtk2" but was told that in order to use the xft option I had to change it to ac_add_options "--enable-default-toolkit=cairo-gtk2".

Can anybody tell me what the standard firefox builds are compiled with IF not XFT/CAIRO_GTK2? Or if I need some other package to make it look decent?

---

