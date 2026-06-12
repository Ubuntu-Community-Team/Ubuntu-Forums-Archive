---
title: "C code not running"
date: 2012-01-26
forum: Programming Talk
---

### Post by rishab1988 on 2012-01-26
I just copied and pasted this code, but it doesn't seem to be running.

The code is as follows :

#include <stdio.h>

void main()
(
printf("Hello World! \n");
}

---

### Post by mörgæs on 2012-01-26
Hi, welcome to the fora.

I have moved your post to Programming Talk.

---

### Post by QIII on 2012-01-26
Try this:

```

#include <stdio.h>

void main()
**{**
printf("Hello World! \n");
}
```instead of this

```

#include <stdio.h>

void main()
(
printf("Hello World! \n");
}

```

You have a parenthesis rather than a curly brace.

---

### Post by Bachstelze on 2012-01-26
Correct:

```
#include <stdio.h>

int main(void)
{
    printf("Hello World! \n");
    return 0;
}
```

return may be omitted in C99 only (not the default).

---

### Post by QIII on 2012-01-26
Eh, yep.

I guess that { stuck out like a sore thumb and I wasn't even looking at anything else.

I've been using IDEs for far too long and letting them yell at me.

---

