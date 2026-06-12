---
title: "Properly installing GCC"
date: 2008-01-01
forum: Packaging and Compiling Programs
---

### Post by Johnny Appleseed on 2008-01-01
So I typed ```
apt-get install gcc
``` and received the response:

```
gcc is already the newest version.
```

But then I tried to use ```
./configure
``` and received:

```
configure: error: C++ compiler cannot create executables
```

So I tried writing a simple test program:

```
#include <stdio.h>
void main()
{
printf("the C program is working");
}
```

Then I typed ```
gcc test.c
``` and got:

```
test.c:1:19: error: stdio.h: No such file or directory
test.c: In function ‘main’:
test.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
test.c:3: warning: return type of ‘main’ is not ‘int’
```

The first line of that got me wondering, so I tried:

```
cd /
sudo find -name stdio.h
```

No such file.

So my system is claiming that gcc is completely installed, and yet that there is no file by the name of stdio.h!  What is going on?  How could I properly install gcc and get it working?

---

### Post by LaRoza on 2008-01-01
```

sudo aptitude install build-essential

```

gcc is installed, but is useless without the above package.

---

