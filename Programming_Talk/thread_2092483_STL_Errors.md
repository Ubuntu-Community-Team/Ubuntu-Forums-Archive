---
title: "STL Errors"
date: 2012-12-08
forum: Programming Talk
---

### Post by DBQ on 2012-12-08
Hi everybody.

I have this problem. When trying to compile sample code found at [http://www.cplusplus.com/reference/forward_list/forward_list/assign/](http://www.cplusplus.com/reference/forward_list/forward_list/assign/)

```

// forward_list::assign
#include <iostream>
#include <forward_list>

int main ()
{
  std::forward_list<int> first;
  std::forward_list<int> second;

  first.assign (4,15);                           // 15 15 15 15

  second.assign (first.begin(),first.end());     // 15 15 15 15

  first.assign ( {77, 2, 16} );                  // 77 2 16

  std::cout << "first contains: ";
  for (int& x : first) std::cout << ' ' << x;
  std::cout << '\n';

  std::cout << "second contains: ";
  for (int& x : second) std::cout << ' ' << x;
  std::cout << '\n';

  return 0;
}

```

I get the following errors, unless I compile it with -std=c++0x flag (I am using g++). Why?

```

In file included from /usr/include/c++/4.7/forward_list:35:0,
                 from sample.cpp:3:
/usr/include/c++/4.7/bits/c++0x_warning.h:32:2: error: #error This file requires compiler and library support for the ISO C++ 2011 standard. This support is currently experimental, and must be enabled with the -std=c++11 or -std=gnu++11 compiler options.
sample.cpp: In function ‘int main()’:
sample.cpp:7:3: error: ‘forward_list’ is not a member of ‘std’
sample.cpp:7:21: error: expected primary-expression before ‘int’
sample.cpp:7:21: error: expected ‘;’ before ‘int’
sample.cpp:8:3: error: ‘forward_list’ is not a member of ‘std’
sample.cpp:8:21: error: expected primary-expression before ‘int’
sample.cpp:8:21: error: expected ‘;’ before ‘int’
sample.cpp:10:3: error: ‘first’ was not declared in this scope
sample.cpp:12:3: error: ‘second’ was not declared in this scope
sample.cpp:14:16: warning: extended initializer lists only available with -std=c++11 or -std=gnu++11 [enabled by default]
sample.cpp:17:17: error: range-based ‘for’ loops are not allowed in C++98 mode
sample.cpp:21:17: error: range-based ‘for’ loops are not allowed in C++98 mode
mike@mike-ThinkPad-W520:~/Desktop/Untitled Folder$ g++ sample.cpp -o s -std=c++0x
mike@mike-ThinkPad-W520:~/Desktop/Untitled Folder$ 

```

Is there a way to avoid using the flag? Thank You!

---

### Post by spjackson on 2012-12-08
g++ supports several flavours of C++. The default is gnu++98. You are using features that are new in C++11. As far as I am aware, the only way to do this is to use -std=c++0x or -std=c++11 (which are equivalent). Why is that a problem for you?

---

