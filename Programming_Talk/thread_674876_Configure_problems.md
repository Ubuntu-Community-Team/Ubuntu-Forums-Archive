---
title: "Configure problems"
date: 2008-01-22
forum: Programming Talk
---

### Post by Saithn on 2008-01-22
I first posted this [here](http://ubuntuforums.org/showthread.php?p=4184159&posted=1#post4184159) in the beginner forum. But someone gave me the advice to post it here. So:


Hey,

I'm a new Ubuntu user trying to use some tools that need to be build. However, I have problems with the ./configure. I've already read quite some forums for this problem, but I'm still stuck.

I am using ubuntu 7.10

The message I get when trying to configure:

```
~/Study/ADK-0.4$ ./configure
loading cache ./config.cache
checking for c++... (cached) c++
  ) works... nor the C++ compiler (c++
configure: error: installation or configuration problem: C++ compiler cannot create executables.
delodic@Delodic:~/Study/ADK-0.4$ 
```

And the Log generated:

```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

configure:531: checking for c++
configure:563: checking whether the C++ compiler (c++
  ) works
configure:579: c++
 -o conftest    conftest.C  1>&5
eval: 1: c++
: not found
configure: failed program was:

#line 574 "configure"
#include "confdefs.h"

int main(){return(0);}
```.

I Assume that my c++ compiler isn't working correctly. Probably missing a package.

 Using google, I found [this]("http://www.linuxquestions.org/questions/linux-software-2/configure-error-installation-or-configuration-problem-c-compiler-cannot-create-e-294172/") topic with someone that has kind of the same problem I think. 

So the packages I have, for each I did a sudo apt-get install

> 
build-essential is already the newest version.
libc6 is already the newest version.
libstdc++6 is already the newest version.
g++ is already the newest version. **g++ set to manual installed.**


If I type

```
echo 'main(){}' >> test.cpp
``` And then ```
g++ -v test.cpp
```

I get:

> ~/Study/ADK-0.4$ g++ -v test.cpp
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
 /usr/lib/gcc/i486-linux-gnu/4.1.3/cc1plus -quiet -v -D_GNU_SOURCE test.cpp -quiet -dumpbase test.cpp -mtune=generic -auxbase test -version -fstack-protector -fstack-protector -o /tmp/cc2zaA20.s
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../i486-linux-gnu/include"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/include/c++/4.1.3
 /usr/include/c++/4.1.3/i486-linux-gnu
 /usr/include/c++/4.1.3/backward
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.1.3/include
 /usr/include
End of search list.
GNU C++ version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2) (i486-linux-gnu)
        compiled by GNU C version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2).
GGC heuristics: --param ggc-min-expand=98 --param ggc-min-heapsize=128256
Compiler executable checksum: 3cc47be363985179cfafdceddd0e8f5d
test.cpp: In function ‘int main()’:
test.cpp:2: error: redefinition of ‘int main()’
test.cpp:1: error: ‘int main()’ previously defined here


Here my results are a bit different than in the other topic. Anyway, there was suggested to do the following:

> 
I'm going to assume that you have the compiler that came with your system in /usr/bin ( if not, install it off of your install cd's). to make sure we pick that one up do this:

```

export CC=/usr/bin/gcc

```
and
```

export CXX=/usr/bin/g++
```

and try to reconfigure your program again.


When I execute these commands, nothing really happens. I assume there is some problem because I tried to build the g++ myself and later (perhaps?) used the upt-get to install the g++.

I hope this is enough information, and that someone can help me :)

---

### Post by Saithn on 2008-01-22
shameless bump for great justice. :guitar:

---

### Post by geraldm on 2008-01-22
echo 'main(){}' >> test.cpp
Use only ONE > # Is it possible that there were two lines in the file?
Create a link from /usr/bin/c++ to point to /usr/bin/g++
Try again.

Gerald

---

### Post by Saithn on 2008-01-22
Thanks for your help!

> **geraldm said:**
> echo 'main(){}' >> test.cpp
Use only ONE > 

Ok. I just did this as a test that might be helpful for you guys to help me. In the other topic the person said to do it with two >>, but perhaps because that guy had another implementation of linux running. Anyway :

```
delodic@Delodic:~$ echo 'main(){}' > test.cpp
delodic@Delodic:~$ g++ -v test.cpp
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
 /usr/lib/gcc/i486-linux-gnu/4.1.3/cc1plus -quiet -v -D_GNU_SOURCE test.cpp -quiet -dumpbase test.cpp -mtune=generic -auxbase test -version -fstack-protector -fstack-protector -o /tmp/ccfyEZJA.s
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../i486-linux-gnu/include"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/include/c++/4.1.3
 /usr/include/c++/4.1.3/i486-linux-gnu
 /usr/include/c++/4.1.3/backward
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.1.3/include
 /usr/include
End of search list.
GNU C++ version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2) (i486-linux-gnu)
        compiled by GNU C version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2).
GGC heuristics: --param ggc-min-expand=98 --param ggc-min-heapsize=128256
Compiler executable checksum: 3cc47be363985179cfafdceddd0e8f5d
 as --traditional-format -V -Qy -o /tmp/cccK00i5.o /tmp/ccfyEZJA.s
GNU assembler version 2.18 (i486-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.18
 /usr/lib/gcc/i486-linux-gnu/4.1.3/collect2 --eh-frame-hdr -m elf_i386 --hash-style=both -dynamic-linker /lib/ld-linux.so.2 /usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crt1.o /usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.1.3/crtbegin.o -L/usr/lib/gcc/i486-linux-gnu/4.1.3 -L/usr/lib/gcc/i486-linux-gnu/4.1.3 -L/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib /tmp/cccK00i5.o -lstdc++ -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc /usr/lib/gcc/i486-linux-gnu/4.1.3/crtend.o /usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crtn.o

```


> # Is it possible that there were two lines in the file?
Which file do you mean? The configure file is pretty big, it happens at around 570.

> 
Create a link from /usr/bin/c++ to point to /usr/bin/g++
Try again.
Gerald

There is a link from /usr/bin/c++ to /usr/bin/g++-4.1 so I think that's okay.


Btw, some code from the configure file which might be helpful

```
echo $ac_n "checking whether the C++ compiler ($CXX $CXXFLAGS $LDFLAGS) works""... $ac_c" 1>&6
echo "configure:563: checking whether the C++ compiler ($CXX $CXXFLAGS $LDFLAGS) works" >&5

ac_ext=C
# CXXFLAGS is not in ac_cpp because -g, -O, etc. are not valid cpp options.
ac_cpp='$CXXCPP $CPPFLAGS'
ac_compile='${CXX-g++} -c $CXXFLAGS $CPPFLAGS conftest.$ac_ext 1>&5'
ac_link='${CXX-g++} -o conftest${ac_exeext} $CXXFLAGS $CPPFLAGS $LDFLAGS conftest.$ac_ext $LIBS 1>&5'
cross_compiling=$ac_cv_prog_cxx_cross

cat > conftest.$ac_ext << EOF

#line 574 "configure"
#include "confdefs.h"

int main(){return(0);}
EOF
if { (eval echo configure:579: \"$ac_link\") 1>&5; (eval $ac_link) 2>&5; } && test -s conftest${ac_exeext}; then
  ac_cv_prog_cxx_works=yes
  # If we can't run a trivial program, we are probably using a cross compiler.
  if (./conftest; exit) 2>/dev/null; then
    ac_cv_prog_cxx_cross=no
  else
    ac_cv_prog_cxx_cross=yes
  fi
else
```

---

### Post by geraldm on 2008-01-22
echo 'main(){}' >> test.cpp
Use only ONE > # Is it possible that there were two lines in the file?

Which file do you mean? The configure file is pretty big, it happens at around 570.

I meant file test.cpp.  From the error messages below, the error points to having 2 lines in that file.  This could have been caused by using two ">>" and running the command twice, which gives two lines.
By using only ONE ">" you get a file with only one line, even if the command is executed two times.

test.cpp: In function ‘int main()’:
test.cpp:2: error: redefinition of ‘int main()’
test.cpp:1: error: ‘int main()’ previously defined here

Gerald

---

