---
title: "g++ finds error in locale_facets.h"
date: 2011-11-01
forum: Programming Talk
---

### Post by Wolf-Ekkehard on 2011-11-01
I thought I should be able to figure that out by myself, but I am beginning to pull my hair out over this...

I have Kubuntu 11.10 running on two 32-bit x86 machines.  On one (a laptop) g++ (4.6.1) works fine.  The other one I just converted recently from a dumped Windows box and put 11.10 on it.  The latter one won't let me compile.  I reduced the problem to the simplest form, i.e. the effects of the include tree of /usr/include/c++/4.6/ios:

```
#include <ios>

int main( int argc, char** argv )
{
    ;
}
```

When I compile on the faulty machine, I get the following output (on the laptop it compiles silently without error and exits):

```
g++ main.cpp
In file included from /usr/include/c++/4.6/bits/basic_ios.h:39:0,
                 from /usr/include/c++/4.6/ios:45,
                 from main.cpp:1:
/usr/include/c++/4.6/bits/locale_facets.h:2530:44: error: macro "isspace" passed 2 arguments, but takes just 1
/usr/include/c++/4.6/bits/locale_facets.h:2536:44: error: macro "isprint" passed 2 arguments, but takes just 1
/usr/include/c++/4.6/bits/locale_facets.h:2542:44: error: macro "iscntrl" passed 2 arguments, but takes just 1
/usr/include/c++/4.6/bits/locale_facets.h:2548:44: error: macro "isupper" passed 2 arguments, but takes just 1
/usr/include/c++/4.6/bits/locale_facets.h:2554:44: error: macro "islower" passed 2 arguments, but takes just 1
/usr/include/c++/4.6/bits/locale_facets.h:2560:44: error: macro "isalpha" passed 2 arguments, but takes just 1
/usr/include/c++/4.6/bits/locale_facets.h:2566:44: error: macro "isdigit" passed 2 arguments, but takes just 1
/usr/include/c++/4.6/bits/locale_facets.h:2572:44: error: macro "ispunct" passed 2 arguments, but takes just 1
/usr/include/c++/4.6/bits/locale_facets.h:2578:45: error: macro "isxdigit" passed 2 arguments, but takes just 1
/usr/include/c++/4.6/bits/locale_facets.h:2584:44: error: macro "isalnum" passed 2 arguments, but takes just 1
/usr/include/c++/4.6/bits/locale_facets.h:2590:44: error: macro "isgraph" passed 2 arguments, but takes just 1
In file included from /usr/include/c++/4.6/cwchar:46:0,
                 from /usr/include/c++/4.6/bits/postypes.h:42,
                 from /usr/include/c++/4.6/iosfwd:42,
                 from /usr/include/c++/4.6/ios:39,
                 from main.cpp:1:
/usr/include/wchar.h:578:8: error: ‘__FILE’ does not name a type
/usr/include/wchar.h:585:19: error: ‘__FILE’ was not declared in this scope
/usr/include/wchar.h:585:27: error: ‘__fp’ was not declared in this scope
/usr/include/wchar.h:585:33: error: expected primary-expression before ‘int’
/usr/include/wchar.h:585:43: error: expression list treated as compound expression in initializer [-fpermissive]
/usr/include/wchar.h:585:45: error: expected ‘,’ or ‘;’ before ‘throw’
/usr/include/wchar.h:592:22: error: ‘__FILE’ was not declared in this scope
/usr/include/wchar.h:592:30: error: expected primary-expression before ‘__restrict’
/usr/include/wchar.h:593:8: error: expected primary-expression before ‘__const’
/usr/include/wchar.h:593:46: error: expected primary-expression before ‘...’ token
/usr/include/wchar.h:593:49: error: expression list treated as compound expression in initializer [-fpermissive]
/usr/include/wchar.h:610:23: error: ‘__FILE’ was not declared in this scope
/usr/include/wchar.h:610:31: error: expected primary-expression before ‘__restrict’
/usr/include/wchar.h:611:9: error: expected primary-expression before ‘__const’
/usr/include/wchar.h:612:24: error: expected primary-expression before ‘__arg’
/usr/include/wchar.h:612:29: error: expression list treated as compound expression in initializer [-fpermissive]
/usr/include/wchar.h:633:21: error: ‘__FILE’ was not declared in this scope
/usr/include/wchar.h:633:29: error: expected primary-expression before ‘__restrict’
/usr/include/wchar.h:634:7: error: expected primary-expression before ‘__const’
/usr/include/wchar.h:634:45: error: expected primary-expression before ‘...’ token
/usr/include/wchar.h:634:48: error: expression list treated as compound expression in initializer [-fpermissive]
/usr/include/wchar.h:687:22: error: ‘__FILE’ was not declared in this scope
/usr/include/wchar.h:687:30: error: expected primary-expression before ‘__restrict’
/usr/include/wchar.h:688:8: error: expected primary-expression before ‘__const’
/usr/include/wchar.h:689:23: error: expected primary-expression before ‘__arg’
/usr/include/wchar.h:689:28: error: expression list treated as compound expression in initializer [-fpermissive]
/usr/include/wchar.h:743:23: error: ‘__FILE’ was not declared in this scope
/usr/include/wchar.h:743:31: error: ‘__stream’ was not declared in this scope
/usr/include/wchar.h:744:22: error: ‘__FILE’ was not declared in this scope
/usr/include/wchar.h:744:30: error: ‘__stream’ was not declared in this scope
/usr/include/wchar.h:757:37: error: ‘__FILE’ has not been declared
/usr/include/wchar.h:758:36: error: ‘__FILE’ has not been declared
/usr/include/wchar.h:773:4: error: ‘__FILE’ has not been declared
/usr/include/wchar.h:780:6: error: ‘__FILE’ has not been declared
/usr/include/wchar.h:787:37: error: ‘__FILE’ has not been declared
/usr/include/wchar.h:799:31: error: ‘__FILE’ was not declared in this scope
/usr/include/wchar.h:799:39: error: ‘__stream’ was not declared in this scope
/usr/include/wchar.h:808:32: error: ‘__FILE’ was not declared in this scope
/usr/include/wchar.h:808:40: error: ‘__stream’ was not declared in this scope
/usr/include/wchar.h:816:46: error: ‘__FILE’ has not been declared
/usr/include/wchar.h:825:45: error: ‘__FILE’ has not been declared
/usr/include/wchar.h:836:6: error: ‘__FILE’ has not been declared
/usr/include/wchar.h:845:8: error: ‘__FILE’ has not been declared
In file included from /usr/include/c++/4.6/bits/localefwd.h:44:0,
                 from /usr/include/c++/4.6/ios:42,
                 from main.cpp:1:
/usr/include/c++/4.6/cctype:66:11: error: ‘::isalnum’ has not been declared
/usr/include/c++/4.6/cctype:67:11: error: ‘::isalpha’ has not been declared
/usr/include/c++/4.6/cctype:68:11: error: ‘::iscntrl’ has not been declared
/usr/include/c++/4.6/cctype:69:11: error: ‘::isdigit’ has not been declared
/usr/include/c++/4.6/cctype:70:11: error: ‘::isgraph’ has not been declared
/usr/include/c++/4.6/cctype:71:11: error: ‘::islower’ has not been declared
/usr/include/c++/4.6/cctype:72:11: error: ‘::isprint’ has not been declared
/usr/include/c++/4.6/cctype:73:11: error: ‘::ispunct’ has not been declared
/usr/include/c++/4.6/cctype:74:11: error: ‘::isspace’ has not been declared
/usr/include/c++/4.6/cctype:75:11: error: ‘::isupper’ has not been declared
/usr/include/c++/4.6/cctype:76:11: error: ‘::isxdigit’ has not been declared
In file included from /usr/include/c++/4.6/bits/locale_facets.h:43:0,
                 from /usr/include/c++/4.6/bits/basic_ios.h:39,
                 from /usr/include/c++/4.6/ios:45,
                 from main.cpp:1:
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:50:35: error: ‘_ISupper’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:51:32: error: ‘_ISlower’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:52:32: error: ‘_ISalpha’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:53:32: error: ‘_ISdigit’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:54:33: error: ‘_ISxdigit’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:55:32: error: ‘_ISspace’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:56:32: error: ‘_ISprint’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:57:32: error: ‘_ISalpha’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:57:43: error: ‘_ISdigit’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:57:54: error: ‘_ISpunct’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:58:32: error: ‘_IScntrl’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:59:32: error: ‘_ISpunct’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:60:32: error: ‘_ISalpha’ was not declared in this scope
/usr/include/c++/4.6/i686-linux-gnu/./bits/ctype_base.h:60:43: error: ‘_ISdigit’ was not declared in this scope
In file included from /usr/include/c++/4.6/bits/basic_ios.h:39:0,
                 from /usr/include/c++/4.6/ios:45,
                 from main.cpp:1:
/usr/include/c++/4.6/bits/locale_facets.h:2530:5: error: ‘std::isspace’ declared as an ‘inline’ variable
/usr/include/c++/4.6/bits/locale_facets.h:2530:5: error: template declaration of ‘bool std::isspace’
/usr/include/c++/4.6/bits/locale_facets.h:2531:7: error: expected primary-expression before ‘return’
/usr/include/c++/4.6/bits/locale_facets.h:2531:7: error: expected ‘}’ before ‘return’
/usr/include/c++/4.6/bits/locale_facets.h:2536:5: error: ‘isprint’ declared as an ‘inline’ variable
/usr/include/c++/4.6/bits/locale_facets.h:2536:5: error: template declaration of ‘bool isprint’
/usr/include/c++/4.6/bits/locale_facets.h:2537:7: error: expected primary-expression before ‘return’
/usr/include/c++/4.6/bits/locale_facets.h:2537:7: error: expected ‘}’ before ‘return’
/usr/include/c++/4.6/bits/locale_facets.h:2537:75: error: expected declaration before ‘}’ token
~/LynX10/src/bug 
$
```

I have diff-ed the output of g++ -v as well as the files locale_facets.h, basic_ios.h, and ios from both machines - they are all identical.

Can anybody shed some light on this for me, please??  How did I mess this up, and, more importantly, how do I fix it?  I really don't want to turn my ten year old laptop into a compile server.....

---

### Post by azzamite on 2011-11-01
That just compiled in my box !

Did you install stuff like make and the development packages for libc6 libstdc++6 ?

My guess is that you're missing some -dev packages.

---

### Post by Wolf-Ekkehard on 2011-11-01
Nope - at least these two are all there.  But it is a good point nonetheless: Which dev packages would not come with g++-4.6, qt4-dev-tools and kdevelop?  I thought those basically should take care of all the dev packages I'd ever need.  Wrong??

These are the packages I installed:

```
apt-get -y install g++
apt-get -y install kdevelop
apt-get -y install libcppunit-dev
apt-get -y install libcppunit-doc
apt-get -y install autoconf
apt-get -y install autoconf-doc
apt-get -y install libncurses-Sdev
apt-get -y install cmake
apt-get -y install lsb-qt4
apt-get -y install qt4-dev-tools
apt-get -y install libqt4-dev
apt-get -y install doxygen
apt-get -y install doxygen-doc
apt-get -y install doxygen-gui
apt-get -y install graphviz
apt-get -y install valgrind
apt-get -y install libc6-dbg
apt-get -y install kcachegrind
apt-get -y install alleyoop
```

---

### Post by gsmanners on 2011-11-01
You have libc6-dbg but not libc6-dev?

---

### Post by Wolf-Ekkehard on 2011-11-01
I have both - on both machines

---

### Post by 3Miro on 2011-11-01
You should have the build-essential package installed (it pulls everything that you may need to compile stuff).

If this doesn't help, change the problem to:

```
//#include <ios>

int main( int argc, char** argv )
{
    ;
}
```

The error is in ios and should affect the rest.

---

### Post by Wolf-Ekkehard on 2011-11-01
yup - I have the build-essentials installed too.

If I take the include statement for ios out of the code, as you suggest, it compiles fine.  But whenever I include <iostream> (which includes <ios> down the line), it barfs.

---

### Post by gsmanners on 2011-11-01
Weird. Works fine here.

```
$ apt-cache policy g++
g++:
  Installed: 4:4.6.1-2ubuntu5
```

EDIT:

```
$ dpkg -S locale_facets.h
libstdc++6-4.6-dev: /usr/include/c++/4.6/bits/locale_facets.h
```

---

### Post by Wolf-Ekkehard on 2011-11-01
yup - works fine on my laptop too..

```
$ apt-cache policy g++
g++:
  Installed: 4:4.6.1-2ubuntu5
  Candidate: 4:4.6.1-2ubuntu5
  Version table:
 *** 4:4.6.1-2ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages
        100 /var/lib/dpkg/status

$ dpkg -S locale_facets.h
libstdc++6-4.6-dev: /usr/include/c++/4.6/bits/locale_facets.h
```

also, same on both of my machines

---

### Post by gsmanners on 2011-11-01
That is a head-scratcher. I'd suspect some RAM problems or maybe a bad sector on the drive of that Wind'ohs box.

---

### Post by Wolf-Ekkehard on 2011-11-01
Well - hardware is always a possibility, I'll run some diagnostics - at least you made me feel less stupid :-)

---

### Post by GeneralZod on 2011-11-02
As a guess, I'd say you might be missing some header: it thinks isspace, etc are macros (like in C, but not in C++), which hints that it's looking for the C++ version of the header which contains this, not finding it, and #including the C version instead.

Try:

```

dpkg --listfiles libstdc++6-4.6-dev  | xargs -n1 file | grep ERROR
```

and see if any errors are reported.

---

### Post by Wolf-Ekkehard on 2011-11-02
Smart idea!!  Of course, I would prefer for it to report an error if it doesn't find the C++ version instead of silently including the C version - but that's just me...

I ran that, but no error was reported.  Then I also dumped the output of xargs into a file and compared it with the output of the identical command run on my laptop - diff came out clean :-(

BTW - hw diagnostics came out clean too :-(

---

### Post by gnometorule on 2011-11-02
I'd uninstall everything related to gcc/c++, and then install merely the basics with build-essential. All I can think of is that a later lib overwrote some include path as the error is already in wchar.h etc. If it compiles after, carefully add additional libs.

---

### Post by Zugzwang on 2011-11-02
@OP: Would you mind posting the output of "g++ --version" here? Is is actually version 4.6, whose include files you are using according to your output?

---

### Post by Wolf-Ekkehard on 2011-11-02
No Problem.  Here it is:

$ g++ --version
g++ (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

---

### Post by Wolf-Ekkehard on 2011-11-06
OK - I'd hate to mark this one "solved" as I could not find out root cause...

I uninstalled everything even remotely related to the C++ compiler and its libraries - no change when I got the build-essential package back.  So I ended up re-installing 11.10 and all of my applications, which got rid of the problem - everything compiles fine now, as it does on any of my other machines.

---

