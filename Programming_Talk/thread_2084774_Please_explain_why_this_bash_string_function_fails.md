---
title: "Please explain why this bash string function fails"
date: 2012-11-16
forum: Programming Talk
---

### Post by nhtrader on 2012-11-16
Ubuntu 12.04.1 LTS
GNU bash, version 4.2.24(1)-release (x86_64-pc-linux-gnu)


I'm looking to replace '/' with '-'

why is output 11-/11-/2012 and not 11-11-2012?


#!/bin/bash
a=11/11/2012
b=${a//\//-/}
echo $a  $b
exit

OUTPUT:
11/11/2012   11-/11-/2012

---

### Post by Vaphell on 2012-11-16
```
$ a=11/11/2012
$ echo ${a//\//-}
11-11-2012
```

---

### Post by nhtrader on 2012-11-16
> **Vaphell said:**
> ```
$ a=11/11/2012
$ echo ${a//\//-}
11-11-2012
```

Thank you. This works perfectly.

---

