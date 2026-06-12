---
title: "Math functions missing?"
date: 2005-05-30
forum: Packaging and Compiling Programs
---

### Post by alive on 2005-05-30
Hello, 

I wasn't able to compile a small program because of an undefined reference to pow(). I tested and it doesn't seem any of the functions in math.h (sin(), etc) are available to my program. Since these are part of the C standard library I'm quite surprised.

What do I have to do to get math functions working? I tried using -lmath, but that didn't work.

Thanks

---

### Post by Juergen on 2005-05-30
Try '-lm', the library is named 'libm'

---

### Post by alive on 2005-05-30
Ah, thank you. I've been developing with gcc on Windoze (MinGW) for awhile, so I wasn't used to having to link with something to get part of the standard library. That cleared it up!

---

