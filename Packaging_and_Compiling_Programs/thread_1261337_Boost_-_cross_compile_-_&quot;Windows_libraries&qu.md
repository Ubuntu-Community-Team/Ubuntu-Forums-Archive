---
title: "Boost - cross compile - &quot;Windows libraries&quot; from &quot;Linux&quot;"
date: 2009-09-08
forum: Packaging and Compiling Programs
---

### Post by petike on 2009-09-08
Hello,
I have downloaded "boost" (1.40.0) source code from "www.boost.org" homepage and trying to compile the libraries to "binary" form.

I have done it without problems for "linux" version following these steps:
--1. I have downloaded and extracted boost source code.
--2. Then I have run "bootstrap.sh" file with the following options (note: I have only compiled the "thread" part of the boost libraries):
```
./bootstrap.sh --with-libraries=thread
```--3. Then I have run "bjam" (the "stage" option means that the output will be created in the "stage/" subdirectory in the current directory):
```
./bjam stage
```and voila: I got the library "binaries": ".a" and ".so" files. And that's what I wanted for Linux.


And now the problematic part: compiling to "Windows" version of the libraries.
I don't know what I have to do. I was trying find out the answer on many forums, google and also on the "www.boost.org" homepage. But nothing helped me.
I think that to compile the "Linux" libraries I should compile it with "gcc" and to compile the "Windows" libraries (".lib" and ".dll") I should use "i586-mingw32msvc-gcc" compiler (included in mingw32 package). I also tried to edit the file "project-config.jam" in the "boost root directory" (the directory where the source code of boost has been extracted) with this:
```
using gcc : : i586-mingw32msvc-gcc ;
```but after executing:
```
./bjam stage
```it gives me a lot of errors:
```

...patience...
...found 518 targets...
...updating 10 targets...
gcc.compile.c++ bin.v2/libs/thread/build/gcc-mingw-4.2/release/threading-multi/pthread/thread.o
i586-mingw32msvc-gcc: unrecognized option '-pthread'
libs/thread/src/pthread/thread.cpp:1: warning: -fPIC ignored for target (all code is position independent)
In file included from ./boost/thread/mutex.hpp:16,
                 from ./boost/thread/pthread/thread_data.hpp:12,
                 from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/mutex.hpp:8:21: error: pthread.h: No such file or directory
In file included from ./boost/thread/pthread/mutex.hpp:16,
                 from ./boost/thread/mutex.hpp:16,
                 from ./boost/thread/pthread/thread_data.hpp:12,
                 from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/timespec.hpp: In function ‘boost::detail::timespec boost::detail::get_timespec(const boost::system_time&)’:
./boost/thread/pthread/timespec.hpp:22: error: return type ‘struct boost::detail::timespec’ is incomplete
./boost/thread/pthread/timespec.hpp:24: error: variable ‘boost::detail::timespec timeout’ has initializer but incomplete type
In file included from ./boost/thread/pthread/mutex.hpp:17,
                 from ./boost/thread/mutex.hpp:16,
                 from ./boost/thread/pthread/thread_data.hpp:12,
                 from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: At global scope:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:20: error: ISO C++ forbids declaration of ‘pthread_mutex_t’ with no type
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:20: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:22: error: expected `)' before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: In destructor ‘boost::pthread::pthread_mutex_scoped_lock::~pthread_mutex_scoped_lock()’:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:29: error: ‘m’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:29: error: ‘pthread_mutex_unlock’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: At global scope:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:36: error: ISO C++ forbids declaration of ‘pthread_mutex_t’ with no type
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:36: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:38: error: expected `)' before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: In destructor ‘boost::pthread::pthread_mutex_scoped_unlock::~pthread_mutex_scoped_unlock()’:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:45: error: ‘m’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:45: error: ‘pthread_mutex_lock’ was not declared in this scope
In file included from ./boost/thread/mutex.hpp:16,
                 from ./boost/thread/pthread/thread_data.hpp:12,
                 from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/mutex.hpp: At global scope:
./boost/thread/pthread/mutex.hpp:33: error: ‘pthread_mutex_t’ does not name a type
./boost/thread/pthread/mutex.hpp:65: error: ISO C++ forbids declaration of ‘pthread_mutex_t’ with no type
./boost/thread/pthread/mutex.hpp:65: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/mutex.hpp:66: error: ‘native_handle_type’ does not name a type
./boost/thread/pthread/mutex.hpp: In constructor ‘boost::mutex::mutex()’:
./boost/thread/pthread/mutex.hpp:37: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:37: error: ‘pthread_mutex_init’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In destructor ‘boost::mutex::~mutex()’:
./boost/thread/pthread/mutex.hpp:45: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:45: error: ‘pthread_mutex_destroy’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘void boost::mutex::lock()’:
./boost/thread/pthread/mutex.hpp:50: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:50: error: ‘pthread_mutex_lock’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘void boost::mutex::unlock()’:
./boost/thread/pthread/mutex.hpp:55: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:55: error: ‘pthread_mutex_unlock’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘bool boost::mutex::try_lock()’:
./boost/thread/pthread/mutex.hpp:60: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:60: error: ‘pthread_mutex_trylock’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: At global scope:
./boost/thread/pthread/mutex.hpp:81: error: ‘pthread_mutex_t’ does not name a type
./boost/thread/pthread/mutex.hpp:83: error: ‘pthread_cond_t’ does not name a type
./boost/thread/pthread/mutex.hpp: In constructor ‘boost::timed_mutex::timed_mutex()’:
./boost/thread/pthread/mutex.hpp:89: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:89: error: ‘pthread_mutex_init’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:95: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:95: error: ‘pthread_cond_init’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:98: error: ‘pthread_mutex_destroy’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In destructor ‘boost::timed_mutex::~timed_mutex()’:
./boost/thread/pthread/mutex.hpp:106: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:106: error: ‘pthread_mutex_destroy’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:108: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:108: error: ‘pthread_cond_destroy’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘void boost::timed_mutex::lock()’:
./boost/thread/pthread/mutex.hpp:156: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:159: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:159: error: ‘pthread_cond_wait’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘void boost::timed_mutex::unlock()’:
./boost/thread/pthread/mutex.hpp:166: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:168: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:168: error: ‘pthread_cond_signal’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘bool boost::timed_mutex::try_lock()’:
./boost/thread/pthread/mutex.hpp:173: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘bool boost::timed_mutex::timed_lock(const boost::system_time&)’:
./boost/thread/pthread/mutex.hpp:184: error: variable ‘const boost::timespec timeout’ has initializer but incomplete type
./boost/thread/pthread/mutex.hpp:185: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:188: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:188: error: ‘pthread_cond_timedwait’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:189: error: ‘ETIMEDOUT’ was not declared in this scope
In file included from ./boost/thread/pthread/thread_data.hpp:15,
                 from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/condition_variable_fwd.hpp: At global scope:
./boost/thread/pthread/condition_variable_fwd.hpp:22: error: ‘pthread_cond_t’ does not name a type
./boost/thread/pthread/condition_variable_fwd.hpp:84: error: ISO C++ forbids declaration of ‘pthread_cond_t’ with no type
./boost/thread/pthread/condition_variable_fwd.hpp:84: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/condition_variable_fwd.hpp:85: error: ‘native_handle_type’ does not name a type
./boost/thread/pthread/condition_variable_fwd.hpp: In constructor ‘boost::condition_variable::condition_variable()’:
./boost/thread/pthread/condition_variable_fwd.hpp:30: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/condition_variable_fwd.hpp:30: error: ‘pthread_cond_init’ was not declared in this scope
./boost/thread/pthread/condition_variable_fwd.hpp: In destructor ‘boost::condition_variable::~condition_variable()’:
./boost/thread/pthread/condition_variable_fwd.hpp:38: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/condition_variable_fwd.hpp:38: error: ‘pthread_cond_destroy’ was not declared in this scope
In file included from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/thread_data.hpp: At global scope:
./boost/thread/pthread/thread_data.hpp:35: error: ‘pthread_t’ does not name a type
./boost/thread/pthread/thread_data.hpp:47: error: ISO C++ forbids declaration of ‘pthread_cond_t’ with no type
./boost/thread/pthread/thread_data.hpp:47: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/thread_data.hpp:58: error: ‘pthread_t’ does not name a type
./boost/thread/pthread/thread_data.hpp: In constructor ‘boost::detail::thread_data_base::thread_data_base()’:
./boost/thread/pthread/thread_data.hpp:54: error: class ‘boost::detail::thread_data_base’ does not have any field named ‘current_cond’
./boost/thread/pthread/thread_data.hpp: At global scope:
./boost/thread/pthread/thread_data.hpp:80: error: expected `)' before ‘*’ token
libs/thread/src/pthread/thread.cpp:678: error: expected `}' at end of input
./boost/thread/pthread/thread_data.hpp:76: error: expected unqualified-id at end of input
./boost/thread/pthread/thread_data.hpp:76: error: expected `}' at end of input
./boost/thread/pthread/thread_data.hpp:76: error: expected `}' at end of input

    "i586-mingw32msvc-gcc"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_THREAD_BUILD_DLL=1 -DBOOST_THREAD_POSIX -DNDEBUG  -I"." -c -o "bin.v2/libs/thread/build/gcc-mingw-4.2/release/threading-multi/pthread/thread.o" "libs/thread/src/pthread/thread.cpp"

...failed gcc.compile.c++ bin.v2/libs/thread/build/gcc-mingw-4.2/release/threading-multi/pthread/thread.o...
gcc.compile.c++ bin.v2/libs/thread/build/gcc-mingw-4.2/release/threading-multi/pthread/once.o
i586-mingw32msvc-gcc: unrecognized option '-pthread'
libs/thread/src/pthread/once.cpp:1: warning: -fPIC ignored for target (all code is position independent)
In file included from ./boost/thread/once.hpp:16,
                 from libs/thread/src/pthread/once.cpp:7:
./boost/thread/pthread/once.hpp:14:21: error: pthread.h: No such file or directory
In file included from ./boost/thread/pthread/once.hpp:16,
                 from ./boost/thread/once.hpp:16,
                 from libs/thread/src/pthread/once.cpp:7:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:20: error: ISO C++ forbids declaration of ‘pthread_mutex_t’ with no type
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:20: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:22: error: expected `)' before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: In destructor ‘boost::pthread::pthread_mutex_scoped_lock::~pthread_mutex_scoped_lock()’:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:29: error: ‘m’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:29: error: ‘pthread_mutex_unlock’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: At global scope:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:36: error: ISO C++ forbids declaration of ‘pthread_mutex_t’ with no type
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:36: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:38: error: expected `)' before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: In destructor ‘boost::pthread::pthread_mutex_scoped_unlock::~pthread_mutex_scoped_unlock()’:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:45: error: ‘m’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:45: error: ‘pthread_mutex_lock’ was not declared in this scope
In file included from ./boost/thread/once.hpp:16,
                 from libs/thread/src/pthread/once.cpp:7:
./boost/thread/pthread/once.hpp: At global scope:
./boost/thread/pthread/once.hpp:34: error: ‘pthread_mutex_t’ does not name a type
./boost/thread/pthread/once.hpp:35: error: ‘pthread_cond_t’ does not name a type
./boost/thread/pthread/once.hpp: In function ‘void boost::call_once(boost::once_flag&, Function)’:
./boost/thread/pthread/once.hpp:54: error: ‘once_epoch_mutex’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:63: error: ‘once_epoch_mutex’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:69: error: ‘once_epoch_cv’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:69: error: there are no arguments to ‘pthread_cond_broadcast’ that depend on a template parameter, so a declaration of ‘pthread_cond_broadcast’ must be available
./boost/thread/pthread/once.hpp:69: error: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
./boost/thread/pthread/once.hpp:73: error: ‘once_epoch_cv’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:73: error: there are no arguments to ‘pthread_cond_broadcast’ that depend on a template parameter, so a declaration of ‘pthread_cond_broadcast’ must be available
./boost/thread/pthread/once.hpp:79: error: ‘once_epoch_cv’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:79: error: ‘once_epoch_mutex’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:79: error: there are no arguments to ‘pthread_cond_wait’ that depend on a template parameter, so a declaration of ‘pthread_cond_wait’ must be available
libs/thread/src/pthread/once.cpp: At global scope:
libs/thread/src/pthread/once.cpp:17: error: ‘pthread_mutex_t’ does not name a type
libs/thread/src/pthread/once.cpp:18: error: ‘pthread_cond_t’ does not name a type
libs/thread/src/pthread/once.cpp:22: error: ‘pthread_key_t’ does not name a type
libs/thread/src/pthread/once.cpp:23: error: ‘pthread_once_t’ does not name a type
libs/thread/src/pthread/once.cpp: In function ‘void boost::detail::<unnamed>::create_epoch_tss_key()’:
libs/thread/src/pthread/once.cpp:32: error: ‘epoch_tss_key’ was not declared in this scope
libs/thread/src/pthread/once.cpp:32: error: ‘pthread_key_create’ was not declared in this scope
libs/thread/src/pthread/once.cpp: In function ‘uintmax_t& boost::detail::get_once_per_thread_epoch()’:
libs/thread/src/pthread/once.cpp:39: error: ‘epoch_tss_key_flag’ was not declared in this scope
libs/thread/src/pthread/once.cpp:39: error: ‘pthread_once’ was not declared in this scope
libs/thread/src/pthread/once.cpp:40: error: ‘epoch_tss_key’ was not declared in this scope
libs/thread/src/pthread/once.cpp:40: error: ‘pthread_getspecific’ was not declared in this scope
libs/thread/src/pthread/once.cpp:44: error: ‘pthread_setspecific’ was not declared in this scope
./boost/thread/pthread/once.hpp: In function ‘void boost::call_once(boost::once_flag&, Function) [with Function = void (*)()]’:
./boost/thread/once.hpp:27:   instantiated from here
./boost/thread/pthread/once.hpp:69: error: ‘pthread_cond_broadcast’ was not declared in this scope
./boost/thread/pthread/once.hpp:73: error: ‘pthread_cond_broadcast’ was not declared in this scope
./boost/thread/pthread/once.hpp:79: error: ‘pthread_cond_wait’ was not declared in this scope

    "i586-mingw32msvc-gcc"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread -fPIC  -DBOOST_ALL_NO_LIB=1 -DBOOST_THREAD_BUILD_DLL=1 -DBOOST_THREAD_POSIX -DNDEBUG  -I"." -c -o "bin.v2/libs/thread/build/gcc-mingw-4.2/release/threading-multi/pthread/once.o" "libs/thread/src/pthread/once.cpp"

...failed gcc.compile.c++ bin.v2/libs/thread/build/gcc-mingw-4.2/release/threading-multi/pthread/once.o...
...skipped <pbin.v2/libs/thread/build/gcc-mingw-4.2/release/threading-multi>libboost_thread.so.1.40.0 for lack of <pbin.v2/libs/thread/build/gcc-mingw-4.2/release/threading-multi>pthread/thread.o...
...skipped <pstage/lib>libboost_thread.so.1.40.0 for lack of <pbin.v2/libs/thread/build/gcc-mingw-4.2/release/threading-multi>libboost_thread.so.1.40.0...
...skipped <pstage/lib>libboost_thread.so for lack of <pstage/lib>libboost_thread.so.1.40.0...
gcc.compile.c++ bin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi/pthread/thread.o
i586-mingw32msvc-gcc: unrecognized option '-pthread'
In file included from ./boost/thread/mutex.hpp:16,
                 from ./boost/thread/pthread/thread_data.hpp:12,
                 from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/mutex.hpp:8:21: error: pthread.h: No such file or directory
In file included from ./boost/thread/pthread/mutex.hpp:16,
                 from ./boost/thread/mutex.hpp:16,
                 from ./boost/thread/pthread/thread_data.hpp:12,
                 from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/timespec.hpp: In function ‘boost::detail::timespec boost::detail::get_timespec(const boost::system_time&)’:
./boost/thread/pthread/timespec.hpp:22: error: return type ‘struct boost::detail::timespec’ is incomplete
./boost/thread/pthread/timespec.hpp:24: error: variable ‘boost::detail::timespec timeout’ has initializer but incomplete type
In file included from ./boost/thread/pthread/mutex.hpp:17,
                 from ./boost/thread/mutex.hpp:16,
                 from ./boost/thread/pthread/thread_data.hpp:12,
                 from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: At global scope:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:20: error: ISO C++ forbids declaration of ‘pthread_mutex_t’ with no type
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:20: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:22: error: expected `)' before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: In destructor ‘boost::pthread::pthread_mutex_scoped_lock::~pthread_mutex_scoped_lock()’:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:29: error: ‘m’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:29: error: ‘pthread_mutex_unlock’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: At global scope:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:36: error: ISO C++ forbids declaration of ‘pthread_mutex_t’ with no type
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:36: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:38: error: expected `)' before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: In destructor ‘boost::pthread::pthread_mutex_scoped_unlock::~pthread_mutex_scoped_unlock()’:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:45: error: ‘m’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:45: error: ‘pthread_mutex_lock’ was not declared in this scope
In file included from ./boost/thread/mutex.hpp:16,
                 from ./boost/thread/pthread/thread_data.hpp:12,
                 from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/mutex.hpp: At global scope:
./boost/thread/pthread/mutex.hpp:33: error: ‘pthread_mutex_t’ does not name a type
./boost/thread/pthread/mutex.hpp:65: error: ISO C++ forbids declaration of ‘pthread_mutex_t’ with no type
./boost/thread/pthread/mutex.hpp:65: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/mutex.hpp:66: error: ‘native_handle_type’ does not name a type
./boost/thread/pthread/mutex.hpp: In constructor ‘boost::mutex::mutex()’:
./boost/thread/pthread/mutex.hpp:37: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:37: error: ‘pthread_mutex_init’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In destructor ‘boost::mutex::~mutex()’:
./boost/thread/pthread/mutex.hpp:45: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:45: error: ‘pthread_mutex_destroy’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘void boost::mutex::lock()’:
./boost/thread/pthread/mutex.hpp:50: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:50: error: ‘pthread_mutex_lock’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘void boost::mutex::unlock()’:
./boost/thread/pthread/mutex.hpp:55: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:55: error: ‘pthread_mutex_unlock’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘bool boost::mutex::try_lock()’:
./boost/thread/pthread/mutex.hpp:60: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:60: error: ‘pthread_mutex_trylock’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: At global scope:
./boost/thread/pthread/mutex.hpp:81: error: ‘pthread_mutex_t’ does not name a type
./boost/thread/pthread/mutex.hpp:83: error: ‘pthread_cond_t’ does not name a type
./boost/thread/pthread/mutex.hpp: In constructor ‘boost::timed_mutex::timed_mutex()’:
./boost/thread/pthread/mutex.hpp:89: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:89: error: ‘pthread_mutex_init’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:95: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:95: error: ‘pthread_cond_init’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:98: error: ‘pthread_mutex_destroy’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In destructor ‘boost::timed_mutex::~timed_mutex()’:
./boost/thread/pthread/mutex.hpp:106: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:106: error: ‘pthread_mutex_destroy’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:108: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:108: error: ‘pthread_cond_destroy’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘void boost::timed_mutex::lock()’:
./boost/thread/pthread/mutex.hpp:156: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:159: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:159: error: ‘pthread_cond_wait’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘void boost::timed_mutex::unlock()’:
./boost/thread/pthread/mutex.hpp:166: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:168: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:168: error: ‘pthread_cond_signal’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘bool boost::timed_mutex::try_lock()’:
./boost/thread/pthread/mutex.hpp:173: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp: In member function ‘bool boost::timed_mutex::timed_lock(const boost::system_time&)’:
./boost/thread/pthread/mutex.hpp:184: error: variable ‘const boost::timespec timeout’ has initializer but incomplete type
./boost/thread/pthread/mutex.hpp:185: error: ‘m’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:188: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:188: error: ‘pthread_cond_timedwait’ was not declared in this scope
./boost/thread/pthread/mutex.hpp:189: error: ‘ETIMEDOUT’ was not declared in this scope
In file included from ./boost/thread/pthread/thread_data.hpp:15,
                 from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/condition_variable_fwd.hpp: At global scope:
./boost/thread/pthread/condition_variable_fwd.hpp:22: error: ‘pthread_cond_t’ does not name a type
./boost/thread/pthread/condition_variable_fwd.hpp:84: error: ISO C++ forbids declaration of ‘pthread_cond_t’ with no type
./boost/thread/pthread/condition_variable_fwd.hpp:84: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/condition_variable_fwd.hpp:85: error: ‘native_handle_type’ does not name a type
./boost/thread/pthread/condition_variable_fwd.hpp: In constructor ‘boost::condition_variable::condition_variable()’:
./boost/thread/pthread/condition_variable_fwd.hpp:30: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/condition_variable_fwd.hpp:30: error: ‘pthread_cond_init’ was not declared in this scope
./boost/thread/pthread/condition_variable_fwd.hpp: In destructor ‘boost::condition_variable::~condition_variable()’:
./boost/thread/pthread/condition_variable_fwd.hpp:38: error: ‘cond’ was not declared in this scope
./boost/thread/pthread/condition_variable_fwd.hpp:38: error: ‘pthread_cond_destroy’ was not declared in this scope
In file included from ./boost/thread/thread.hpp:17,
                 from libs/thread/src/pthread/thread.cpp:10:
./boost/thread/pthread/thread_data.hpp: At global scope:
./boost/thread/pthread/thread_data.hpp:35: error: ‘pthread_t’ does not name a type
./boost/thread/pthread/thread_data.hpp:47: error: ISO C++ forbids declaration of ‘pthread_cond_t’ with no type
./boost/thread/pthread/thread_data.hpp:47: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/thread_data.hpp:58: error: ‘pthread_t’ does not name a type
./boost/thread/pthread/thread_data.hpp: In constructor ‘boost::detail::thread_data_base::thread_data_base()’:
./boost/thread/pthread/thread_data.hpp:54: error: class ‘boost::detail::thread_data_base’ does not have any field named ‘current_cond’
./boost/thread/pthread/thread_data.hpp: At global scope:
./boost/thread/pthread/thread_data.hpp:80: error: expected `)' before ‘*’ token
libs/thread/src/pthread/thread.cpp:678: error: expected `}' at end of input
./boost/thread/pthread/thread_data.hpp:76: error: expected unqualified-id at end of input
./boost/thread/pthread/thread_data.hpp:76: error: expected `}' at end of input
./boost/thread/pthread/thread_data.hpp:76: error: expected `}' at end of input

    "i586-mingw32msvc-gcc"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread  -DBOOST_ALL_NO_LIB=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_POSIX -DNDEBUG  -I"." -c -o "bin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi/pthread/thread.o" "libs/thread/src/pthread/thread.cpp"

...failed gcc.compile.c++ bin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi/pthread/thread.o...
gcc.compile.c++ bin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi/pthread/once.o
i586-mingw32msvc-gcc: unrecognized option '-pthread'
In file included from ./boost/thread/once.hpp:16,
                 from libs/thread/src/pthread/once.cpp:7:
./boost/thread/pthread/once.hpp:14:21: error: pthread.h: No such file or directory
In file included from ./boost/thread/pthread/once.hpp:16,
                 from ./boost/thread/once.hpp:16,
                 from libs/thread/src/pthread/once.cpp:7:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:20: error: ISO C++ forbids declaration of ‘pthread_mutex_t’ with no type
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:20: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:22: error: expected `)' before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: In destructor ‘boost::pthread::pthread_mutex_scoped_lock::~pthread_mutex_scoped_lock()’:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:29: error: ‘m’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:29: error: ‘pthread_mutex_unlock’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: At global scope:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:36: error: ISO C++ forbids declaration of ‘pthread_mutex_t’ with no type
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:36: error: expected ‘;’ before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:38: error: expected `)' before ‘*’ token
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp: In destructor ‘boost::pthread::pthread_mutex_scoped_unlock::~pthread_mutex_scoped_unlock()’:
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:45: error: ‘m’ was not declared in this scope
./boost/thread/pthread/pthread_mutex_scoped_lock.hpp:45: error: ‘pthread_mutex_lock’ was not declared in this scope
In file included from ./boost/thread/once.hpp:16,
                 from libs/thread/src/pthread/once.cpp:7:
./boost/thread/pthread/once.hpp: At global scope:
./boost/thread/pthread/once.hpp:34: error: ‘pthread_mutex_t’ does not name a type
./boost/thread/pthread/once.hpp:35: error: ‘pthread_cond_t’ does not name a type
./boost/thread/pthread/once.hpp: In function ‘void boost::call_once(boost::once_flag&, Function)’:
./boost/thread/pthread/once.hpp:54: error: ‘once_epoch_mutex’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:63: error: ‘once_epoch_mutex’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:69: error: ‘once_epoch_cv’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:69: error: there are no arguments to ‘pthread_cond_broadcast’ that depend on a template parameter, so a declaration of ‘pthread_cond_broadcast’ must be available
./boost/thread/pthread/once.hpp:69: error: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
./boost/thread/pthread/once.hpp:73: error: ‘once_epoch_cv’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:73: error: there are no arguments to ‘pthread_cond_broadcast’ that depend on a template parameter, so a declaration of ‘pthread_cond_broadcast’ must be available
./boost/thread/pthread/once.hpp:79: error: ‘once_epoch_cv’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:79: error: ‘once_epoch_mutex’ is not a member of ‘boost::detail’
./boost/thread/pthread/once.hpp:79: error: there are no arguments to ‘pthread_cond_wait’ that depend on a template parameter, so a declaration of ‘pthread_cond_wait’ must be available
libs/thread/src/pthread/once.cpp: At global scope:
libs/thread/src/pthread/once.cpp:17: error: ‘pthread_mutex_t’ does not name a type
libs/thread/src/pthread/once.cpp:18: error: ‘pthread_cond_t’ does not name a type
libs/thread/src/pthread/once.cpp:22: error: ‘pthread_key_t’ does not name a type
libs/thread/src/pthread/once.cpp:23: error: ‘pthread_once_t’ does not name a type
libs/thread/src/pthread/once.cpp: In function ‘void boost::detail::<unnamed>::create_epoch_tss_key()’:
libs/thread/src/pthread/once.cpp:32: error: ‘epoch_tss_key’ was not declared in this scope
libs/thread/src/pthread/once.cpp:32: error: ‘pthread_key_create’ was not declared in this scope
libs/thread/src/pthread/once.cpp: In function ‘uintmax_t& boost::detail::get_once_per_thread_epoch()’:
libs/thread/src/pthread/once.cpp:39: error: ‘epoch_tss_key_flag’ was not declared in this scope
libs/thread/src/pthread/once.cpp:39: error: ‘pthread_once’ was not declared in this scope
libs/thread/src/pthread/once.cpp:40: error: ‘epoch_tss_key’ was not declared in this scope
libs/thread/src/pthread/once.cpp:40: error: ‘pthread_getspecific’ was not declared in this scope
libs/thread/src/pthread/once.cpp:44: error: ‘pthread_setspecific’ was not declared in this scope
./boost/thread/pthread/once.hpp: In function ‘void boost::call_once(boost::once_flag&, Function) [with Function = void (*)()]’:
./boost/thread/once.hpp:27:   instantiated from here
./boost/thread/pthread/once.hpp:69: error: ‘pthread_cond_broadcast’ was not declared in this scope
./boost/thread/pthread/once.hpp:73: error: ‘pthread_cond_broadcast’ was not declared in this scope
./boost/thread/pthread/once.hpp:79: error: ‘pthread_cond_wait’ was not declared in this scope

    "i586-mingw32msvc-gcc"  -ftemplate-depth-128 -O3 -finline-functions -Wno-inline -Wall -pthread  -DBOOST_ALL_NO_LIB=1 -DBOOST_THREAD_BUILD_LIB=1 -DBOOST_THREAD_POSIX -DNDEBUG  -I"." -c -o "bin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi/pthread/once.o" "libs/thread/src/pthread/once.cpp"

...failed gcc.compile.c++ bin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi/pthread/once.o...
...skipped <pbin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi>libboost_thread.a(clean) for lack of <pbin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi>pthread/thread.o...
...skipped <pbin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi>libboost_thread.a for lack of <pbin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi>pthread/thread.o...
...skipped <pstage/lib>libboost_thread.a for lack of <pbin.v2/libs/thread/build/gcc-mingw-4.2/release/link-static/threading-multi>libboost_thread.a...
...failed updating 4 targets...
...skipped 6 targets...

```and nothing was built.

Could anybody help me?

P.S.: I am using "Ubuntu 9.04 Jaunty" and "mingw32" package from repository.


Thanks in advance.

---

### Post by kehon on 2009-09-20
also have same problem and would like some help

---

### Post by LonelyStar on 2011-02-02
Hey,

Kind of an old post, but I have the same question:
How can I cross compile boost from ubuntu to win32?
I have mingw32 installed, and compile cmake or autotools projects. But bjam?!?

Anything solved?
Anyone any input?

Thanks!
Nathan

---

### Post by SevenMachines on 2011-02-03
Yep, bjam mystifies me to be honest, but the first part, building boost using mingw32, of this howto seems to vaguely work...
[http://www.vle-project.org/wiki/Cross_compilation_Win32](http://www.vle-project.org/wiki/Cross_compilation_Win32)

---

