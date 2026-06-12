---
title: "error using valgrind client requests with threads"
date: 2018-06-29
forum: Programming Talk
---

### Post by chuchi on 2018-06-29
Hi everyone,


I am playing around with valgrind client memchech requests and found that when using threads, valgrind reports erros that it shouldn't report. Take this example code: 


```

//main.cpp
#include <cassert>
#include <thread>
#include <valgrind/memcheck.h>


void func()
{


}


int main()
{
    unsigned int initialErrors_, finalErrors_;
    VALGRIND_DO_ADDED_LEAK_CHECK;
    initialErrors_ = VALGRIND_COUNT_ERRORS;


    std::thread t1(func);
    t1.join();


    VALGRIND_DO_ADDED_LEAK_CHECK;
    finalErrors_ = VALGRIND_COUNT_ERRORS;


    assert(initialErrors_ == finalErrors_);


    return 0;
}

```


This is an excerpt of the output I get if I execute this with 'valgrind --leak-check=full ./main': 


```



288 (+288) bytes in 1 (+1) blocks are possibly lost in loss record 1 of 2
    at 0x4C2FB55: calloc (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
    by 0x40138A4: allocate_dtv (dl-tls.c:322)
    by 0x40138A4: _dl_allocate_tls (dl-tls.c:539)
    by 0x53DA26E: allocate_stack (allocatestack.c:588)
    by 0x53DA26E: pthread_create@@GLIBC_2.2.5 (pthread_create.c:539)
    by 0x4EF2DC2: std::thread::_M_start_thread(std::shared_ptr<std::thread::_Impl_base>, void (*)()) (in /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21)
    by 0x4014D7: std::thread::thread<void (&)()>(void (&)()) (thread:137)
    by 0x4010AD: main (main.cpp:16)


 LEAK SUMMARY:
    definitely lost: 0 (+0) bytes in 0 (+0) blocks
    indirectly lost: 0 (+0) bytes in 0 (+0) blocks
      possibly lost: 288 (+288) bytes in 1 (+1) blocks
    still reachable: 72,704 (+0) bytes in 1 (+0) blocks
         suppressed: 0 (+0) bytes in 0 (+0) blocks
 Reachable blocks (those to which a pointer was found) are not shown.
 To see them, rerun with: --leak-check=full --show-leak-kinds=all


main: main.cpp:22: int main(): Assertion `initialErrors_ == finalErrors_' failed.



```




Why am I getting a 'possibly lost' using valgrind client requests with a thread?


Thanks a lot!!

---

