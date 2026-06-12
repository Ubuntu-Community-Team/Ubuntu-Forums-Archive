---
title: "Incompatible types (java)"
date: 2009-04-27
forum: Programming Talk
---

### Post by SpyroViper on 2009-04-27
Hey guys,

I think this is me being dumb again lol.  BUt I can't for the life of me figure out why I'm getting an incompatible types error on this line:

> {
 int i = 0; 
while (i< authoreId. length)
 return System.out.print (i);

}

The rest of my code is fine, it's just this line.

Thanks guys! :guitar:

---

### Post by kpkeerthi on 2009-04-27
You are returning System.out.print(i), the type of which is **void**.

---

### Post by SpyroViper on 2009-04-27
Ahh,

Thank you!  Me being dumb agan lol!

---

