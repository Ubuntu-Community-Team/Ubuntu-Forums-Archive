---
title: "BASH: math with variables"
date: 2007-09-29
forum: Programming Talk
---

### Post by ryanVickers on 2007-09-29
I would like to do some simple math for some code.

ex.
variableA=variableB*variableC

what could be the code for this?

---

### Post by Ramses de Norre on 2007-09-29
variableA=$((variableB*variableC))

---

### Post by ryanVickers on 2007-09-29
and what about

variableA=variableA "Divided by" 1000 * 1024

---

### Post by Ramses de Norre on 2007-09-29
variableA=$(($variableA/1000*1024)) ;)

Mind to use braces when needed, I wasn't sure whether you meant /1000*1024 or /(1000*1024).

---

### Post by ryanVickers on 2007-09-29
thanks :)

I still needed to do a little testing, but I guess it's better to do the multiplying first and then divide ;)

---

### Post by cwaldbieser on 2007-09-29
> **ryanVickers said:**
> thanks :)

I still needed to do a little testing, but I guess it's better to do the multiplying first and then divide ;)

Note that bash does integer math.  If you need fractions, you need another program like "bc" or "awk".

---

### Post by ryanVickers on 2007-09-29
ok then.  This is perfect for now though :)

---

### Post by Claus7 on 2009-10-14
Hello,

> **cwaldbieser said:**
> Note that bash does integer math.  If you need fractions, you need another program like "bc" or "awk".

thanks for posting that!

Regards!

---

### Post by Izziedee on 2011-08-31
Wow, 4 years later, just the answer I was looking for. Thanks!

---

### Post by sisco311 on 2011-10-01
Necrobumping.

Thread Closed.

New one here: [http://ubuntuforums.org/showthread.php?t=1852886](http://ubuntuforums.org/showthread.php?t=1852886)

---

