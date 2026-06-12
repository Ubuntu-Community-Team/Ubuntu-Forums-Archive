---
title: "gcc fixed division"
date: 2007-01-13
forum: Programming Talk
---

### Post by Hacim on 2007-01-13
Hello, I always thought that integer division return a floating point value,for example:

(32/ 512) == 0.0625
but unless I cast each number to a float first like this:

(float(32) / float(512))

it just drops the decimal.Am I remembering wrong or is there a compiler flag that could be set?

thanks you.

---

### Post by cylon359 on 2007-01-13
integer division returns an integer...

---

### Post by jblebrun on 2007-01-13
> **Hacim said:**
> Hello, I always thought that integer division return a floating point value,for example:

(32/ 512) == 0.0625
but unless I cast each number to a float first like this:

(float(32) / float(512))

it just drops the decimal.Am I remembering wrong or is there a compiler flag that could be set?

thanks you.

Yes, as cyclon said, if you specify two integers, the result of a division will be an integer. There is an easier way to force floating point division, though. If any of the numbers is determined to be floating point by the compiler then the expression will be evaluated as a floating point expression. So just write:

32.0/512

---

