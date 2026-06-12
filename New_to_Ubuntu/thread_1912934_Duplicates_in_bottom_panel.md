---
title: "Duplicates in bottom panel"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by ericstrom on 2012-01-21
Using Lucid Lynx 10.04

New issue for me. Suddenly when I open an application, I get duplicate icons showing in the bottom panel. For example, when I open Chrome browser, I am showing two copies in the bottom panel. This happens with other applications also like Open Office. So, as you would imagine, if I open a few different applications, my panel becomes full quickly.

If I close the application, both will close in the panel. Tried a restart but the problem persists.

Everything seems to run normally other than annoying duplicates issue.

What causes this ?  More importantly, how do I fix it ?

---

### Post by BC59 on 2012-01-21
Try this
```
rm -r ~/.gconf*
```

---

### Post by cmcanulty on 2012-01-21
You probably have 2 instances of window list in panel try removing the thing that looks like a separator and it will probably be cured rt cl+ alt to remove items in classic

---

