---
title: "how to write this simple shell script"
date: 2007-02-25
forum: Programming Talk
---

### Post by vinboy on 2007-02-25
anyone good at scripting?

please help me write a bash/shell script to track what package i have installed manually:

```
aptins kubuntu-desktop
```
the aptins record the {argument} into a file and invoke       apt-get install {argument}

```
aptrem kubuntu-desktop
```
the aptins remove the {argument} from a file and invoke           apt-get remove {argument}

or is there similar scripts/tools available?

thanks in advance :guitar:

---

### Post by lnostdal on 2007-02-25
hm, you should know that these things are already logged in /var/log/aptitude

..or is this not what you're after?

edit:
the log file looks reasonably parsable too :)

---

