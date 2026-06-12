---
title: "C++ compiling problem"
date: 2005-11-22
forum: Programming Talk
---

### Post by lukasmaci on 2005-11-22
Hello, I am trying to compile my first Hello world program in C++.
I have installed g++ by Synaptic and I have written this code
```

#include <iostream>
using namespace std;

int main() 
{
	cout << "Hello world";
	return 0;
}

```

If I try to compile it ```
g++ prvni.cpp -o prvni
``` g++ writes me this
```

In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++config.h:35,                 from /usr/include/c++/4.0.2/iostream:43,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/os_defines.h:39:22: error: features.h: No such file or directory
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:41,                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/cstring:51:20: error: string.h: No such file or directoryIn file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:42,                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/cstdio:52:19: error: stdio.h: No such file or directory
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:43,                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/clocale:49:20: error: locale.h: No such file or directoryIn file included from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:44:38: error: langinfo.h: No such file or directory
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:45:56: error: iconv.h: No such file or directory
/usr/include/c++/4.0.2/i486-linux-gnu/bits/c++locale.h:46:39: error: libintl.h: No such file or directory
In file included from /usr/include/c++/4.0.2/i486-linux-gnu/bits/gthr.h:114,
                 from /usr/include/c++/4.0.2/i486-linux-gnu/bits/c++io.h:37,
                 from /usr/include/c++/4.0.2/iosfwd:46,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/gthr-default.h:43:21: error: pthread.h: No such file or directory
/usr/include/c++/4.0.2/i486-linux-gnu/bits/gthr-default.h:44:20: error: unistd.h: No such file or directory
In file included from /usr/include/c++/4.0.2/iosfwd:47,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/cctype:49:19: error: ctype.h: No such file or directory
In file included from /usr/include/c++/4.0.2/cwchar:51,
                 from /usr/include/c++/4.0.2/bits/postypes.h:46,
                 from /usr/include/c++/4.0.2/iosfwd:49,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/ctime:51:18: error: time.h: No such file or directory
In file included from /usr/include/c++/4.0.2/bits/postypes.h:46,
                 from /usr/include/c++/4.0.2/iosfwd:49,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/cwchar:54:19: error: wchar.h: No such file or directory
In file included from /usr/include/c++/4.0.2/iosfwd:49,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/bits/postypes.h:49:35: error: stdint.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h:11,
                 from /usr/include/c++/4.0.2/climits:49,
                 from /usr/include/c++/4.0.2/bits/stl_algobase.h:66,
                 from /usr/include/c++/4.0.2/bits/char_traits.h:46,
                 from /usr/include/c++/4.0.2/ios:45,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /usr/include/c++/4.0.2/bits/stl_algobase.h:67,
                 from /usr/include/c++/4.0.2/bits/char_traits.h:46,
                 from /usr/include/c++/4.0.2/ios:45,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/cstdlib:57:20: error: stdlib.h: No such file or directoryIn file included from /usr/include/c++/4.0.2/debug/debug.h:272,
                 from /usr/include/c++/4.0.2/bits/stl_algobase.h:76,
                 from /usr/include/c++/4.0.2/bits/char_traits.h:46,
                 from /usr/include/c++/4.0.2/ios:45,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/cassert:48:20: error: assert.h: No such file or directoryIn file included from /usr/include/c++/4.0.2/bits/locale_facets.h:46,
                 from /usr/include/c++/4.0.2/bits/basic_ios.h:44,
                 from /usr/include/c++/4.0.2/ios:50,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from prvni.cpp:1:
/usr/include/c++/4.0.2/cwctype:52:20: error: wctype.h: No such file or directory/usr/include/c++/4.0.2/cstring:79: error: ‘::memcpy’ has not been declared


```

and many many others errors.
Please, could you tell me what to do.
Thank you very much.

---

### Post by gord on 2005-11-22
```
 sudo apt-get install build-essential 
```

gcc is only the compiler, you also need all the standard libarys and the like.

---

### Post by narcolept on 2005-11-22
it appears you're missing libraries.  apt-cache search g++ and look for library/devel packages, and this should work for you.  What the errors are saying is that it's missing those funtions.  all g++ itself is is the compiler, you need libraries and header files in order to compile.

---

### Post by Biased turkey on 2005-11-23
As Gord says, installing build-essential is ... well essential for Developing C++ programs. That should solve your problem.
[https://wiki.ubuntu.com/InstallingCompilers]("https://wiki.ubuntu.com/InstallingCompilers")


After compiling a few programs by hand, just to see how it works , I highly suggest to install Anjuta the integrated development package.

---

### Post by AndreiCiprian on 2005-11-24
I have installed build-essential and anjuta too.
Things are working perfectly no matter what solution I choose: terminal or ide.

---

