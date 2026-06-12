---
title: "Migration to gcc 4.1.2, problem with object file being empty"
date: 2007-09-05
forum: Programming Talk
---

### Post by buddi on 2007-09-05
I am trying to migrate to a newer version of the gcc and see that a simple Semaphore code is producing .o with no contents. I don't get any errors or warnings but the compiler silently builds the .o without any thing in it. Anybody had this problem earlier. NEED HELP !!

---

### Post by gnusci on 2007-09-05
The compiler is no ready for creating binaries, use:

**$ sudo apt-get install build-essential** (compiling tools)
**$ sudo apt-get install freeglut3-dev**   (open gl)
**$ sudo apt-get build-dep xorg-dev**    (x11 for developing)

---

### Post by buddi on 2007-09-05
I am able to build 95 % of the code and also tried this version of gcc with another application which got built and tested properly. The is with this specific file:

#include "Semaphore.h"
#include <string>

using namespace std;

template class Semaphore<int>;

template <class T> Semaphore<T>::Semaphore() {
  count = 0;

  int pthread_status;
  if( ( pthread_status = pthread_mutex_init( &mutex, NULL ) ) != 0 ) {
    string err = "Couldn't create mutex!\n";
    throw err;
  }

  if( ( pthread_status = pthread_cond_init( &cond, NULL ) ) != 0 ) {
    string err = "Couldn't create condition variable!\n";
    throw err;
  }
}

template <class T> T Semaphore<T>::operator++() {
  int pthread_status;
  if( ( pthread_status = pthread_mutex_lock( &mutex ) ) != 0 ) {
    string err = "Couldn't lock mutex!\n";
    throw err;
  }

  T result = count++;

  if( ( pthread_status = pthread_mutex_unlock( &mutex ) ) != 0 ) {
    string err = "Couldn't unlock mutex!\n";
    throw err;
  }

  return result;
}

template <class T> T Semaphore<T>::operator++( int ) {
  int pthread_status;
  if( ( pthread_status = pthread_mutex_lock( &mutex ) ) != 0 ) {
    string err = "Couldn't lock mutex!\n";
    throw err;
  }

  T result = ++count;

  if( ( pthread_status = pthread_mutex_unlock( &mutex ) ) != 0 ) {
    string err = "Couldn't unlock mutex!\n";
    throw err;
  }

  return result;
}

template <class T> T Semaphore<T>::operator--() {
  int pthread_status;
  if( ( pthread_status = pthread_mutex_lock( &mutex ) ) != 0 ) {
    string err = "Couldn't lock mutex!\n";
    throw err;
  }

  T result = count--;

  if( count == 0 ) {
    if( ( pthread_status = pthread_cond_signal( &cond ) ) != 0 ) {
      string err = "Couldn't signal condition!\n";
      throw err;
    }
  }

  if( ( pthread_status = pthread_mutex_unlock( &mutex ) ) != 0 ) {
    string err = "Couldn't unlock mutex!\n";
    throw err;
  }

  return result;
}

template <class T> T Semaphore<T>::operator--( int ) {
  int pthread_status;
  if( ( pthread_status = pthread_mutex_lock( &mutex ) ) != 0 ) {
    string err = "Couldn't lock mutex!\n";
    throw err;
  }

  T result = --count;

  if( count == 0 ) {
    if( ( pthread_status = pthread_cond_signal( &cond ) ) != 0 ) {
      string err = "Couldn't signal condition!\n";
      throw err;
    }
  }

  if( ( pthread_status = pthread_mutex_unlock( &mutex ) ) != 0 ) {
    string err = "Couldn't unlock mutex!\n";
    throw err;
  }

  return result;
}

template <class T> void Semaphore<T>::wait() {
  int pthread_status;

  // check first to avoid racing here
  if( ( pthread_status = pthread_mutex_lock( &mutex ) ) != 0 ) {
    string err = "Couldn't lock mutex!\n";
    throw err;
  }

  bool done = ( count == 0 );

  if( ( pthread_status = pthread_mutex_unlock( &mutex ) ) != 0 ) {
    string err = "Couldn't unlock mutex!\n";
    throw err;
  }

  while( !done ) {
    if( ( pthread_status = pthread_mutex_lock( &mutex ) ) != 0 ) {
      string err = "Couldn't lock mutex!\n";
      throw err;
    }

    if( ( pthread_status = pthread_cond_wait( &cond, &mutex ) ) != 0 ) {
      string err = "Couldn't wait on condition!\n";
      throw err;
    }
    done = ( count == 0 );

    if( ( pthread_status = pthread_mutex_unlock( &mutex ) ) != 0 ) {
      string err = "Couldn't unlock mutex!\n";
      throw err;
    }
  }
}

template <class T> Semaphore<T>::~Semaphore() {
}

---

### Post by gnusci on 2007-09-05
Sorry,

But it is impossible for me to find an error just looking to the code, you should provide something we can compile to check with our compilers...!

---

### Post by buddi on 2007-09-05
Ok. I am attaching xyz.cpp and xyz.h in the tar file which I compiled using 3.4.2 and it creates a .o properly but does not when using 4.1.2.

here is the option I used:

/sbcimp/run/pd/gcc/32-bit/4.1.2/bin/g++ -g -c -o xyz.o xyz.cpp

I did an nm on the xyz.o and it did not produce any output

but when I created a xyz.o with 

/sbcimp/run/pd/gcc/3.4.2-32bit/bin/g++ -g -c -o xyz.o xyz.cpp

nm on  xyz.o:
         U _Unwind_Resume
00000000 W _ZN9SemaphoreIiEC1Ev
00000000 W _ZN9SemaphoreIiEC2Ev
00000000 W _ZN9SemaphoreIiED1Ev
00000000 W _ZN9SemaphoreIiED2Ev
00000000 W _ZN9SemaphoreIiEppEv
         U _ZNSaIcEC1Ev
         U _ZNSaIcED1Ev
         U _ZNSsC1EPKcRKSaIcE
         U _ZNSsC1ERKSs
         U _ZNSsD1Ev
00000000 V _ZTISs
00000000 V _ZTSSs
         U _ZTVN10__cxxabiv117__class_type_infoE
         U __cxa_allocate_exception
         U __cxa_throw
         U __gxx_personality_v0
         U pthread_cond_init
         U pthread_mutex_init
         w pthread_mutex_lock
         w pthread_mutex_unlock

Thanks for your help

---

### Post by dwhitney67 on 2007-09-05
Here's the version of GCC I have installed on my system, which I determined by running:

[FONT="Courier New"]$ g++ --version[/FONT]

gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


I untarred your tar-ball, renamed the files to Semaphore.cpp and Semaphore.h, and attempted to compile with this command:

[FONT="Courier New"]$ g++ -c Semaphore.cpp[/FONT]

Everything compiled fine.  It did not link of course because your code lacks a main().

If you cannot compile, then I suggest you check the forum(s) to find a way to uninstall your GCC and then re-attempt a re-install.


P.S.  Nice code btw; very easy to read.  Have you considered using the boost libraries for your pthread needs?

---

### Post by buddi on 2007-09-06
Just curious was it on Linux OS where you could compile this ?

the os/system  where I am trying this is :
uname -a
Linux xstm0166dap 2.4.21-37.ELsmp #1 SMP Wed Sep 7 13:28:55 EDT 2005 i686 athlon i386 GNU/Linux

I know boost libraries are the best to use. This is a app which have received from another group and they have been using real low level calls. Our application is fully based on boost.

BTW thanks for trying that for me.

---

### Post by dwhitney67 on 2007-09-06
It appears you have an old kernel... shouldn't matter though.  It's what GCC does for you that matters.

Here are the results I obtained from running 'uname -a':

Linux korat 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

Btw, I have three systems available (with the same architecture)... one running Ubuntu 7.04, the other Fedora Core 5, the other Fedora Core 7.

The responses I have posted on this thread all came from my Ubuntu system.

---

### Post by buddi on 2007-09-06
Mine compiles too without any issue, just that the .o (object files) don't have any symbols. If you don't mind can you please try 

nm <object file built against 4.1.2>

and let me know if you see any output

---

### Post by dwhitney67 on 2007-09-06
> **buddi said:**
> Mine compiles too without any issue, just that the .o (object files) don't have any symbols. If you don't mind can you please try 

nm <object file built against 4.1.2>

and let me know if you see any output

What do you mean, debug symbols??  If you want those, then compile with:

[FONT="Courier New"]$ g++ -g -c file.cpp[/FONT]

The -g option provides the symbol table.

Btw, here is the output from running [FONT="Courier New"]nm -a Semaphore.o[/FONT]:

```
> nm -a Semaphore.o
00000000 b .bss
00000000 n .comment
00000000 d .data
00000000 N .debug_abbrev
00000000 N .debug_info
00000000 N .debug_line
00000000 N .debug_str
00000000 n .note.GNU-stack
00000000 t .text
00000000 a Semaphore.cpp
```

---

### Post by buddi on 2007-09-07
Apologize for not being very clear. Here is what I meant. I compiled twice with debug option, once with 4.1.2 and once with 3.4.2 compiler and here is the simple output of nm from both of them:

4.1.2:

nm -a Semaphore.o
00000000 b .bss
00000000 n .comment
00000000 d .data
00000000 N .debug_abbrev
00000000 N .debug_info
00000000 N .debug_line
00000000 N .debug_str
00000000 n .note.GNU-stack
00000000 t .text
00000000 a Semaphore.cpp


3.4.2: 

nm -a Semaphore.o.3.4.2 
00000000 b .bss
00000000 n .comment
00000000 d .data
00000000 N .debug_abbrev
00000000 N .debug_aranges
00000000 N .debug_frame
00000000 N .debug_info
00000000 N .debug_line
00000000 N .debug_pubnames
00000000 N .debug_str
00000000 r .eh_frame
00000000 r .gcc_except_table
00000000 d .gnu.linkonce.d.DW.ref.__gxx_personality_v0
00000000 d .gnu.linkonce.d._ZTISs
00000000 r .gnu.linkonce.r._ZTSSs
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiE4waitEv
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEC1Ev
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEC2Ev
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiED1Ev
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiED2Ev
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEmmEi
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEmmEv
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEppEi
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEppEv
00000000 t .gnu.linkonce.t.__i686.get_pc_thunk.bx
00000000 n .note.GNU-stack
00000000 r .rodata
00000000 t .text
00000000 V DW.ref.__gxx_personality_v0
00000000 a Semaphore.cpp
         U _GLOBAL_OFFSET_TABLE_
         U _Unwind_Resume
00000000 W _ZN9SemaphoreIiE4waitEv
00000000 W _ZN9SemaphoreIiEC1Ev
00000000 W _ZN9SemaphoreIiEC2Ev
00000000 W _ZN9SemaphoreIiED1Ev
00000000 W _ZN9SemaphoreIiED2Ev
00000000 W _ZN9SemaphoreIiEmmEi
00000000 W _ZN9SemaphoreIiEmmEv
00000000 W _ZN9SemaphoreIiEppEi
00000000 W _ZN9SemaphoreIiEppEv
         U _ZNSaIcEC1Ev
         U _ZNSaIcED1Ev
         U _ZNSsC1EPKcRKSaIcE
         U _ZNSsC1ERKSs
         U _ZNSsD1Ev
00000000 V _ZTISs
00000000 V _ZTSSs
         U _ZTVN10__cxxabiv117__class_type_infoE
         U __cxa_allocate_exception
         U __cxa_throw
         U __gxx_personality_v0
00000000 T __i686.get_pc_thunk.bx
         U pthread_cond_init
         U pthread_cond_signal
         U pthread_cond_wait
         U pthread_mutex_init
         w pthread_mutex_lock
         w pthread_mutex_unlock


What I was trying to convey was that when we compile with debug option on 4.1.2 we see only debug symbols and nothing more, like the symbols for the function defination etc. That is the exact problem I am having, when I create a .so out of 4.1.2 compiled .o and link with an application I get all kinds of undefined references.

---

### Post by gnusci on 2007-09-07
I also did compile it without any inconvenience... I did not see any problem!

Here some outputs:

```
g++ (GCC) 3.3.5 20050117 (prerelease)
```

```
$ uname -a
Linux 2.6.11.4-20a-smp #1 SMP Wed Mar 23 21:52:37 UTC 2005 x86_64 x86_64 x86_64 GNU/Linux
```


```
nm Semaphore.o
                 U __cxa_allocate_exception
                 U __cxa_throw
                 U __gxx_personality_v0
                 U pthread_cond_init
                 U pthread_mutex_init
                 w pthread_mutex_lock
                 w pthread_mutex_unlock
                 U _Unwind_Resume
0000000000000000 W _ZN9SemaphoreIiEC1Ev
0000000000000000 W _ZN9SemaphoreIiEC2Ev
0000000000000000 W _ZN9SemaphoreIiED1Ev
0000000000000000 W _ZN9SemaphoreIiED2Ev
0000000000000000 W _ZN9SemaphoreIiEppEv
                 U _ZNSaIcEC1Ev
                 U _ZNSaIcED1Ev
                 U _ZNSsC1EPKcRKSaIcE
                 U _ZNSsC1ERKSs
                 U _ZNSsD1Ev
0000000000000000 V _ZTISs
0000000000000000 V _ZTSSs
                 U _ZTVN10__cxxabiv117__class_type_infoE
```

Maybe you should check your system...

---

### Post by dwhitney67 on 2007-09-07
> **buddi said:**
> Apologize for not being very clear. Here is what I meant. I compiled twice with debug option, once with 4.1.2 and once with 3.4.2 compiler and here is the simple output of nm from both of them:

4.1.2:

nm -a Semaphore.o
00000000 b .bss
00000000 n .comment
00000000 d .data
00000000 N .debug_abbrev
00000000 N .debug_info
00000000 N .debug_line
00000000 N .debug_str
00000000 n .note.GNU-stack
00000000 t .text
00000000 a Semaphore.cpp


3.4.2: 

nm -a Semaphore.o.3.4.2 
00000000 b .bss
00000000 n .comment
00000000 d .data
00000000 N .debug_abbrev
00000000 N .debug_aranges
00000000 N .debug_frame
00000000 N .debug_info
00000000 N .debug_line
00000000 N .debug_pubnames
00000000 N .debug_str
00000000 r .eh_frame
00000000 r .gcc_except_table
00000000 d .gnu.linkonce.d.DW.ref.__gxx_personality_v0
00000000 d .gnu.linkonce.d._ZTISs
00000000 r .gnu.linkonce.r._ZTSSs
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiE4waitEv
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEC1Ev
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEC2Ev
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiED1Ev
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiED2Ev
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEmmEi
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEmmEv
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEppEi
00000000 t .gnu.linkonce.t._ZN9SemaphoreIiEppEv
00000000 t .gnu.linkonce.t.__i686.get_pc_thunk.bx
00000000 n .note.GNU-stack
00000000 r .rodata
00000000 t .text
00000000 V DW.ref.__gxx_personality_v0
00000000 a Semaphore.cpp
         U _GLOBAL_OFFSET_TABLE_
         U _Unwind_Resume
00000000 W _ZN9SemaphoreIiE4waitEv
00000000 W _ZN9SemaphoreIiEC1Ev
00000000 W _ZN9SemaphoreIiEC2Ev
00000000 W _ZN9SemaphoreIiED1Ev
00000000 W _ZN9SemaphoreIiED2Ev
00000000 W _ZN9SemaphoreIiEmmEi
00000000 W _ZN9SemaphoreIiEmmEv
00000000 W _ZN9SemaphoreIiEppEi
00000000 W _ZN9SemaphoreIiEppEv
         U _ZNSaIcEC1Ev
         U _ZNSaIcED1Ev
         U _ZNSsC1EPKcRKSaIcE
         U _ZNSsC1ERKSs
         U _ZNSsD1Ev
00000000 V _ZTISs
00000000 V _ZTSSs
         U _ZTVN10__cxxabiv117__class_type_infoE
         U __cxa_allocate_exception
         U __cxa_throw
         U __gxx_personality_v0
00000000 T __i686.get_pc_thunk.bx
         U pthread_cond_init
         U pthread_cond_signal
         U pthread_cond_wait
         U pthread_mutex_init
         w pthread_mutex_lock
         w pthread_mutex_unlock


What I was trying to convey was that when we compile with debug option on 4.1.2 we see only debug symbols and nothing more, like the symbols for the function defination etc. That is the exact problem I am having, when I create a .so out of 4.1.2 compiled .o and link with an application I get all kinds of undefined references.

The fact that you are getting undefined references could be due to any number of problems, but the most likely is that you are not specifying the path to the shared library (using a -L option) when you are linking your application.  That's just one possibility.  Perhaps you are building the library incorrectly?

Here's a link to a [HOWTO]("http://www.dwheeler.com/program-library/Program-Library-HOWTO/x36.html") on how to build shared libraries.

The document is using 'gcc' in its examples; I believe in your case you want to use 'g++' because you are dealing with C++.

Do you have a Makefile (or other build script) that you can post?

---

