---
title: "[SOLVED] gksu is not allowing parameters passed to xosview"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by timandjulz on 2008-10-24
This is a simplified command line to show the problem.  The real command line requires gksu.

I execute:
```
xosview +net -ints -page
```
This displays network stats and hides interrupts and page file usage.

When I do the same using gksu, I get an error:
```
tim@office:~/bogus$ gksu xosview +net -ints -page
gksu: invalid option -- e
GKsu version 2.0.0
<snip>

```

The command line works if I don't use gksu.  It also works with sudo.  If I remove "-page" from xosview's command line then it works with gksu.

What gives?
Tim

---

### Post by caljohnsmith on 2008-10-24
Sometimes it's enough to put quotes around the command argument of gksu:
```
gksu "xosview +net -ints -page"
```
See if maybe that works.

---

### Post by timandjulz on 2008-10-24
Son of a gun.  You are correct caljohnsmith.  It looks like everything must be passed in quotes.

Thanks!
Tim

---

