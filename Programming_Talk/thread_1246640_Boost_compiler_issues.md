---
title: "Boost compiler issues"
date: 2009-08-21
forum: Programming Talk
---

### Post by ShaolinF on 2009-08-21
Hi Guys
I am trying to using the boost::thread feature. Whenever I compile I get the following error:

$ c++ -I /usr/local/boost_1_39_0 filereader.cc -o fr /usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a

```
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::thread::detach()':
thread.cpp:(.text+0x13f): undefined reference to `pthread_detach'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::detail::set_current_thread_data(boost::detail::thread_data_base*)':
thread.cpp:(.text+0x24a): undefined reference to `pthread_setspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::detail::(anonymous namespace)::create_current_thread_tls_key()':
thread.cpp:(.text+0x266): undefined reference to `pthread_key_create'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::detail::get_current_thread_data()':
thread.cpp:(.text+0x293): undefined reference to `pthread_getspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::thread::start_thread()':
thread.cpp:(.text+0x610): undefined reference to `pthread_create'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `thread_proxy':
thread.cpp:(.text+0x6f7): undefined reference to `pthread_setspecific'
thread.cpp:(.text+0x736): undefined reference to `pthread_setspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::(anonymous namespace)::make_external_thread_data()':
thread.cpp:(.text+0xb8e): undefined reference to `pthread_setspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::this_thread::interruption_requested()':
thread.cpp:(.text+0xefe): undefined reference to `pthread_getspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::this_thread::interruption_enabled()':
thread.cpp:(.text+0xf63): undefined reference to `pthread_getspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::detail::find_tss_data(void const*)':
thread.cpp:(.text+0xfa7): undefined reference to `pthread_getspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::this_thread::interruption_point()':
thread.cpp:(.text+0x1019): undefined reference to `pthread_getspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::this_thread::restore_interruption::~restore_interruption()':
thread.cpp:(.text+0x10c3): undefined reference to `pthread_getspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o):thread.cpp:(.text+0x10e8): more undefined references to `pthread_getspecific' follow
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::thread::timed_join(boost::posix_time::ptime const&)':
thread.cpp:(.text+0x1c27): undefined reference to `pthread_join'
thread.cpp:(.text+0x1cf9): undefined reference to `pthread_getspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::thread::join()':
thread.cpp:(.text+0x1f30): undefined reference to `pthread_getspecific'
thread.cpp:(.text+0x1fd5): undefined reference to `pthread_join'
thread.cpp:(.text+0x20df): undefined reference to `pthread_getspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(thread.o): In function `boost::this_thread::sleep(boost::posix_time::ptime const&)':
thread.cpp:(.text+0x22a6): undefined reference to `pthread_getspecific'
thread.cpp:(.text+0x23b0): undefined reference to `pthread_getspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(once.o): In function `boost::detail::get_once_per_thread_epoch()':
once.cpp:(.text+0x17): undefined reference to `pthread_once'
once.cpp:(.text+0x24): undefined reference to `pthread_getspecific'
once.cpp:(.text+0x53): undefined reference to `pthread_setspecific'
/usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a(once.o): In function `create_epoch_tss_key':
once.cpp:(.text+0x86): undefined reference to `pthread_key_create'
collect2: ld returned 1 exit status
```

Anyone know where Im going wrong ?
Im using Ubuntu 9.04

---

### Post by ShaolinF on 2009-08-21
problem fixed. I needed to include the pthread lib to the commandline in order for it to work:

c++ -I /usr/local/boost_1_39_0 filereader.cc -o fr /usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a **_-lpthread_**

---

### Post by dwhitney67 on 2009-08-22
Your solution, albeit that it worked, does not seem right.  Perhaps a "feature" of using Boost 1.39.0?

Typically when using Boost library (ver 1.37.0) that is available from the Ubuntu repos, the only library that one needs to specify is libboost_thread-mt.so (-lboost_thread-mt).

Anyhow, good luck with your project.  If you are developing under Ubuntu, and you have no specific requirement to use Boost 1.39.0, then perhaps you should consider using the version in the Ubuntu repo.

---

