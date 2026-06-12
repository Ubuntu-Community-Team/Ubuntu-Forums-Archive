---
title: "Problem w/ bash script for sys stats"
date: 2008-04-28
forum: Programming Talk
---

### Post by AKern011 on 2008-04-28
I run two linux servers with LAMP on them. They both have dev suites on them to allow me to program/administer from school. One of the projects I have been working on is a bash script to output system information such as proc, mem used/avail, drive space used/avil, etc. into an html file. But when I try to use *uname -p* in my bash script, the proc returns as *unknown* on my system with . Yet, it shows up as two Intel Core 2 E8500s @ 3.16GHz in my System Monitor>Systems tab.

Does anyone know any way in either PHP or bash to get the proc of my system so I can use it with any of my servers and have it actually display anything other than unknown?

---

### Post by dwhitney67 on 2008-04-29
This works for me:
cat /proc/cpuinfo | grep "model name" | cut -d ' ' -f 3-

---

### Post by ghostdog74 on 2008-04-29
```

awk -F":" '/model name/{print $2}' /proc/cpuinfo

```

---

