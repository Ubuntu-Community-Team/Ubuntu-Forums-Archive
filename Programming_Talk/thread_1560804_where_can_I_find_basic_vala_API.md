---
title: "where can I find basic vala API"
date: 2010-08-25
forum: Programming Talk
---

### Post by tbastian on 2010-08-25
I read the vala tutorial and I'm very impressed with the language. I've done some Java programming and got tired of how slow it is because it's interpreted, but I LOVE the syntax and built in features. Vala syntax is amazing, it has everything I've ever wanted in a language, but there seems to be very little documentation. valadoc.org gives just function names, not descriptions, and I can't find built-in function documentation (eg is there a case insensitive compare for strings?!)

---

### Post by kahumba on 2010-08-25
There we go (to the left one can see a multitude of documented "packages"):
[http://valadoc.org/](http://valadoc.org/)
Particularly your string related question is in the "package" glib-2.0, the class "string":
[http://valadoc.org/glib-2.0/string.html](http://valadoc.org/glib-2.0/string.html)

I'd like it to be available for download but unfortunately there seems to be no such option, browsing online for many folks (like me) takes a lot longer than browsing from HDD because of internet connection quality.

---

### Post by tbastian on 2010-08-25
aha! thanks a lot!

---

### Post by splicerr on 2010-08-25
> **kahumba said:**
> There we go (to the left one can see a multitude of documented "packages"):
[http://valadoc.org/](http://valadoc.org/)
Particularly your string related question is in the "package" glib-2.0, the class "string":
[http://valadoc.org/glib-2.0/string.html](http://valadoc.org/glib-2.0/string.html)

I'd like it to be available for download but unfortunately there seems to be no such option, browsing online for many folks (like me) takes a lot longer than browsing from HDD because of internet connection quality.

You can generate docs from the vapi files yourself with valadoc. But you'll basically just get the classes and its properties and methods in html or devhelp2 form. No descriptions as on the website.

---

### Post by ierosvin on 2010-09-23
vala API is also available in /usr/share/vala/api. :)

---

