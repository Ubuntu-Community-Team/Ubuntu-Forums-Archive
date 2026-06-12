---
title: "Postscript question"
date: 2012-12-02
forum: Programming Talk
---

### Post by PryGuy on 2012-12-02
Good day, everyone!

I have a string, something like en_US, fr_FR, ru_RU, etc. I need to extract the last two capital letters after the underscore. As you understand there's a fixed number of characters everywhere, so it is probably possible to extract the last two chars.

This is a gfxboot script so it's not Postscript Level 2 and 'search' operator doesn't work. Tried to google it but there's not much information on Postscript.

Please help,
thanks in advance.

---

### Post by Lux Perpetua on 2012-12-02
Isn't it simply: ```
dup length 2 sub 2 getinterval
```

---

