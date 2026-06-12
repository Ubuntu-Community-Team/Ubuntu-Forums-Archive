---
title: "difference between hash and hash ref in perl"
date: 2007-03-09
forum: Programming Talk
---

### Post by monkeyking on 2007-03-09
Could someone elaborete on the difference between hash's and hash references in perl.

And when to use what?

Thanks in advance

---

### Post by Mr. C. on 2007-03-09
A hash is a basic data type in Perl.  It uses keys to access its contents.

A hash ref is an abbreviation to a reference to a hash.  References are scalars, that is simple values.  It is a scalar value that contains essentially, a pointer to the actual hash itself.

Got it?

MrC

---

### Post by monkeyking on 2007-03-09
yes,
pointer was the magic word
thanks.

---

