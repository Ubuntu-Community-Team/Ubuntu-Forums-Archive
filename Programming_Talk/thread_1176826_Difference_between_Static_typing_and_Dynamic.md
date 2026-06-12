---
title: "Difference between Static typing and Dynamic"
date: 2009-06-02
forum: Programming Talk
---

### Post by ThewhiteLynx on 2009-06-02
What is the difference between static typing and Dynamic typing?  I keep hearing the two phrases used saying "Java is static" and "Python is Dynamic" but what is the difference?

---

### Post by simeon87 on 2009-06-02
I'd have to look the definition up but roughly: static typing means the types of variables are known at compile time and dynamic typing means the typing are determined at runtime.

Java is static because you define the type for each variable, e.g. int width, Box box, etc.

Python is dynamic because you simply write a variable and a value and the type can easily be changed at runtime (so you can write width = 3 and then later width = "foobar" so the type now changes from int to string).

Also see:

[http://en.wikipedia.org/wiki/Type_system#Static_typing](http://en.wikipedia.org/wiki/Type_system#Static_typing)
[http://en.wikipedia.org/wiki/Type_system#Dynamic_typing](http://en.wikipedia.org/wiki/Type_system#Dynamic_typing)

---

### Post by ThewhiteLynx on 2009-06-02
Ah, I had a feeling that was the case.  I once used a language named Dr. Scheme that was dynamic, so I was hoping it was possible for other cases.

Thanks

---

