---
title: "C Variable Types/ &quot;#define&quot;"
date: 2009-07-24
forum: Programming Talk
---

### Post by matmatmat on 2009-07-24
Is there a way to get the type of a variable?
Is there a way to use if's with defines

---

### Post by jespdj on 2009-07-24
No, C does not have a standard runtime type information mechanism.

What do you mean with your second question? There's #ifdef, see [Conditional Syntax](http://gcc.gnu.org/onlinedocs/cpp/Conditional-Syntax.html#Conditional-Syntax) in the GCC manual.

---

### Post by matmatmat on 2009-07-24
Does that mean there is also no way to get the length of a variable?

---

### Post by MadCow108 on 2009-07-24
you can get the length of a varable type in bytes with sizeof(type)

but use with care when using it with arrays.
you'll mostly get the size of the pointer not the size of the array.

---

