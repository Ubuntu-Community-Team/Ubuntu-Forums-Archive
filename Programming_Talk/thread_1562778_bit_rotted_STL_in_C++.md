---
title: "bit rotted STL in C++"
date: 2010-08-28
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-28
I have some C++ code that uses the Standard Template Library, but was written in 1995. Today it can't find the STL header files... like #include <function.h> consequently reporting things like:
```

operator.1.cc:24: error: no match for &#8216;operator!=&#8217; in &#8216;Small != Large&#8217;

```

I do have an old set of STL headers and if I use those then it compiles, but I want to change the code to use contemporary STL.

The closest I could find is called "functional", but that does NOT appear to have an equivalent :confused:

```

template <class T1, class T2>
inline bool operator!=(const T1& x, const T2& y) {
    return !(x == y);
}

```

Has anyone got suggestion for how I can find all the correct new header file names... and on a philosophical note: Do you think the new file structure and naming convention of header files is actually an improvement?

Thanks in advance :)

---

### Post by MadCow108 on 2010-08-28
I am not familiar with the old headers but rel_ops namespace in <utility> is probably what you're looking for:
[http://www.cplusplus.com/reference/std/utility/rel_ops/](http://www.cplusplus.com/reference/std/utility/rel_ops/)

---

### Post by dwhitney67 on 2010-08-28
> **worksofcraft said:**
> I have some C++ code that uses the Standard Template Library, but was written in 1995. Today it can't find the STL header files... like #include <function.h> consequently reporting things like:
```

operator.1.cc:24: error: no match for &#8216;operator!=&#8217; in &#8216;Small != Large&#8217;

```

In the past, STL header files were appended with a .h extension; that is no longer the case.  In addition to this, STL containers and utility functions have been added to the std namespace.

Here's a *before* and *after* case (which is very trivial):
```

// before

#include <iostream.h>

int main()
{
   cout << "hello world." << endl;
}

// after

#include <iostream>

int main()
{
   std::cout << "hello world" << std::endl;
}

```
As for the error you are getting above, it would appear that the operator!=() is not defined for the data type represented by the objects Small and Large.  What type of object are these?

Here's a trivial example of where an class is defined with the operator!=() method:
```

#include <cassert>

class Foo
{
public:
   Foo(int val) : myVal(val) {}

   //bool operator==(const Foo& other) const
   //{
   //   return myVal == other.myVal;
   //}

   bool operator!=(const Foo& other) const
   {
      return myVal != other.myVal;
   }

private:
   int myVal;
};

// This is not required if class method Foo::operator!=() is defined.
//template <class T1, class T2>
//inline bool operator!=(const T1& x, const T2& y)
//{
//   return !(x == y);
//}

int main()
{
   Foo ten(10);
   Foo two(2);

   assert(ten != two);
}

```

---

### Post by worksofcraft on 2010-08-28
Hey thanks for both those great ideas :)

I tried what you suggest and including a "using namespace std;" seemed very promising, but alas still no joy with our modern stl yet :(

I did find a slightly older stl but still a lot newer that the one from 1994.

That one uses the rel_ops you mention and did compile.

So I wittled the problem right down to a few lines of code and the 3 files from that old stl.

I can compile it using:
g++ -DYEAR=1994 -I./stl1994 operator.1.cc

but compiling with the new stl gives me that error message. Here I'll attach a tar of the necessary bits in the hope somone can see what I'm missing.

Thanks in advance

---

### Post by MadCow108 on 2010-08-28
add an
#include <utility>

and an
using namespace std::rel_ops

and it should work
rel_ops:: is inside std:: (nested namespace) so you don't need the std:: if you did a using namespace std; beforehand

---

### Post by worksofcraft on 2010-08-28
> **MadCow108 said:**
> add an
#include <utility>

and an
using namespace std::rel_ops

and it should work
rel_ops:: is inside std:: (nested namespace) so you don't need the std:: if you did a using namespace std; beforehand

ah... thanks, eventually I found it:
```

#include <function.h> // 1994 version of STL
// replaced with:
#include <bits/stl_relops.h> // contemporary stl
#include <utility>
#include <functional>
#include <algorithm>
using namespace std;
using namespace std::rel_ops;

```

:)

---

### Post by MadCow108 on 2010-08-28
you should not include the bits folder, this is plattform dependent
stick to the standard headers!!

if your utility does not include rel_ops you have a buggy/non-standard version either file a bugreport or change to a standard conforming version (the standard is 12 years old everybody should have implemented this simple part by now!)

[quote=C++ standard]
20.3 Utility components
utility
This subclause contains some basic function and class templates that are used throughout the rest of the
library.
Header <utility> synopsis:

#include <initializer_list>
namespace std {
// 20.3.1, operators:
namespace rel_ops {
template<class T>
template<class T>
template<class T>
template<class T>
}
...
[/quote]

---

### Post by worksofcraft on 2010-08-28
> **MadCow108 said:**
> you should not include the bits folder, this is plattform dependent
stick to the standard headers!!

if your utility does not include rel_ops you have a buggy/non-standard version either file a bugreport or change to a standard conforming version (the standard is 12 years old everybody should have implemented this simple part by now!)

I searched my whole file system. There are no files containing the string **rel_ops** in their name. The closest I could find is:
```

/usr/include/c++/4.4/bits/stl_relops.h

```
I have a standard Ubuntu 10.04 with build essential installed. I also checked a Hardy Heron Ubuntu and that doesn't have them either.

Edit: Oh sorry now I understand what you say. The name space rel_ops is supposed to be defined in header file <utility> I'll try to work out why it isn't appearing and report back later.

Later: OK problem solved, my installation had got corrupted I have no idea how, but the one on a different virtual machine worked just fine.

I could never have found it without your information about name spaces and <utility> header! Thanks :)

---

