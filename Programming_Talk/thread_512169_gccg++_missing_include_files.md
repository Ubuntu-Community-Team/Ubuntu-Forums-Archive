---
title: "gcc/g++ missing include files"
date: 2007-07-28
forum: Programming Talk
---

### Post by smo0th on 2007-07-28
Hello, this is the first time I'm trying to write c code in linux and it pops the following errors:

dong.c:2:18: error: stdio.c: No such file or directory
dong.c:3:19: error: stdlib.c: No such file or directory

I checked the packages with apt-get and synaptic and everything seems ok, what should I do to get this working? :(

---

### Post by bbzbryce on 2007-07-28
> **smo0th said:**
> Hello, this is the first time I'm trying to write c code in linux and it pops the following errors:

dong.c:2:18: error: stdio.c: No such file or directory
dong.c:3:19: error: stdlib.c: No such file or directory

I checked the packages with apt-get and synaptic and everything seems ok, what should I do to get this working? :(

Can you list the code which gives you this error? Does the following work?

```
#include <stdio.h>

int main() {
	printf("Ubuntu rocks\n");
}
```

Save to test.c and compile by: gcc test.c
Run: ./a.out

---

### Post by smo0th on 2007-07-28
yikes!.. ](*,)

I found the error I was mispelling stdlib.c for stdlib.h, duh, sorry about that. :oops:

---

### Post by bbzbryce on 2007-07-28
> **smo0th said:**
> yikes!.. ](*,)

I found the error I was mispelling stdlib.c for stdlib.h, duh, sorry about that. :oops:

That's what I was thinking, but didn't want to blatantly ask. ;)

---

### Post by pcmanlin on 2007-07-28
:) try:
sudo apt-get install build-essential

maybe it will work.

---

