---
title: "Conversion between UTF-8 and Unicode"
date: 2007-05-07
forum: Programming Talk
---

### Post by alphilli on 2007-05-07
In an application written in C++ I need to be able to convert text from Unicode to UTF-8 and from UTF-8 to Unicode.

Are there any built-in functions to do those conversions on a Linux platform?

---

### Post by cwaldbieser on 2007-05-09
> **alphilli said:**
> In an application written in C++ I need to be able to convert text from Unicode to UTF-8 and from UTF-8 to Unicode.

Are there any built-in functions to do those conversions on a Linux platform?

UTF-8 is an encoding of Unicode.  Are you trying to convert to another encoding?  If so, which one?  UTF-16?  UTF-32?

---

### Post by alphilli on 2007-05-09
I need to convert between UTF-32 and UTF-8. 

I know that they are both Unicode encodings but they are totally different representations of Unicode.

---

### Post by cwaldbieser on 2007-05-10
> **alphilli said:**
> I need to convert between UTF-32 and UTF-8. 

I know that they are both Unicode encodings but they are totally different representations of Unicode.
Try "iconv".  It is in the repositories.  There are also libiconv libraries ($ apt-cache search iconv).
[http://www.gnu.org/software/libiconv/]("http://www.gnu.org/software/libiconv/")

---

