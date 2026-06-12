---
title: "[C++] Question about 'const'"
date: 2008-09-18
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-09-18
As far as I understand the 'const' keyword makes a variable hold its value permanently without (you)being able to modify it. My question is, why some functions(gstreamer) return a type of 'const gchar*'? Does it have the same meaning? If so, why would I need my 'value' to be unmodifiable? And also why an implicit typecast to 'gchar *' doesn't work?

---

### Post by Npl on 2008-09-18
> **SledgeHammer_999 said:**
> As far as I understand the 'const' keyword makes a variable hold its value permanently without (you)being able to modify it. My question is, why some functions(gstreamer) return a type of 'const gchar*'? Does it have the same meaning? If so, why would I need my 'value' to be unmodifiable? And also why an implicit typecast to 'gchar *' doesn't work?

Theres a significant difference between 'const gchar*' and 'gchar *const'. First means you have a pointer to a constant value, later means you have constant pointer to a value - you can remember this by simply reading the expression from right to left.

and you cant cast const * to nonconst* as it would ridicule the meaning, the value its pointing to must not be modified. You can however do 'gchar myval = *const_pointer_to_val'

---

### Post by dwhitney67 on 2008-09-18
Here's a [link ]("http://www.parashift.com/c++-faq-lite/const-correctness.html#faq-18.5")concerning the declaration of pointers and references that was posted by Dribeas in another thread.  I think you will find your answer there.

P.S.  You can strip away the const of a pointer using const_cast<>... but you should ask yourself why you need to do this before actually doing it!
[PHP]const gchar * function();

// ...

gchar *g = const_cast<gchar*>( function() );[/PHP]

---

### Post by dribeas on 2008-09-18
> **dwhitney67 said:**
> P.S.  You can strip away the const of a pointer using const_cast<>... but you should ask yourself why you need to do this before actually doing it!
[PHP]const gchar * function();
// ...
gchar *g = const_cast<gchar*>( function() );[/PHP]

Even more, in some cases the compiler and OS may place constants in read-only memory (pages of memory marked as not-writable, or even real ROMs for embedded systems). While you can force the compiler into allowing you to change the constants, the OS and/or hardware might think otherwise and either fail or kill your application.

---

### Post by SledgeHammer_999 on 2008-09-18
oh yeah I totally forgot about the pointer(*) issue. thanks Npl I understand it now. All I wanted was to store the "name" of all elements I found in a big list and use them afterwards... so I forgot that the values were 'pointed'... Thank you guys.

---

### Post by kknd on 2008-09-18
In gstreamer and other glib-bases libraries, that also means that you don't need to do a g_free on the string (all non-const gchar* must be freed with g_free)

---

### Post by SledgeHammer_999 on 2008-09-18
ok thanks!!

---

