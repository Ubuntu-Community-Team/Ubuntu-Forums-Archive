---
title: "‘PRIu64’ print macro for uint64_t"
date: 2013-01-05
forum: Programming Talk
---

### Post by bird1500 on 2013-01-05
Hi,
I prefer printf() despite using C++ and I found [here]("http://www.remlab.net/op/integer.shtml") there's a standard way to print a uint64_t (gcc apparently uses %llu or so) called "**PRIu64" **but apparently it's not supported under Linux, [this]("http://tcpreplay.synfin.net/ticket/496") doesn't work for me in 12.10 amd64 with g++.
What should I do?

---

### Post by Bachstelze on 2013-01-05
What you should do is not use them. They are C, not C++.

*EDIT:* Actually they seem to be in C++11

```
firas@itsuki ~ % cat test.cpp                   
#include <cinttypes>
#include <cstdio>

int main(void)
{
    uint64_t x = 5;
    printf("%" PRIu64 "\n", x);
}
firas@itsuki ~ % g++ -std=c++11 -o test test.cpp
firas@itsuki ~ % ./test 
5

```

---

### Post by bird1500 on 2013-01-05
Thanks,
C seems to work out of the box (without -std=c11):

gcc test.c -o test
```

#include <inttypes.h>
#include <stdio.h>

int main() {
    uint64_t x = 5;
    printf("%" PRIu64 "\n", x);
    
    return 0;
}

```~$ ./test
5
~$

I guess I'll stick with llu or lu until recent Linux distros switch to C++11 by default.

---

### Post by Bachstelze on 2013-01-06
> **bird1500 said:**
> 
I guess I'll stick with llu or lu until recent Linux distros switch to C++11 by default.

You're probably going to have to wait a long time, since gcc still doesn't use C99 by default. ;) It's totally okay to use C++11 if it is available, you just need to pass a special flag during compilation, that's what Makefiles are for.

---

