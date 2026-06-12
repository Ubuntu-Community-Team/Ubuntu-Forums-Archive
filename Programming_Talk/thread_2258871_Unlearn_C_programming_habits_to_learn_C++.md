---
title: "Unlearn C programming habits to learn C++?"
date: 2014-12-31
forum: Programming Talk
---

### Post by flaymond on 2014-12-31
What that supposed to mean? I always found on Internet that learning C will also learn bad habits, and the habits not good for C++. What or which 'habits' does it mean?

---

### Post by TheFu on 2014-12-31
The 2 languages have different styles.  Being elegant in C++ is different from being elegant in C. Sometimes it is just indentation rules that are different. Camel-case is different, Sometimes it is how C programs automatically casts between different data types and C++ wants things to have explicit translations for type safety. This last one is huge.  Implicitly converting a char into an int is bad, same for converting a pointer into an int or comparing a pointer to '0' instead of 'NULL'.

There are probably many others - just been too long since I did any pure C programming.

---

### Post by flaymond on 2014-12-31
Hmm, I see..well...which is the most used for specific purpose? Well, I heard that C is a highly portable even it's a low level language. What made C++ is more powerful than C others than OO? I'm learning C now (I don't know if I made a bad choice), I wanna understand the procedural programming...(I only found old books about C that hardly to understand as a teenager and a non-native English speaker)....I got a lot of books(I take a sip of it) that cover C++ like C++ Primer Plus in a 'dialogue way'. I know that you will not tell me which to choose, but at least tell me..that what I'm learning now is helpful if someday I need to use C++. I really don't know what I'm doing.

---

### Post by spjackson on 2014-12-31
Some programmers, once they have learnt "how to program" in a particular language, when they come to use a different language, see it as a matter of translating what they already know (i.e. "how to program") to the syntax of the new language. "The determined Real Programmer can write FORTRAN programs in any language." (see [http://en.wikiquote.org/wiki/Fortran](http://en.wikiquote.org/wiki/Fortran))

Programming languages differ not only in syntax but in other ways too. The truth is that there are many ways to program (e.g. procedural, functional, OOP). Some languages encourage a particular paradigm, others (e.g. C++) readily support many paradigms.

When you come to C++ you should not be thinking, "I have a problem. How would I solve it in C and how do I express that solution in C++?" But rather you should think, "I have a problem. How do I solve it in C++?" Note that this trap is a danger for any programmer whose first language is not C++ but it is of greatest danger to C programmers because a C solution can often be directly expressed in C++.

See also "1.6.1 Suggestions for C Programmers" in [http://www.stroustrup.com/3rd_notes.pdf](http://www.stroustrup.com/3rd_notes.pdf).  (The 4th edition lists 10 points, but I don't think that is accessible online for free.)

---

### Post by TheFu on 2014-12-31
My considered response on how to learn to program. [http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program)
C is the second language that I recommend.

BTW, I can write FORTRAN in any language. ;)

I use *C++ Primer Plus* many, many, many years ago in a C++ class.  After that class, never used it again, for anything. Is that the white book or the purple one?

---

### Post by flaymond on 2014-12-31
Thanks guys! It'll help me a lot to stay motivated! :KS

---

