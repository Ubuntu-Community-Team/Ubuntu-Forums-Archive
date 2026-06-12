---
title: "include &lt;string&gt; -&gt;error and include &lt;string.h&gt; -&gt; no error. Why?"
date: 2008-07-07
forum: Programming Talk
---

### Post by KIAaze on 2008-07-07
What is the difference between "#include <string>" and "#include <string.h>"?

For instance:
```
#include <string.h>
#include <iostream>
using namespace std;

int main(void)
{
        cout<<strlen("test")<<endl;
        return(0);
}

```
compiles, while
```
#include <string>
#include <iostream>
using namespace std;

int main(void)
{
        cout<<strlen("test")<<endl;
        return(0);
}

```
does not and gives me this error message:
```
string_test.cpp: In function &#8216;int main()&#8217;:
string_test.cpp:7: error: &#8216;strlen&#8217; was not declared in this scope

```

Compilation command:
```
g++ string_test.cpp
```


Does <string> mean that it will search for string.hpp or other before string.h?
Because I do indeed have several string.hpp in /usr/include/boost. 

Version info:
```
$g++ -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.1-3ubuntu1' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.1 (Ubuntu 4.3.1-3ubuntu1)

```
(using Ubuntu 8.10)

Note:
I'm asking this because I got the
"'strlen' was not declared in this scope" error while trying to compile sugar from source, and I hope that there's a better solution than modifying the source code. :???:
[I already changed the source code and got passed this error and am now stuck on a new one...]

Could it be the compiler version?

---

### Post by WW on 2008-07-07
**<string>** is for the [C++ string class](http://www.cplusplus.com/reference/string/string/).

**<string.h>** is for the C string functions.  The function strlen() is for C-style strings.

What language is sugar written in?

---

### Post by KIAaze on 2008-07-07
Thanks for the clarification.

Well, the compilation process with sugar-jhbuild clearly uses g++ and I found some classes and cout in the code, so I'd say C++. (at least xapian, because I believe most of the rest of it is Python)

Here are the instructions I was following:
[http://wiki.laptop.org/go/Sugar_with_sugar-jhbuild](http://wiki.laptop.org/go/Sugar_with_sugar-jhbuild)

I'm trying to compile it from source because I can't install the debian packages due to dependency problems in Intrepid. :/

The string problem was in /source/xapian-core-1.0.2/net/serialise.cc to be exact.
It had "#include <string>"...

Now I'm stuck on this:
```
net/tcpserver.cc: In static member function 'static int TcpServer::get_listening_socket(const std::string&, int)':                             
net/tcpserver.cc:190: error: 'memcpy' was not declared in this scope                                                                           
make[2]: *** [net/tcpserver.lo] Error 1                                                                                                        
make[2]: Leaving directory `/home/KIAaze/sugar/sugar-jhbuild/source/xapian-core-1.0.2'                                                           
make[1]: *** [all-recursive] Error 1                                                                                                           
make[1]: Leaving directory `/home/KIAaze/sugar/sugar-jhbuild/source/xapian-core-1.0.2'                                                           
make: *** [all] Error 2                                                                                                                        
*** error during stage build of xapian-core: ########## Error running make   *** [7/45]
```
My experience tells me that simply including a string header would do the trick, but I find it strange that I would have to change the source code.

edit:
C++ for Xapian explicitly confirmed: [http://xapian.org/](http://xapian.org/)

---

