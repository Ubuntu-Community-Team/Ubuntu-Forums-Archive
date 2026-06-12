---
title: "Compilation error"
date: 2007-11-18
forum: Packaging and Compiling Programs
---

### Post by ahsonbol on 2007-11-18
Hi,

I am trying to add a simple system call. I do all the necessary steps (modifying unistd.h , modifying syscall_table.S,modifying Makefile, build the kernel). I wrote a simple user code to try the new added system call
I got this compilation error

code.c:8: error: expected declaration specifiers or ‘...’ before ‘mycall’
code.c:8: error: expected declaration specifiers or ‘...’ before ‘arg1’
code.c:8: error: expected declaration specifiers or ‘...’ before ‘arg2’

my code is
```

#include <linux/errno.h>
#include <sys/syscall.h>
#include <linux/unistd.h>
#include <stdio.h>

#define __NR_mycall 320

int _syscall2(int,mycall,int,arg1,int,arg2);

int main()
{
	int z;
	z=mycall(7,8);
	printf("%d\n",z);
	return 0;
}

```

Any help???

---

### Post by ddrichardson on 2007-11-18
Haven't used C/C++ in ages but take out the comma between the type and variable name:```

int _syscall2(int,mycall,int,arg1,int,arg2);
```to:```
int _syscall2(int mycall,int arg1,int arg2);
```

---

### Post by ahsonbol on 2007-11-18
I was just a typing error
but errors still exist 
```

#include <linux/errno.h>
#include <sys/syscall.h>
#include <linux/unistd.h>
#include <stdio.h>

#define __NR_mycall 320

_syscall2(int mycall,int,arg1,int,arg2);

int main()
{
	int z;
	z=mycall(7,8);
	printf("%d\n",z);
	return 0;
}

```

errors are:
code.c:8: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;arg1&#8217;
code.c:8: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;arg2&#8217;
code.c:8: warning: data definition has no type or storage class

---

### Post by ddrichardson on 2007-11-18
Dude you still have commas between the int types and the int variables!

---

### Post by ahsonbol on 2007-11-18
well I checked the book I am reading and I found that these commas are necessary: the first two parameters represent the return type and the system call name. the other parameters represent the type of the argument.

I know that function prototypes don't require these commas but it is written in the book in this fashion

the line is
_syscall2(int,mycall,int,arg1,int,arg2);

---

### Post by ddrichardson on 2007-11-18
I don't doubt you, but the compiler reckons it's wrong.

---

