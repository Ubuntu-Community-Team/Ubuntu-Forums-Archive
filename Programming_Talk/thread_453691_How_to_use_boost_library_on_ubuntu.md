---
title: "How to use boost library on ubuntu"
date: 2007-05-24
forum: Programming Talk
---

### Post by yinglcs2 on 2007-05-24
Hi,

I think I have installed boost library on ubunut successfully:

$ sudo apt-get install libboost*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libboost-regex1.33.1 for regex 'libboost*'
Note, selecting libboost-thread-dev for regex 'libboost*'
Note, selecting libboost-graph-dev for regex 'libboost*'
Note, selecting libboost-date-time-dev for regex 'libboost*'
Note, selecting libboost-dbg for regex 'libboost*'
Note, selecting libboost-iostreams-dev for regex 'libboost*'
Note, selecting libboost-dev for regex 'libboost*'
Note, selecting libboost-doc for regex 'libboost*'
Note, selecting libboost-thread1.33.1 for regex 'libboost*'
Note, selecting libboost-filesystem-dev for regex 'libboost*'
Note, selecting libboost-date-time1.33.1 for regex 'libboost*'
Note, selecting libboost-test-dev for regex 'libboost*'
Note, selecting libboost-wave-dev for regex 'libboost*'
Note, selecting libboost-serialization-dev for regex 'libboost*'
Note, selecting libboost-signals-dev for regex 'libboost*'
Note, selecting libboost-signals1.33.1 for regex 'libboost*'
Note, selecting libboost-regex-dev for regex 'libboost*'
Note, selecting libboost-python-dev for regex 'libboost*'
Note, selecting libboost-filesystem1.33.1 for regex 'libboost*'
Note, selecting libboost-python1.33.1 for regex 'libboost*'
Note, selecting libboost-program-options-dev for regex 'libboost*'
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

But when I compile this simple program, i can't find 'thread.hpp', can you please tell me why?


#include <boost/thread/thread.hpp>
#include <iostream>

void hello()
{
  std::cout <<
    "Hello world, I'm a thread!"
    << std::endl;
}

int main(int argc, char* argv[])
{
  boost::thread thrd(&hello);
  thrd.join();
  return 0;
}

../main.cpp:13:35: warning: boost/thread/thread.hpp: No such file or directory
../main.cpp:28:2: warning: no newline at end of file

---

### Post by Bluetech on 2007-05-24
From this line:
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
It seems like you havn't actually installed the libraries. Have you?

---

### Post by yinglcs2 on 2007-05-25
No. I think I have. I have run the command twice. That is why it said no package is installed the second time.

---

### Post by WW on 2007-05-25
[This page]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libboost-thread-dev&version=feisty&arch=i386") shows the files installed by the package libboost-thread-dev (for feisty, i386).  The error message says you are missing /usr/include/boost/thread/thread.cpp.  Have you checked that you actually have the files?  What does this command show?
```

ls -l /usr/include/boost/thread*

```

---

### Post by yinglcs2 on 2007-05-25
There is /usr/include/boost, but there is not /usr/include/boost/thread

I tried "sudo apt-get install libboost-thread-dev", but it said no package is available.


$ sudo apt-get install libboost-thread-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libboost-thread-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libboost-thread-dev has no installation candidate

---

### Post by DoktorSeven on 2007-05-25
Works here, but the include should be
#include <boost/thread.hpp>

(Also, be sure to compile with the -lboost_thread parameter.)

---

### Post by yinglcs2 on 2007-05-25
But in /usr/include/boost, I don't have any file starts with 'thread'.

Can you please tell me how to install boost thread?

---

### Post by WW on 2007-05-26
You must first enable the Universe repository.  Here is a [description of how to do that]("https://help.ubuntu.com/community/Repositories/Ubuntu") in the wiki.

Then run
```

sudo apt-get install libboost-thread-dev

```

---

### Post by yinglcs2 on 2007-05-26
Thanks.  It said 'E: Package libboost-thread-dev has no installation candidate'

$ sudo apt-get install libboost-thread-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libboost-thread-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libboost-thread-dev has no installation candidate

---

### Post by WW on 2007-05-26
Sorry... I just edited my previous post.  You must first enable the Universe repository.

---

### Post by yinglcs2 on 2007-05-26
Thanks. But when I compile a simple program, I get this linker error.

i have add '-lboostthread' to my linker flag:

```
make all 
./main.o: In function `main':
/home/yinglcs/eclipseworkspace/test/Debug/../main.cpp:25: undefined reference to `boost::thread::thread(boost::function0<void, std::allocator<boost::function_base> > const&)'
/home/yinglcs/eclipseworkspace/test/Debug/../main.cpp:26: undefined reference to `boost::thread::join()'
/home/yinglcs/eclipseworkspace/test/Debug/../main.cpp:27: undefined reference to `boost::thread::~thread()'
/home/yinglcs/eclipseworkspace/test/Debug/../main.cpp:27: undefined reference to `boost::thread::~thread()'
collect2: ld returned 1 exit status
make: *** [test] Error 1
Building target: test
Invoking: GCC C++ Linker
g++  -o"test"  ./main.o 
```


my code:

```
#include <boost/thread/thread.hpp>
#include <iostream>

void hello()
{
  std::cout <<
    "Hello world, I'm a thread!"
    << std::endl;
}

int main(int argc, char* argv[])
{
  boost::thread thrd(&hello);
  thrd.join();
  return 0;
}
```

---

### Post by WW on 2007-05-26
The library option should be **-lboost_thread**, but I don't know if that explains the error that you got.  I saved your example in a file called **boostthreadtest.cpp**, and compiled and ran it as follows:
```

$ g++ boostthreadtest.cpp -o boostthreadtest -lboost_thread
$ ./boostthreadtest
Hello world, I'm a thread!
$

```

---

### Post by yinglcs2 on 2007-05-26
Thanks. But can you please tell me if I need to setup the LD_LIBRARY_PATH in my .bashrc?

Otherwise, how can I specify where is the boost_thread library for linking?

---

### Post by WW on 2007-05-26
The library object files are in /usr/lib.  g++ will search there automatically.  There is no need to set LD_LIBRARY_PATH.

---

