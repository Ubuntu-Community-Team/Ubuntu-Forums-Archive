---
title: "change doxygen frontpage"
date: 2008-09-24
forum: Programming Talk
---

### Post by monkeyking on 2008-09-24
I'm trying to document my program,
and decided to go with doxygen.


This is quite nice,
but does anyone know, how to change the frontpage of the generated html file.


thanks

---

### Post by monkeyking on 2008-09-24
I found out, that I have to put a \mainpage somewhere in my sourcecode.

But I do still need some info on how to make non codedocumentation in doxygen.

---

### Post by dribeas on 2008-09-27
> **monkeyking said:**
> I found out, that I have to put a \mainpage somewhere in my sourcecode.

But I do still need some info on how to make non codedocumentation in doxygen.

I have no real experience with doxygen, just follow the rules a coworker gave me (so I don't know if there's any better solution). We add a doxygen.h (C++) file to each module with module wide doxygen comments.

---

