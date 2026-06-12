---
title: "Assertions in eclipse"
date: 2006-10-17
forum: Programming Talk
---

### Post by Ramses de Norre on 2006-10-17
Does anyone know how to turn on assertion checking in eclipse?

---

### Post by amo-ej1 on 2006-10-18
I assume you're talking about Java projects here, change your JRE  to have the flags -ea

from java -help
```

    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions


```

---

### Post by Ramses de Norre on 2006-10-18
OK that did the trick!
I guess I misread the man page and I used the -esa option instead of -ea, which didn't work =).

And it's indeed for java projects.

---

