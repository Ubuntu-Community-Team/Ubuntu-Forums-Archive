---
title: "install STL (Standard Template Library)"
date: 2009-09-09
forum: Programming Talk
---

### Post by secure on 2009-09-09
hello
i'm new to ubuntu
i want to use STL so i download it from 
[http://www.sgi.com/tech/stl/](http://www.sgi.com/tech/stl/)


i'm untar it and move it to /usr/include/stl

in main.cpp
#include<cstdio>
#include<cstdlib>	
#include<stl/stl_vector.h>
int main()
{
	printf("Hello World\n");
	
}

but when i compile it's tell

In file included from Dijkstra.cpp:3:
/usr/include/stl/stl_vector.h:34:28: error: concept_checks.h: No such file or directory
In file included from Dijkstra.cpp:3:
/usr/include/stl/stl_vector.h:122: error: expected constructor, destructor, or type conversion before &#8216;template&#8217;

it's FAQ said
How do I install the SGI STL?
You should unpack the STL include files in a new directory, and then use the -I (or /I) option to direct the compiler to look there first. We don't recommend overwriting the vendor's include files.

At present the SGI STL consists entirely of header files. You don't have to build or link in any additional runtime libraries. 


but i don't know how to use -I and what it's called
thanks

---

### Post by dwhitney67 on 2009-09-09
You should not have to download a specific STL from SGI.  GCC provides a wonderful "knock-off" of the STL that pretty much 99.44% of all Linux C++ developers use.

If you have not already done it, install GCC using:
```

sudo apt-get install build-essential

```

---

### Post by secure on 2009-09-09
oh thanks dwhitney67

but could you tell me when i download library from website 
1. where place i should copy that library
2. how can i do it work

---

### Post by Simian Man on 2009-09-09
Don't use the one from SGI.  In fact don't download any program or libraries outside directly form websites unless the package manager doesn't have them (or there are known problems with them).

---

### Post by MadCow108 on 2009-09-09
to answer the question:
you need to tell the compiler where to look for the include files.
this is done with the -I flag
e.g:
g++ -I/usr/include/stl yourfile.cpp

---

### Post by secure on 2009-09-09
thank you everyone for your help
:):):):)

---

### Post by dwhitney67 on 2009-09-09
> **secure said:**
> oh thanks dwhitney67

but could you tell me when i download library from website 
1. where place i should copy that library
2. how can i do it work

Answers:

1.  The apt-get package manager will take care of that for you.  But if you must know, look in /usr/include/c++, and then delve further into the subdirectories.  These vary from one Linux/Ubuntu version to another, depending on the version of GCC that is installed.

2.  What follows is a simple program, and instructions on how to build it and run it:
```

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

```
```

g++ SimpleProgram.cpp -o simple
./simple

```

---

### Post by Maxxum7 on 2010-04-29
g++ fails to compile the following:

```
#include <iostream>

using namespace std;

int main() {
  ostream_iterator<int> output(cout, " ");

  return 0;
}
```


```

a.cpp: In function ‘int main()’:
a.cpp:6: error: ‘ostream_iterator’ was not declared in this scope
a.cpp:6: error: expected primary-expression before ‘int’
a.cpp:6: error: expected ‘;’ before ‘int’

```

My g++ is
```
$ g++ -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9)
```

Could you guys give some clue what is wrong?

Thanks a lot!:guitar:

---

### Post by PaulM1985 on 2010-04-29
You need to include iterator at the top of the file, so the two includes are:

#include <iostream>
#include <iterator>

This should get it compiling.

Paul

---

### Post by Maxxum7 on 2010-04-29
Thank you, Paul!

Can you take a look at this one?

```
#include <iostream>
#include <vector>
#include <iterator>

using namespace std;

template <class T>
void printVector(const vector<T> &vec) {
  vector<T>::const_iterator p1; // what is wrong with this statement?
  for (p1 = vec.begin(); p1 != vec.end(); ++p1) {
    cout << *p1 << ' ';
  }
}

int main() {

  return 0;
}
```

g++ complains:
```
a.cpp: In function &#8216;void printVector(const std::vector<T, std::allocator<_CharT> >&)&#8217;:
a.cpp:9: error: expected &#8216;;&#8217; before &#8216;p1&#8217;
a.cpp:10: error: &#8216;p1&#8217; was not declared in this scope

```

BTW, visual studio 2008 has no problem to compile the above.

> **PaulM1985 said:**
> You need to include iterator at the top of the file, so the two includes are:

#include <iostream>
#include <iterator>

This should get it compiling.

Paul

---

### Post by dwhitney67 on 2010-04-29
Change the following statement:
```

vector<T>::const_iterator p1;

```
to appear as:
```

**typename** vector<T>::const_iterator p1;

```


P.S.  You may find using the following to be easier than defining your own print function:
```

#include <vector>
#include <iterator>
#include <algorithm>
#include <iostream>
...
std::vector<int> myVector;
...
std::copy(myVector.begin(), myVector.end(), std::ostream_iterator<int>(std::cout, " "));

```

---

### Post by Maxxum7 on 2010-04-29
Thank you very much, dwhitney67!

> **dwhitney67 said:**
> Change the following statement:
```

vector<T>::const_iterator p1;

```
to appear as:
```

**typename** vector<T>::const_iterator p1;

```


P.S.  You may find using the following to be easier than defining your own print function:
```

#include <vector>
#include <iterator>
#include <algorithm>
#include <iostream>
...
std::vector<int> myVector;
...
std::copy(myVector.begin(), myVector.end(), std::ostream_iterator<int>(std::cout, " "));

```

---

