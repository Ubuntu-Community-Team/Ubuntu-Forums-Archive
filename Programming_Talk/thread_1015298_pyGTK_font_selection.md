---
title: "pyGTK font selection"
date: 2008-12-18
forum: Programming Talk
---

### Post by af20001 on 2008-12-18
Hi,

In pyGTK, does anyone know if there is a way to get just the font size, name or style on their own from the font selection? The get_font_name() method returns something like:

TlwgMono Bold 12
gargi 14
Nimbus Roman No9 L Italic 12

What if you want to get style or name parts on their own?

---

### Post by bruce89 on 2008-12-18
I'm afraid the Python bindings don't have get_family () or get_size () yet, as they were only added to GTK+ a few months ago (2.14).

---

