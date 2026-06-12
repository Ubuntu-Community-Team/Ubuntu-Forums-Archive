---
title: "c++ questions"
date: 2007-12-06
forum: Programming Talk
---

### Post by zerofreeze on 2007-12-06
-i want someone to tell me a program that's similar to dev-c++ to install and build console application on.
-i have a built console application that i made on windows, can it works on ubuntu ?

---

### Post by ray bot on 2007-12-06
> -i want someone to tell me a program that's similar to dev-c++ to install and build console application on.
Try either kdevelop or anjuta

> -i have a built console application that i made on windows, can it works on ubuntu ?
That depends on how you wrote your program.  If it uses libraries that are only available on Windows, then it will only run on Windows.  Otherwise it should compile and run just fine in Ubuntu.

---

### Post by zerofreeze on 2007-12-06
where can i install anjuta ?

---

### Post by rbprogrammer on 2007-12-06
> **zerofreeze said:**
> where can i install anjuta ?
in synaptic for GNOME or if you use KDE then in adept

or you could go command line and do:
```

sudo apt-get install anjuta

```

---

### Post by SledgeHammer_999 on 2007-12-06
You could also use [Code::Blocks](www.codeblocks.org). I reccomend you to use the nightly builds because the stable one is really old.

---

### Post by jespdj on 2007-12-06
Beware that the Anjuta v2.2.0 package for Gutsy is broken and doesn't work well.

I've downloaded the sources for Anjuta v2.2.2 from [www.anjuta.org](www.anjuta.org) and compiled it myself, and that works much better than the Gutsy Anjuta package.

---

