---
title: "why gcc isnt compiling?"
date: 2008-01-26
forum: Packaging and Compiling Programs
---

### Post by edan on 2008-01-26
hi all 
i wrote a simple Hello wrold c++ program 
but c++ does'nt compile it, i allready upgraded my gcc and installed build-essential.

this is the code:
```

#include <iostream>
using namespace std;
int main()
{
  cout << "Hello World!" << endl;   
return 0;
}

``` 

and this is the error the gcc prints:
```

/tmp/ccoCgNsO.o: In function `__static_initialization_and_destruction_0(int, int)':
helloc++.cc:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccoCgNsO.o: In function `__tcf_0':
helloc++.cc:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccoCgNsO.o: In function `main':
helloc++.cc:(.text+0x8e): undefined reference to `std::cout'
helloc++.cc:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
helloc++.cc:(.text+0x9b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
helloc++.cc:(.text+0xa3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
helloc++.cc:(.text+0xb2): undefined reference to `std::cout'
helloc++.cc:(.text+0xb7): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
helloc++.cc:(.text+0xbf): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
helloc++.cc:(.text+0xc7): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccoCgNsO.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


```

thnx

---

### Post by sisco311 on 2008-01-26
compile it with g++:
```
g++ -o output file.cpp
```

---

### Post by cpw on 2008-01-30
I'm new at this business, so bear with me.
Kernel is 2.6.22-14-generic SMP i686
gcc is 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

problem seems related to cc1plus.

test program is: 'main() {}'

failure is: 
  g++: Internal error: Segmentation fault (program cc1plus)

Here is a script i ran:

#!/bin/sh

echo "*** testing g++ using one line program: 'main() {}'"
echo "main() {}" > test.cpp
g++ -save-temps -v test.cpp 
if test $? -gt 0; then
  echo "*** g++ -save-temps -v of `cat test.cpp`" failed!
else
  echo "*** compilation of `cat test.cpp`" succeeded.
fi
if test -f test.ii; then
  echo "*** -save-temps generated test.ii, contents are:"
  cat test.ii
  echo "*** end of test.ii contents"
else
  echo "*** -save-temps did NOT generate test.ii!"
fi
if test -f a.out; then
  ./a.out
  if test $? -gt 0; then
    echo "*** run of program (a.out) "'`cat test.cpp`' failed!
  else
    echo "*** run of program (a.out) "'`cat test.cpp`' succeeded.
  fi
else
  echo "*** no a.out generated!"
fi
echo "uname: `uname -a`"
echo -n "/etc/issue: "
set `cat /etc/issue`
echo $1 $2

# end of the test

Here is result of the test:

*** testing g++ using one line program: 'main() {}'
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
 /usr/lib/gcc/i486-linux-gnu/4.1.3/cc1plus -E -quiet -v -D_GNU_SOURCE test.cpp -mtune=generic -fpch-preprocess -o test.ii
g++: Internal error: Segmentation fault (program cc1plus)
Please submit a full bug report.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.

*** g++ -save-temps -v of main() {} failed!
*** -save-temps did NOT generate test.ii!
*** no a.out generated!
uname: Linux cynosure 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
/etc/issue: Ubuntu 7.10

# end of the script

The question is: where do I find a fix for cc1plus?  The script runs
fine on ubuntu 6.10.

I solved this problem by: running dpkg -S cc1plus, to find out the package to reinstall:
  g++-4.1: /usr/lib/gcc/i486-linux-gnu/4.1/cc1plus
Then I simply reinstalled the package: apt-get --reinstall g++4.1

Sorry for the bother.  But, it was a good learning experience.

---

### Post by reef_d on 2008-01-31
I too have a similar problem. I installed Ubuntu Feisty Fawn on my laptop. When i wrote my program in Anjuta and tried compiling i get the following message:

error:stdio.h: No such file or directory. What do i have to install to use the libraries?

---

### Post by Compyx on 2008-01-31
I wish people would use the search functions of these forums:

```
sudo apt-get install build-essential
```

---

### Post by dicecca112 on 2008-01-31
re-read the OP post, he said he already installed build-essentials

---

### Post by Compyx on 2008-02-02
I wasn't replying to the OP, I was replying to reef_d.

---

### Post by coyotech on 2008-02-02
I have the same problem. gcc,tcc,geany,anjuto, none of them can find the headers. I've installed build-essential, the latest linux headers, reinstalled gcc and all that. It isn't working. Lots of people are having the same problem, and they always stop at the same place: install build-essential...it doesn't work, and there are no more answers. After installing build-essential, is there something else you should do? Is there some command line trick that will make it work?

You might find a solution and put it in your sticky posts. I've searched till I'm sick of it. Maybe this latest Ubuntu has a problem with the c compiler or something?

---

### Post by edan on 2008-02-04
thanks for all the help everyone

i solved the problem
(i actually have no clue what was the problem or what i did that it started working).
i just reinstalled some packages and used g++ instead of gcc....

---

### Post by Trevor_Jones on 2008-05-13
Hi I have a similar problem but I can't use:
"[COLOR=Cyan]sudo apt-get install build-essential[/COLOR]" because I have not got my new m/c, with Hardy on-line yes.  I am down-loading with my old laptop and kermiting any files across to the new machine and using the Gdebi package installer to install them.
So I down-loaded "[COLOR=MediumTurquoise]build_essential _11.3ubuntu1.i386.deb[/COLOR]"
the installer reports:
[COLOR=Red]Error : Dependency is not satisfied: libc6-dev/libc-dev[/COLOR]
So I down-loaded "[COLOR=Cyan]libc6-dev_2.3.6.dsl-13etch5-i386.deb[/COLOR]"
GDebi reported:
[COLOR=Red]Error : Dependency not satisfied : libc6[/COLOR]
BUT it is loaded both libgcc and libc6 are straight from the distro
All I want to do is compile the slamr sl module for my modem and then I can use:
sudo apt-get install <whatever> to my heart's content.
What am I doing wrong?

---

