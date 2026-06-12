---
title: "Standard Template Library"
date: 2010-08-16
forum: Programming Talk
---

### Post by aatwo on 2010-08-16
On my new ubuntu machine I used 'sudo apt-get install build-essential' to get everything i needed for c++, but when I try to compile a simple program using the standard template library I get errors saying the files cannot be found:

```

#include <stdio.h>
#include <iostream.h>
using namespace std;


```

Any ideas why?

---

### Post by schauerlich on 2010-08-16
C++ headers don't use .h extensions. Also, for C standard library headers, drop the .h and add a 'c' to the front.

```
#include <cstdio>
#include <iostream>

int main(void) {
  printf("I like to mix C and C++.\n");
  std::cout << "Don't be like me. Choose one and stick with it." << std::endl;
  return 0;
}
```

Also, make sure you're compiling with g++ and not plain gcc.

---

### Post by jon zendatta on 2010-08-16
> #include <stdio.h>
yep this is true for standard C

---

### Post by aatwo on 2010-08-17
hehe what a silly error on my behalf. Thanks for pointing that out.

---

