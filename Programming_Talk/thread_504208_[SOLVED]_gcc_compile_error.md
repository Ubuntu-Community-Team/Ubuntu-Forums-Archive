---
title: "[SOLVED] gcc compile error"
date: 2007-07-18
forum: Programming Talk
---

### Post by PastorTaz on 2007-07-18
I'm working on a practical exam on smashing a stack.  I'm running Feisty on a Dell 820.  I have Feisty in both VMWare and native boot.

The code I'm using is C++.  Here is the code used...


```
void function (char *str)

{
char buffer [100];
strcpy(buffer, str); //The strcpy function does not check for bounds
}

int main ()
{
char string[512];
int i;

for (i=0; i<512; i++) //loop 512 times
{
string[i] = 'A';
}
function(string);
exit(0);
}

```

When I use gcc I get this error

root@vm-ubuntu:/lpt/ceptlab# gcc -o overflow3 overflow.c
overflow.c: In function ‘function’:
overflow.c:5: warning: incompatible implicit declaration of built-in function ‘strcpy’
overflow.c: In function ‘main’:
overflow.c:18: warning: incompatible implicit declaration of built-in function ‘exit’
root@vm-ubuntu:/lpt/ceptlab# 

When I use gcc-3.3 it compiles just fine.

Can anyone tell me why?
Thanks,

---

### Post by Wybiral on 2007-07-18
Did you:
```

#include <stdlib.h>
#include <string.h>

```
?

If so, you may need to install "build-essential"

```

sudo apt-get install build-essential

```

---

### Post by PastorTaz on 2007-07-18
No I did not use those includes.

Should I install build-essential anyway?

---

### Post by xtacocorex on 2007-07-18
Yes, build-essential contains the compilers and the libraries needed to compile.

---

### Post by Wybiral on 2007-07-18
> **PastorTaz said:**
> No I did not use those includes.

Should I install build-essential anyway?

Well, "strcpy" is from "string.h" and "exit" is from "stdlib.h" so you will need to include them. If you include them and still get errors, then you might not have the headers which is why I say to get "build-essential".

---

### Post by PastorTaz on 2007-07-19
Thanks Wybiral! It worked like a charm.

---

