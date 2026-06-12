---
title: "[SOLVED] Help - C libraries dissapeared!"
date: 2007-08-17
forum: Programming Talk
---

### Post by Vadi on 2007-08-17
Hello,

For some reason, my C libraries disappeared today - when I try and compile a program, I get this:

```
header.h:28:20: error: string.h: No such file or directory
header.h:29:19: error: ctype.h: No such file or directory
header.h:30:19: error: stdio.h: No such file or directory
header.h:31:20: error: stdlib.h: No such file or directory
header.h:32:19: error: errno.h: No such file or directory
header.h:90:26: error: arpa/telnet.h: No such file or directory
```

I'm relatively new to Linux, so where's a chance that I deleted them somehow :/

What package should I download to get them back?

Edit: I have a suspicion that I might have removed them when I used the 'remove orphaned packages' tool. But I can't remember the name of the package..

---

### Post by LaRoza on 2007-08-17
```

sudo aptitude install build-essential

```

If you are using:
```

#include "string.h"

```
Change the quotes to <>.

---

### Post by Vadi on 2007-08-17
Thank you *so* much! That worked.

---

### Post by LaRoza on 2007-08-17
> **Vadi said:**
> Thank you *so* much! That worked.

Which one? 

(If your problem is solved, mark the thread as solved.)

---

### Post by Wybiral on 2007-08-17
> **LaRoza said:**
> Which one? 

(If your problem is solved, mark the thread as solved.)

The use of (<>) vs ("") only defines the starting place that the compiler searches for them. It should still find them if using "" so I assume they just didn't install build-essential.

---

### Post by Vadi on 2007-08-17
The first solution to install the package did it.

I had it installed before, or at least something, because the program was compiling right before. I must have removed it by accident.

How can I modify the title? I can't find an option to do so.

Thanks again!

---

### Post by Vadi on 2007-08-20
One more problem that I'm getting:

```
main.c:120:44: error: zlib.h: No such file or directory
```

In line 120, I just have

```
#  include <zlib.h>
```.

I did a seach for zlib.h, and it -is- on my system. Any idea why can't it find it? :(

---

### Post by Vadi on 2007-08-20
Downloading zlib1g-dev solved it... thanks all!

---

