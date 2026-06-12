---
title: "g++ cannot find &lt;iostream&gt;"
date: 2008-09-17
forum: Programming Talk
---

### Post by tmtmtmtm on 2008-09-17
I use Redhat 7, there is GCC3.2.2 with it.
But I built gcc-2.7.2.3 on it due to the need of my project.

This is my test code.
#include <iostream>
using namespace std;
int main()
{
   int i=0;
   i++;
}

it cannot be built by g++ in gcc2723

my command:
g++ -v -Wall /home/tm/test/test.cpp

   ....
   #include<...> search starts here:
   /usr/local/gcc-2.7.2.3/include/g++
   .....
   /usr/include
   ENd of search list.
   /home/tm/test/test.cpp:1: iostream: No such file or directory.

Actually, iostream is in /usr/include/c++/3.2.2


So Question:
(1) how can I link gcc2723 with this include path? Is there some environment variable I should change?

(2)You see, there is a library for 3.2.2, but where can I get the library for 2.7.2.3?

---

### Post by dribeas on 2008-09-17
> **tmtmtmtm said:**
> #include<...> search starts here:
   /usr/local/gcc-2.7.2.3/include/g++

So Question:
(1) how can I link gcc2723 with this include path? Is there some environment variable I should change?

(2)You see, there is a library for 3.2.2, but where can I get the library for 2.7.2.3?

You can probably give the include directories with -I so that it finds its own <iostream>, probably in /usr/local/gcc-2.7.2.3/... Note that STLs are not always compatible between different g++ releases. I assume that you really need to use g++ 2.7.3... else you'll be better off by upgrading to g++ 3.x or 4.x.

---

### Post by rnodal on 2008-09-17
Did you fully install that one version of gcc that you want to use? If you did then doing something like:
[PHP]
[command prompt]:path/to/g++ myfile.cpp
[/PHP]

should work.

-r

---

