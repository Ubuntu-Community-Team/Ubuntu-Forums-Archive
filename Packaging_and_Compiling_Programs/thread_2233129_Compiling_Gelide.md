---
title: "Compiling Gelide"
date: 2014-07-06
forum: Packaging and Compiling Programs
---

### Post by lunaservant on 2014-07-06
I am trying to compile Gelide on Ubuntu 14 and I had some issues with the configure stage but managed to get past them.  Now I am having trouble with the make stage and can't understand what the problem is.  the error output is below:

```
utils/process.cpp:78:19: error: ‘close’ was not declared in this scope   close(m_proc_out);
                   ^
make[2]: *** [process.o] Error 1
make[2]: Leaving directory `/home/ridge/Downloads/Emulator_ROMS/gelide-0.1.5/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ridge/Downloads/Emulator_ROMS/gelide-0.1.5'
make: *** [all] Error 2



```

---

### Post by lunaservant on 2014-07-06
I found a work around so just ignore this or delete it or whatever

---

### Post by Toz on 2014-07-06
*Moving to **Packaging and Compiling Programs***

The code is buggy - its missing a declaration for close() in src/utils/process.cpp. Just add:
```
#include <unistd.h>
```
...to the headers section of that file.

See: [https://github.com/DAP-DarkneSS/obs/commit/ab97329150c6898fea3a67507aa91ef87b98cba4]("https://github.com/DAP-DarkneSS/obs/commit/ab97329150c6898fea3a67507aa91ef87b98cba4")

---

### Post by Toz on 2014-07-06
> **lunaservant said:**
> I found a work around so just ignore this or delete it or whatever

You ninja'd me. Lets leave it here with the solution in case some one else looks.

---

