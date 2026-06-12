---
title: "Passing a function as a parameter to another function"
date: 2009-01-02
forum: Programming Talk
---

### Post by Facetious Falcon on 2009-01-02
I've got some code which won't compile which was made in Visual C++.

Basically I get errors if a pass-by-reference function has as it's parameter as another function.

For example:

function1(function2(x));

function1 is a pass by reference function. If I try and get it to work like this it means I have to go through and do the calculation and input it as a variable.

For example:

var1 = function2(x);
function1(var1);

This works for some reason.

I'm using the GCC compiler within Codeblocks. The code I'm using is quite old so I'm not sure if they're were any major changes but I don't understand why it would only be for pass-by-reference functions.

Thanks very much for the help.

---

### Post by dwhitney67 on 2009-01-02
You must be doing something other than what you described in the OP.

[php]
#include <iostream>

void function1(int value)
{
  std::cout << "received a " << value << std::endl;
}

int function2()
{
  return 2;
}

int main()
{
  function1(function2());
}
[/php]

Unless of course, you have function1() declared as:
[php]
void function1(int& value)
{
  ...
}
[/php]
Then you would get this error:
```

g++ test.cpp 
test.cpp: In function &#8216;int main()&#8217;:
test.cpp:15: error: invalid initialization of non-const reference of type &#8216;int&&#8217; from a temporary of type &#8216;int&#8217;

```
In such case, you need to pass the reference of a variable; you cannot pass a reference to a non-const rvalue.

---

