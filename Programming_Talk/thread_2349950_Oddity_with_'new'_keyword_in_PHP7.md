---
title: "Oddity with 'new' keyword in PHP7"
date: 2017-01-20
forum: Programming Talk
---

### Post by QIII on 2017-01-20
I've noticed something weird.

I'm using Bluefish for some php development.  I'm trying to instantiate a class, which is in an include in another .php file.

I suppose that doesn't matter so much.

What does matter is that the 'new' keyword is not behaving as a keyword.  

That is, in the following, the keyword 'new' isn't "doing" anything.

```
$fooObject = new barClass();
```

It's not even coming up in keyword autocomplete.

Any ideas like "it's in front of your face, old man!"

---

### Post by QIII on 2017-01-20
Meh.  Never mind.  It was autocompleting in another IED, so that was a red herring.

But I did notice a typo in the include, which ended up being the actual problem.

All is well.  I cleaned my trifocals and I am back on track again.

---

