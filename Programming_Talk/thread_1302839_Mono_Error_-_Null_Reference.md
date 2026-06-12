---
title: "Mono Error - Null Reference"
date: 2009-10-27
forum: Programming Talk
---

### Post by sandivilli on 2009-10-27
Hi, i`ve tried to compile a code with gmcsc/csc (Mono), and it compiled ok.
But when i execute, the bin file it gives me:

A null reference or invalid value was found [GDI+ status: InvalidParameter]

... anyone have a clue?

Thanks

---

### Post by PaulM1985 on 2009-10-27
I can't really say too accurately without looking at the code, but I am guessing that you are trying to access something that is not initialised.

Is there anything like:

MyClass aThing;

aThing.doMethod();


without an
aThing = new MyClass();
between?

Could you post some code? 

Paul

---

### Post by sandivilli on 2009-10-30
Hi, the code is here: 

[http://zetcode.com/tutorials/monowinformstutorial/snake/](http://zetcode.com/tutorials/monowinformstutorial/snake/)

i guess, its right.

Thanks

---

