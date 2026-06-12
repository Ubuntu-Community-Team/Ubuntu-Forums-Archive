---
title: "problem with the compilation  (fatal error: iostream: No such file or directory)"
date: 2013-12-26
forum: Packaging and Compiling Programs
---

### Post by cdb10 on 2013-12-26
Hello!
I am very sorry I only speak a little English. 
I have a problem with the compilation.
This is a simple examples:
```

lap1@laptop:~/stlpr$ cat c.cpp
#include<iostream>


int main()
{
        cout<<"hello!"<<endl;
}




lap1@laptop:~/stlpr$ g++ c.cpp
c.cpp:1:19: fatal error: iostream: No such file or directory
compilation terminated.
lap1@laptop:~/stlpr$ 

```
```

lap1@laptop:~/stlpr$ cat a.cpp
#include <vector>
#include <iterator>
#include <iostream>


int main()
{
   std::vector<int> vec;   // declare a vector of int


   vec.push_back(10);      // add some values
   vec.push_back(20);
   vec.push_back(30);


   std::copy(vec.begin(), vec.end(), std::ostream_iterator<int>(std::cout, " "));
   std::cout << std::endl;
}
lap1@laptop:~/stlpr$ 
lap1@laptop:~/stlpr$ g++ a.cpp
a.cpp:1:18: fatal error: vector: No such file or directory
compilation terminated.
lap1@laptop:~/stlpr$ 




```

My system is
```

lap1@laptop:~/stlpr$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise
lap1@laptop:~/stlpr$ 

```
I have installed:
```

lap1@laptop:~/stlpr$ dpkg --get-selections | grep build-essential
build-essential                                 install
lap1@laptop:~/stlpr$ dpkg --get-selections | grep libstdc++
libstdc++6                                      install
libstdc++6-4.4-dev                              install
libstdc++6-4.6-dev                              install
lap1@laptop:~/stlpr$ 

```

---

### Post by steeldriver on 2013-12-26
Hello and welcome to the forums

You have 2 versions of libstdc++6 dev (libstdc++6-**4.4**-dev and libstdc++6-**4.6**-dev) - is one of them consistent with the current version of g++ ? what is the result of

```
g++ --version
```

---

### Post by cdb10 on 2013-12-27
```

lap1@laptop:~$ g++ --version
g++ (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


lap1@laptop:~$ 



```

---

### Post by kajoky on 2013-12-27
One thing is in the #includes, they are missing the .h
they should be #include<iostream.h>
that is why you get the error "no such file or directory"

---

### Post by steeldriver on 2013-12-27
^^^ sorry that's just incorrect - the use of the .h forms in C++ is deprecated, see 

[http://stackoverflow.com/a/214242](http://stackoverflow.com/a/214242)
[http://stackoverflow.com/a/2976483](http://stackoverflow.com/a/2976483)
[http://members.gamedev.net/sicrane/articles/iostream.html](http://members.gamedev.net/sicrane/articles/iostream.html)

The iostream file is provided by the corresponding libstdc++6 package e.g.

```

$ apt-file search -x '/usr/include/c\+\+/[0-9]\.[0-9]/iostream$'
libstdc++6-4.4-dev: /usr/include/c++/4.4/iostream
libstdc++6-4.5-dev: /usr/include/c++/4.5/iostream
libstdc++6-4.6-dev: /usr/include/c++/4.6/iostream

```

The only thing wrong I see with the OP's code is not providing a namespace *using* directive - but AFAIK that won't cause the 'file not found' error, it will just produce errors like "&#8216;cout&#8217; was not declared in this scope" and so on

---

### Post by kajoky on 2013-12-27
Very sorry.

---

### Post by cdb10 on 2013-12-29
```

lap1@laptop:~/stlpr$ apt-file search -x '/usr/include/c\+\+/[0-9]\.[0-9]/iostream$'
libstdc++6-4.4-dev: /usr/include/c++/4.4/iostream
libstdc++6-4.5-dev: /usr/include/c++/4.5/iostream
libstdc++6-4.6-dev: /usr/include/c++/4.6/iostream
lap1@laptop:~/stlpr$ 
lap1@laptop:~/stlpr$ cat c.cpp
#include<iostream>
using namespace std;
int main()
{
    cout<<"hey"<<endl;
}




lap1@laptop:~/stlpr$ g++ c.cpp -o c
c.cpp:1:19: fatal error: iostream: No such file or directory
compilation terminated.
lap1@laptop:~/stlpr$ 


```
I do not understand this contradiction:
```

lap1@laptop:~/stlpr$ dpkg -l |grep libstdc++
ri  libstdc++6                             4.6.3-1ubuntu5                               GNU Standard C++ Library v3
ri  libstdc++6-4.6-dev                     4.6.3-1ubuntu5                               GNU Standard C++ Library v3 (development files)
lap1@laptop:~/stlpr$  dpkg --get-selections | grep libstdc++
libstdc++6					deinstall
libstdc++6-4.6-dev				deinstall
lap1@laptop:~/stlpr$ 

```

---

### Post by steeldriver on 2013-12-29
It looks like the packages are marked for removal, maybe that is related to your compilation issues (perhaps other related stuff *has* been removed)? I don't know. You can check where g++ is searching for include files using

```
g++ -E -x c++ - -v < /dev/null
```

You should see something like

```

Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.4-1ubuntu1~12.04' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.6.4 (Ubuntu/Linaro 4.6.4-1ubuntu1~12.04) 
COLLECT_GCC_OPTIONS='-E' '-v' '-shared-libgcc' '-mtune=generic' '-march=i686'
 /usr/lib/gcc/i686-linux-gnu/4.6/cc1plus -E -quiet -v -imultilib . -imultiarch i386-linux-gnu -D_GNU_SOURCE - -mtune=generic -march=i686 -fstack-protector
ignoring nonexistent directory "/usr/local/include/i386-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i686-linux-gnu/4.6/../../../../i686-linux-gnu/include"
#include "..." search starts here:
[B]#include <...> search starts here:
 /usr/include/c++/4.6
 /usr/include/c++/4.6/i686-linux-gnu/.
 /usr/include/c++/4.6/backward
 /usr/lib/gcc/i686-linux-gnu/4.6/include
 /usr/local/include
 /usr/lib/gcc/i686-linux-gnu/4.6/include-fixed
 /usr/include/i386-linux-gnu
 /usr/include
End of search list.
[/B]# 1 "<stdin>"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "<stdin>"
COMPILER_PATH=/usr/lib/gcc/i686-linux-gnu/4.6/:/usr/lib/gcc/i686-linux-gnu/4.6/:/usr/lib/gcc/i686-linux-gnu/:/usr/lib/gcc/i686-linux-gnu/4.6/:/usr/lib/gcc/i686-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/i686-linux-gnu/4.6/:/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/:/usr/lib/gcc/i686-linux-gnu/4.6/../../../../lib/:/lib/i386-linux-gnu/:/lib/../lib/:/usr/lib/i386-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/i686-linux-gnu/4.6/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-E' '-v' '-shared-libgcc' '-mtune=generic' '-march=i686'

```

Maybe that will give us some ideas (possibly g++ and/or libstdc++6-4.x-dev need to be reinstalled?)

---

