---
title: "Working with compressed files as you would with dirs in C?"
date: 2008-09-12
forum: Programming Talk
---

### Post by Amon_Re on 2008-09-12
Hi guys,

I'm currently (ab)using google trying to hunt down an existing lib with C bindings that allows me to create a compressed file, and create new files directly within that compressed file.

Sofar i've had little luck finding anything usefull (my google-fu isn't as strong as i hoped) so i was wondering if anyone inhere knew of one with a licence that's compatible with LGPL.

---

### Post by Darkhack on 2008-09-12
[http://www.nih.at/libzip/](http://www.nih.at/libzip/)

---

### Post by Amon_Re on 2008-09-12
> **Darkhack said:**
> [http://www.nih.at/libzip/](http://www.nih.at/libzip/)

I already saw that one, and it allows you to read files directly from inside a zip file, but it doesn't allow you to write to a file in a zipfile directly (yet?).

I'll probably use that one tho, and create files in /tmp prior to moving them to the zipfile

---

