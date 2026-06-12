---
title: "undefined reference to `assert'"
date: 2010-07-26
forum: Packaging and Compiling Programs
---

### Post by _sluimers_ on 2010-07-26
I'm having trouble to compile a program that uses libaudiere, which I compiled as well as I want to use the latest svn version because it has ALSA support.

The exact error:

```

/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libaudiere.so: undefined reference to `assert'

```

I tried compiling libaudiere.so with -I/usr/include, but that doesn't help.

---

### Post by anglican on 2010-07-26
> **_sluimers_ said:**
> I'm having trouble to compile a program that uses libaudiere, which I compiled as well as I want to use the latest svn version because it has ALSA support.

The exact error:

```

/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/libaudiere.so: undefined reference to `assert'

```I tried compiling libaudiere.so with -I/usr/include, but that doesn't help.
I'd expect to see that error if a source file is missing the necessary include:
```
#include <assert.h>

```
Presumably a look at all the other compiler output will show you which source file is missing that inclusion.

H

---

### Post by _sluimers_ on 2010-07-26
Thank you very much! :D

Yes, I overlooked those warnings during compiling.

---

