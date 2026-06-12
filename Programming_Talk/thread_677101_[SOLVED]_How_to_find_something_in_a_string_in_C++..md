---
title: "[SOLVED] How to find something in a string in C++."
date: 2008-01-24
forum: Programming Talk
---

### Post by Acglaphotis on 2008-01-24
Im used to doing this on python
 [PHP]
if 'something' in variable:
    somestuff
[/PHP]

But i can't seem to find a C++ counterpart to python's "in". Any ideas?

---

### Post by LaRoza on 2008-01-24
> **Acglaphotis said:**
> Im used to doing this on python
 [PHP]
if 'something' in variable:
    somestuff
[/PHP]

But i can't seem to find a C++ counterpart to python's "in". Any ideas

What data structure are you using?

---

### Post by Acglaphotis on 2008-01-24
Just a normal string (like char[x]), and i want to find a specific word in it.

---

### Post by LaRoza on 2008-01-24
[http://www.cppreference.com/cppstring/index.html](http://www.cppreference.com/cppstring/index.html)

Use the string class, not char[]. You can look into regular expressions if you need more functionality.

---

### Post by Acglaphotis on 2008-01-24
Thanks, i found a buch of useful references in there!

---

### Post by LaRoza on 2008-01-24
> **Acglaphotis said:**
> Thanks, i found a buch of useful references in there!

Yes, it is packed with good information.

---

