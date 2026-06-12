---
title: "Quick Java question"
date: 2009-12-06
forum: Programming Talk
---

### Post by skipsbro on 2009-12-06
Does anyone know if Java has a method similar to the C/C++ "system()" function?

---

### Post by Reiger on 2009-12-06
Something like

Process proc = Runtime.getRuntime().exec(/* pick your argument flavour here; they come in many varieties */);

And then obtain your output via the I/O streams of the process.

Quick Google for a tutorial: [http://devdaily.com/java/edu/pj/pj010016/](http://devdaily.com/java/edu/pj/pj010016/)

---

