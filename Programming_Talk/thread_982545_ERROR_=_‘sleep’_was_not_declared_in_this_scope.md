---
title: "ERROR = ‘sleep’ was not declared in this scope"
date: 2008-11-14
forum: Programming Talk
---

### Post by ChurroLoco on 2008-11-14
Hi getting this error in my code:

```
‘Sleep’ was not declared in this scope
```

I was also getting:

```
‘exit’ was not declared in this scope
```

But that went away once I included <stdlib.h>.
Is there another header that defines Sleep?

---

### Post by samjh on 2008-11-14
It's sleep(), not Sleep().

You need:```
#include <unistd.h>
```

[http://opengroup.org/onlinepubs/007908799/xsh/sleep.html](http://opengroup.org/onlinepubs/007908799/xsh/sleep.html)

---

