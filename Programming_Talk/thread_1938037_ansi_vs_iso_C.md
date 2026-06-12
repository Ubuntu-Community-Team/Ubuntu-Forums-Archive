---
title: "ansi vs iso C"
date: 2012-03-09
forum: Programming Talk
---

### Post by conradin on 2012-03-09
Hi Everyone, 
I'm reading a book on C programing which specifies itself as ANSI. 
So I have a few questions about ANSI vs ISO.
Like does it matter at all? What is the modern standard? Which has more relivance in the linux community. And what does gcc use?

---

### Post by lisati on 2012-03-09
*Thread moved to **Programming Talk**.*

My experience with C is limited. No doubt there will be others who are more qualified than myself who will be forthcoming with their eloquence.

---

### Post by schauerlich on 2012-03-09
ANSI and ISO are just different organizations that ratify standards. The standards that one of them produces is usually named by the year it came out: C89 (aka C90) is the standard released in 1989, and the other major standard C99 was released in 1999. In general, you can assume most compilers/systems will implement C89 - it's been around a long time and has pretty much universally been adopted. C99, despite being around for over 10 years, is still not supported everywhere. Major open source compilers (gcc, clang) implement C99 fully, Microsoft's C compiler, however, doesn't. So, if you want to write portable code, it's best to restrict yourself to C89. If you know your code will always be run on a platform that supports it, it's fine to use C99. Note also that some compilers have their own extensions to the language (gnu89, gnu99, etc from gcc. it defaults to gnu89).

Generally, when one says "ANSI C", they mean C89/C90.

Note: there's also a new C11 standard, but since it was only just published it doesn't have wide support.

---

### Post by conradin on 2012-03-09
Thanks schauerlich, That helps a lot!

---

### Post by trent.josephsen on 2012-03-10
ISO C90 and ANSI C89 are pretty much exactly the same thing; at least, I can't recall hearing of any substantial difference between them.  C99 is not maintained by ANSI and is never referred to as "ANSI".

Off topic, C11 adds a handful of new features and makes some of the mandatory C99 features optional (most notably VLAs).  No major compilers have adopted C11 yet.

---

