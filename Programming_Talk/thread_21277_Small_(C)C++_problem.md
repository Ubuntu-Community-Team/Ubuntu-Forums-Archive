---
title: "Small (C/)C++ problem"
date: 2005-03-21
forum: Programming Talk
---

### Post by Kimm on 2005-03-21
I am writing a small function. This function can take two arguments, and well, so far it works, the only problem I am having is that I want the secund argument to be optional. Does anyone know how I can do this??

---

### Post by dcraven on 2005-03-21
In C++ you can declare function arguments to have default values, in which case passing the value at the call is essentially optional.

For example, here are test.h and test.cc files respectively...

```

class TestClass
{
public:
        void TestFunc (int arg1, int arg2 = 0);
};

```

```

#include <iostream>
#include "test.h"

using namespace std;

void TestClass::TestFunc (int arg1, int arg2)
{
        cout << "Arg1: " << arg1 << endl;
        cout << "Arg2: " << arg2 << endl;
}

int main (int argc, char** argv)
{
        TestClass test;
        test.TestFunc (2, 4);
        test.TestFunc (4);

        return 0;
}

```

And it's output:
```

Arg1: 2
Arg2: 4
Arg1: 4
Arg2: 0

```

You can see in the main function that the TestFunc is called twice, once with two arguments and once with only one.

HTH,
~djc

---

### Post by ebrowne on 2005-03-21
There are a couple of ways of doign this.  If your using C unfortunitally you'll have to pass a "default" value if the option is not to be passed.  In C++ this can be accomplised by writeing two functions with the same name just differnent number of arguments or one that passes a default like in C but the C++ handles this differently.  I can never rememver if this is call overloading or polymorphism but I hope this helps.

---

### Post by dcraven on 2005-03-21
[QUOTE=ebrowne]There are a couple of ways of doign this.  If your using C unfortunitally you'll have to pass a "default" value if the option is not to be passed.
[/QUOTE]
I didn't even know that C could do this.. I'll have to experiment.

[QUOTE=ebrowne]
  In C++ this can be accomplised by writeing two functions with the same name just differnent number of arguments or one that passes a default like in C but the C++ handles this differently.  I can never rememver if this is call overloading or polymorphism but I hope this helps.[/QUOTE]
Yes, this is another way. This would be called overloading, which sounds bad but isn't. :-) 

Cheers,
~djc

---

