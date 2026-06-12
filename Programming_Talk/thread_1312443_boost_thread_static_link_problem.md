---
title: "boost thread static link problem"
date: 2009-11-03
forum: Programming Talk
---

### Post by j_goldie on 2009-11-03
Hi,
I'm using Karmic version x64, boost lib version 1.38
When building boost.thread project with flag Boost_USE_STATIC_LIBS ON, I get the errors listed below, while if I build them with
Boost_USE_STATIC_LIBS OFF, everything works fine. I mean not only builds, but it executes as it should.
Btw, the Karmic is fresh install (no upgrade). CMake, boost 1.38 and g++ are from ubuntu repos. Everything worked just fine with Jaunty (with boost 1.35 actually). Is this the boost problem, or something else?
To reproduce the above problem, just take the code and CMakeLists.txt listed below. I should note that the same problem persists with boost 1.40 in repo too.
best regards,
j_goldie

```

// main.cpp
#include <boost/thread/thread.hpp>
#include <iostream>

void hello() 
{
    std::cout << "Hello world, I'm a thread!" << std::endl;
}

int main(int argc, char* argv[]) 
{
    boost::thread thrd(&hello);
    thrd.join();
    return 0;
}
```
This is the CMakeLists.txt
```
cmake_minimum_required (VERSION 2.6) 
PROJECT(boost_text)
set(Boost_USE_STATIC_LIBS   ON)
set(Boost_USE_MULTITHREADED ON)
find_package( Boost COMPONENTS thread)
INCLUDE_DIRECTORIES(${Boost_INCLUDE_DIRS})
ADD_EXECUTABLE( probni  MACOSX_BUNDLE main.cpp )
TARGET_LINK_LIBRARIES(probni ${Boost_LIBRARIES})
```
And Finally, here are the error messages:
```
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `T.1030':
(.text+0x1b8): undefined reference to `pthread_key_create'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `boost::thread::detach()':
(.text+0x76d): undefined reference to `pthread_detach'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `thread_proxy':
(.text+0xbd0): undefined reference to `pthread_setspecific'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `thread_proxy':
(.text+0xbf5): undefined reference to `pthread_setspecific'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `boost::thread::start_thread()':
(.text+0xdf0): undefined reference to `pthread_create'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `boost::(anonymous namespace)::make_external_thread_data()':
(.text+0x1071): undefined reference to `pthread_setspecific'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `boost::thread::timed_join(boost::posix_time::ptime const&)':
(.text+0x1811): undefined reference to `pthread_join'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `boost::thread::join()':
(.text+0x1c69): undefined reference to `pthread_join'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `boost::detail::(anonymous namespace)::create_current_thread_tls_key()':
(.text+0x10b): undefined reference to `pthread_key_create'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `boost::detail::get_current_thread_data()':
(.text+0x224): undefined reference to `pthread_getspecific'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(thread.o): In function `boost::detail::set_current_thread_data(boost::detail::thread_data_base*)':
(.text+0x474): undefined reference to `pthread_setspecific'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(once.o): In function `boost::detail::get_once_per_thread_epoch()':
(.text+0xc): undefined reference to `pthread_once'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(once.o): In function `boost::detail::get_once_per_thread_epoch()':
(.text+0x17): undefined reference to `pthread_getspecific'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(once.o): In function `boost::detail::get_once_per_thread_epoch()':
(.text+0x42): undefined reference to `pthread_setspecific'
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/libboost_thread-mt.a(once.o): In function `create_epoch_tss_key':
(.text+0x6b): undefined reference to `pthread_key_create'
collect2: ld returned 1 exit status
make[2]: *** [Console/console_claw] Error 1
make[1]: *** [Console/CMakeFiles/console_claw.dir/all] Error 2
make: *** [all] Error 2
```

---

### Post by dwhitney67 on 2009-11-03
I do not have access to an x64 system, much less with Karmic (Ubuntu 9.10).

However, by examining the link errors that you reported, it would be my guess that you need to link with the pthread library.  On the command line or within a typical Makefile, you would need to specify -lpthread.

---

### Post by j_goldie on 2009-11-03
Yeah, I know, but the problem still remains. I mean, it worked on jaunty, now it doesn't with Karmic. As I said, the dynamic linking works like it should, while the static fails, and that's what puzzles me. The cmake version is the same, 2.6.4. What I'm trying to say is that the makefile was the same in Jaunty and in Karmic.
any thoughts?
best regards,
j_goldie

---

### Post by weishigoname on 2009-12-24
I meet the some problem too,and I do not kown how ?

---

### Post by Some Penguin on 2009-12-24
The obvious question is whether you actually have a static version of the pthread library... perhaps you only have the dynamically linked library.

---

