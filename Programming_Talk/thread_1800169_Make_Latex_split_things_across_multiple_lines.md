---
title: "Make Latex split things across multiple lines"
date: 2011-07-08
forum: Programming Talk
---

### Post by DBQ on 2011-07-08
Hi everybody.

I have this problem with latex if I do: {\it some very very long sentence which should span multiple lines} the whole sentence ends up on one line and goes right past the margin?

Any ideas on how to make it automatically split across multiple lines?

Thanks You!

---

### Post by nmaster on 2011-07-08
this doesn't really fit in "programming talk"...

try this:
```

\itshape
The quick brown fox jumps over the lazy dog.
\normalshape

```
[http://www.latex-community.org/forum/viewtopic.php?f=19&t=5492](http://www.latex-community.org/forum/viewtopic.php?f=19&t=5492)

---

### Post by DBQ on 2011-07-08
Thank you, I will give it a try.  BTW, the reason I posted it here was because I am writing a program part of which is manipulating latex; should have mentioned that in the beginning ;)

---

### Post by nmaster on 2011-07-11
did it work for you? if so, you should mark this as "SOLVED".

---

