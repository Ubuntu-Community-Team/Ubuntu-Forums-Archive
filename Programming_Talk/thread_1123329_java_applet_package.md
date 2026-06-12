---
title: "java applet package"
date: 2009-04-12
forum: Programming Talk
---

### Post by ggankhuy on 2009-04-12
can someone tell me what package i have to install to start using the java applet class?
right now, whenever i do put following statement: 
import java.awt.applet.*;
I get a compilation error. Thanks!

---

### Post by Jiraiya_sama on 2009-04-12
I don't know that there is a specific package for it. I just installed openjdk6 and I was good to go.

---

### Post by myrtle1908 on 2009-04-12
There is no applet package in awt.  I think you want:-

```
import java.applet.Applet;
```

---

