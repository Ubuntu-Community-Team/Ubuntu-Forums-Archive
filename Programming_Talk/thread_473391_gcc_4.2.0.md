---
title: "gcc 4.2.0"
date: 2007-06-14
forum: Programming Talk
---

### Post by galeron on 2007-06-14
Hey,

I installed gcc 4.2.0 in my home directory (using the --prefix=<whatever>). It was successfully compiled and installed.

However, when I tried to run a C++ program
```
g++ -fopenmp code.cpp
```

I got the error that the library iostream.h was not found. i.e., 
```

code.cpp:1:20: error: iostream: No such file or directory
code.cpp: In function &#8216;int main()&#8217;:
code.cpp:6: error: &#8216;cout&#8217; was not declared in this scope

```

My program is attached below:
```

#include <iostream>
#include <omp.h>
using namespace std;
int main(){
        omp_set_num_threads(4);
        cout << omp_get_num_threads();
        return 0;}

```

Any ideas on how I can rectify this?

---

### Post by duff on 2007-06-14
Did you pass "--enable-languages=c++" to the configure script?

---

### Post by TreeFinger on 2007-06-14
I am a newbie but I tried googling and I believe you should try:

```

#include <iostream.h>

```

---

### Post by galeron on 2007-06-14
Hi guys,

Thanks for the suggestions. Yes, i did enable C++ (in fact, I enabled C, Obj C, C++ and Obj C++). I also tried variations of iostream and iostream.h

Finally I resolved the problem by redownloading the gcc file from another location to recompile. It finally worked :D

---

