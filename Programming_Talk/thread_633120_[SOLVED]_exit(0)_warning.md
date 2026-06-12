---
title: "[SOLVED] exit(0) warning"
date: 2007-12-06
forum: Programming Talk
---

### Post by adityakavoor on 2007-12-06
this is my C program .. foo.c
```

int main()
{
	exit(0);
}

```

I compile it 
```
cc foo.c

foo.c: In function ‘main’:
foo.c:3: warning: incompatible implicit declaration of built-in function ‘exit’

```

What shud I do to mask the warning ??

---

### Post by jespdj on 2007-12-06
Add the following line at the beginning of your source file:
```
#include <stdlib.h>
```

---

### Post by adityakavoor on 2007-12-06
Thank You :)

---

