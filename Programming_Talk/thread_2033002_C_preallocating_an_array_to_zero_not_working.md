---
title: "C preallocating an array to zero not working"
date: 2012-07-25
forum: Programming Talk
---

### Post by scorpious on 2012-07-25
as seen in attachment. I cannot figure out what I've done wrong.

---

### Post by the_unforgiven on 2012-07-25
```
counts[**letter**]
```
??

Your index variable is **i** - not **letter**.
letter runs from 65 (i = 0) .... 91 (i = 26).

There is no problem with the allocation - it's the printing that's messed up.

---

### Post by scorpious on 2012-07-25
OMG I cannot believe I missed it. I spent hours looking at that.

Thanks

---

### Post by Tony Flury on 2012-07-25
When posting code in future - use the code tags (the # button on the toolbar), rather than posting a screen shot :-).

Also - can you mark this thread as solved - go to Thread Tools.

---

### Post by the_unforgiven on 2012-07-25
BTW, to keep it more readable, you could've also done:
```
letter = i + 'A';
```
just so that it's explicitly stated what you're trying to do :)

---

### Post by scorpious on 2012-07-25
ok thankyou

---

