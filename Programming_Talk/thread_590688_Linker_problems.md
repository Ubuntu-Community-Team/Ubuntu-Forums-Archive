---
title: "Linker problems"
date: 2007-10-25
forum: Programming Talk
---

### Post by edfredcoder on 2007-10-25
Hi, I am having some trouble with linking any C programs. For example:

```

$ cat > test.c
main () { printf("Test\n"); }
$ gcc test.c -o test
test.c: In function 'main':
test.c:1: warning: incompatible implicit declaration of built-in function 'printf'
test.c:1:30: warning: no newline at end of file
collect2: cannot find 'ld'

```

Does anyone know what is wrong? (The linker is in my path)
Any help is appreciated.

-Kevin

---

### Post by kaamos on 2007-10-25
```

#include <stdio.h>
#include <stdlib.h>

```

---

### Post by edfredcoder on 2007-10-25
No, that will not fix it. It is a linker error, not a compiler error.

---

### Post by kaamos on 2007-10-25
Did you actually try what was suggested before answering? Or read the part about build-essential in the wiki?

---

### Post by edfredcoder on 2007-10-25
I'm sorry my earlier post sounded so abrasive. I wasn't thinking much when I wrote it.
I did try what you suggested. I hadn't heard of build essential though. Thank you for the information.

-Kevin

---

