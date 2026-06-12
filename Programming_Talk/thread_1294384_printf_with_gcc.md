---
title: "printf with gcc"
date: 2009-10-18
forum: Programming Talk
---

### Post by wirate on 2009-10-18
i use code::blocks to write my beginner programs. however, when i directly compile my source at bash using
```
gcc <filename.c> -o <programname>
```

it says "printf not declared". which file do i include to use functions like printf and scanf?

---

### Post by Joeb454 on 2009-10-18
you need to ```
#include <stdio.h>
``` at the top of the file, if you haven't already.

Also - it may be worth checking if build-essential is installed, by running ```
sudo apt-get install build-essential
```

---

### Post by wirate on 2009-10-19
stdio worked. thanks

---

