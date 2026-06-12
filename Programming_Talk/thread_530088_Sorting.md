---
title: "Sorting?"
date: 2007-08-20
forum: Programming Talk
---

### Post by beckham on 2007-08-20
I know how to sort a few number but i dont know to sort alphabet. Can anybody  help me?

---

### Post by finer recliner on 2007-08-20
what language? different languages will handle single characters differently. some will be very easy for comparing against one another (perl for example, in which a string is scalar).

---

### Post by fct on 2007-08-20
In which language?

Languages like C implement strings as arrays of char, that is itself a numeric type. For example, comparisons like 'A'<'B' or 'A' == 'A' work. You just need to make those operations for every char in the string.

---

### Post by beckham on 2007-09-07
Its in c language. I have found made the loop myself.Thanks for the efforts

---

### Post by gnusci on 2007-09-07
Here you have the reference of a bunch of function you can use for string operation:

[http://www.cplusplus.com/reference/clibrary/cstring/](http://www.cplusplus.com/reference/clibrary/cstring/)

In particular I think you may find [COLOR="Red"]strcmp[/COLOR] very useful:

[http://www.cplusplus.com/reference/clibrary/cstring/strcmp.html](http://www.cplusplus.com/reference/clibrary/cstring/strcmp.html)

---

