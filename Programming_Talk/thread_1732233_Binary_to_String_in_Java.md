---
title: "Binary to String in Java"
date: 2011-04-18
forum: Programming Talk
---

### Post by DBQ on 2011-04-18
Hi Everybody,

I am implementing RSA in Java (my own RSA). I want to transform my encrypted text, which is a number, back into a string. Is there a way to do that?

Thank You!

---

### Post by myrtle1908 on 2011-04-18
You probably want something like ...

```
String s = Integer.toString(myInt);
```

---

