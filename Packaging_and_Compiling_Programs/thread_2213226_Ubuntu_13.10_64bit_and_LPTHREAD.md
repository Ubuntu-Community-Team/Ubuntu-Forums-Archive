---
title: "Ubuntu 13.10 64bit and LPTHREAD"
date: 2014-03-25
forum: Packaging and Compiling Programs
---

### Post by aylerni on 2014-03-25
Hello, Im trying to compile a multithreaded program I found on stackoverflow, and there was a missing reference.
So I googled, and found out I needed lpthread.

I googled further, and found out -lpthread is all you need.
I added it: g++ -lpthread  untitled.cpp -o untitled

But it still says "undefined reference to `pthread_create' "

```

  GNU nano 2.2.6                                  File: untitled.cpp                                                                           

#include <iostream>
#include <ctime>
#include <pthread.h>

void *print_message(void*){
    std::cout << "Threading\n";
}



int main() {

    pthread_t t1;

    pthread_create(&t1, NULL, &print_message, NULL);
    std::cout << "Hello";

    return 0;
}

```

Is this error Ubuntu based?

---

