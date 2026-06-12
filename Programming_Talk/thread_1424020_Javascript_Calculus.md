---
title: "Javascript Calculus"
date: 2010-03-07
forum: Programming Talk
---

### Post by ctult on 2010-03-07
Hi!

I am making a physics simulator in Javascript.  I need a calculus Javascript library for the advanced stuff(explosions, fluid dynamics, etc...)

Thanks in advance.

CTuLT

---

### Post by nvteighen on 2010-03-07
Could you please tell us how did you come to the idea of using Javascript for this? Not that it is impossible, but surely highly impractical. For instance, I doubt decent JS libraries are available to do those tasks.

---

### Post by myrtle1908 on 2010-03-07
It's actually very doable.  Some JS and physics stuff ... [http://www.andrew-hoyer.com/experiments/cloth](http://www.andrew-hoyer.com/experiments/cloth)

---

### Post by kahumba on 2010-03-07
That example is nice but hogs both my CPUs. For example the math operations in C++ are waaaaay faster than in JavaScript (test yourself before arguing).
So I'd use JavaScript only for **learning** physics, and **not** for production quality stuff.

---

### Post by myrtle1908 on 2010-03-07
> **kahumba said:**
> That example is nice but hogs both my CPUs. For example the math operations in C++ are waaaaay faster than in JavaScript (test yourself before arguing).
So I'd use JavaScript only for **learning** physics, and **not** for production quality stuff.

Interesting.  Moving the cloth around consumes almost zero CPU on my quad core.  You may get more mileage with Chrome.  That said, obviously JavaScript is not ideal for this sort of thing.  Still, it can be done.

---

### Post by kahumba on 2010-03-07
I just checked with Chrome - indeed, a lot less CPU usage. But then again, less than 10% use Chrome and even then a C++ implementation would be a lot faster. Not to mention that that example **doesn't work** in IE6 nor IE7 at all (not that I care), haven't tested it in IE8. If the OP is ok with that and doesn't care about much more sophisticated stuff - go on with JavaScript, otherwise (I'd) use a compiled language.

---

