---
title: "Mingw cross compiler undefined reference to __gcov"
date: 2016-08-19
forum: Packaging and Compiling Programs
---

### Post by auto333 on 2016-08-19
I am running Ubuntu 16.04 with the default repository.

When I try to to instrumentate the following example with g++ everything works as expected:
g++ -o test -fprofile-generate -lgcov test.cpp
```

#include <iostream>

int main()
{
int d=0;
for(int i=0; i<10; ++i)
{
d+=i;
std::cout << d << std::endl;
}
return 0;
}

```

However when I try to do the same with mingw I run into the following errors:

```

[COLOR=#000000][FONT=Verdana]x86_64-w64-mingw32-g++ -o test -fprofile-generate -lgcov test.cpp
/tmp/ccsOAum1.o:test.cpp:(.text+0x1a): undefined reference to `__gcov_indirect_call_profiler_v2'
/tmp/ccsOAum1.o:test.cpp:(.text+0x34): undefined reference to `__gcov_time_profiler'
/tmp/ccsOAum1.o:test.cpp:(.text+0xe2): undefined reference to `__gcov_indirect_call_profiler_v2'
/tmp/ccsOAum1.o:test.cpp:(.text+0x10e): undefined reference to `__gcov_time_profiler'
/tmp/ccsOAum1.o:test.cpp:(.text+0x151): undefined reference to `__gcov_indirect_call_profiler_v2'
/tmp/ccsOAum1.o:test.cpp:(.text+0x17d): undefined reference to `__gcov_time_profiler'
/tmp/ccsOAum1.o:test.cpp:(.text+0x20c): undefined reference to `__gcov_indirect_call_profiler_v2'
/tmp/ccsOAum1.o:test.cpp:(.text+0x238): undefined reference to `__gcov_time_profiler'
/tmp/ccsOAum1.o:test.cpp:(.data+0xa0): undefined reference to `__gcov_merge_time_profile'
/tmp/ccsOAum1.o:test.cpp:(.rdata$.refptr.__gcov_indirect_call_callee[.refptr.__gcov_indirect_call_callee]+0x0): undefined reference to `__gcov_indirect_call_callee'
collect2: error: ld returned 1 exit status[/FONT][/COLOR]

```

Does anybody know what is happening here?
Kind regards

---

### Post by steeldriver on 2016-08-19
Have you tried switching the order of the library and source file?

```

x86_64-w64-mingw32-g++ -o test -fprofile-generate **test.cpp -lgcov**

```

---

### Post by auto333 on 2016-08-19
Thanks for your quick reply. Changing the order of the library as suggested results in the same error.

I added the path of the lib to my command but it does not change things either.
-L/usr/lib/gcc/x86_64-w64-mingw32/5.3-posix/

---

