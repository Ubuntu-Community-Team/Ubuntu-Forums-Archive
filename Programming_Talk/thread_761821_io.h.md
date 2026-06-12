---
title: "io.h"
date: 2008-04-21
forum: Programming Talk
---

### Post by drinu21 on 2008-04-21
hi all,

i am writing a program to control the parallel port, and i have to include asm/io.h to control it, but i cannot find io.h. i searched in usr/include/asm but its not there. i am using kubuntu 7.04. do you have any idea on what can i do.?

thanks 

adrian

---

### Post by tseliot on 2008-04-21
make sure the linux-headers for your kernel are installed.

Type:
```
sudo updatedb
```

```
locate io.h | grep asm
```

and you will find the exact path.

---

### Post by Caduceus on 2008-04-21
Maybe io.h is a header for a language? .h counds like C to me...

---

### Post by kalana:D on 2010-07-26
#include<sys/io.h>
This works!!!!!!!;)

---

