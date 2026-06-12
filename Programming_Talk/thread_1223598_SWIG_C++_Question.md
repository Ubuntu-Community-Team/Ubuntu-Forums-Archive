---
title: "SWIG C++ Question"
date: 2009-07-26
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2009-07-26
Hi Guys

I'm having a timker with swig to try and get some of my C++ to work along with my Python.

The problem is that I followed the tutorials and still get the following error:

import test
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "test.py", line 7, in <module>
    import _test
ImportError: ./_test.so: undefined symbol: _ZN4TestC1Ev

Here are my source files:

```
 // test.h 
#include <string>

class Test {
    public:
        Test();
//        void Say(string msg);
        ~Test();

};
```

```
#include "test.h"

Test::Test()
{
   std::cout << "Test created" << std::endl;
}

/*void Test::Say(string msg)
{
  cout << msg << endl;
}*/

Test::~Test()
{
   std::cout << "Test Deleted" << std::endl;
}
```

Finally my interface:

```
%module test

%{
#include "test.h"
%}

%include "test.h"
%include "std_string.i"

```

and this is how I compile:

```

swig -c++ -python test.i
gcc -fPIC -c test_wrap.cxx -I/usr/include/python2.5
g++ -shared test_wrap.o -o _test.so

```

Then I finally go into the python shell and import the tet module, and thats where my error happens!

Can anyone offer words of advise?

Mike

---

### Post by TheStatsMan on 2009-07-26
Don't have time for a good look but don't you need to include<iostream> in test.h and shouldn't you be using g++ instead of gcc.

---

### Post by Mickeysofine1972 on 2009-07-27
> **TheStatsMan said:**
> Don't have time for a good look but don't you need to include<iostream> in test.h and shouldn't you be using g++ instead of gcc.

Well I did try g++ the first time round as the tutorial on the SWIG site uses c++ on the commandline so I figure I would just use g++ instead, however, I also saw another tutorial that said that using gcc with the -fPIC switch was important as it make the variales link better, (not really sure now if thats true or not)

Mike

---

