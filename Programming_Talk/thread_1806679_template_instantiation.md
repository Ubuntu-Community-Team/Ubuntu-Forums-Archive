---
title: "template instantiation"
date: 2011-07-18
forum: Programming Talk
---

### Post by Blackbug on 2011-07-18
I have around 20 template classes. And, I need to write a small testprogram to test the Instantiation of all these classes.
 
Kindly suggest the approach how should i do that..
 
thanks

---

### Post by dwhitney67 on 2011-07-18
```

#include <Template1.h>
#include <Template2.h>
...
#include <Template20.h>

class TestClass
{
};

int main()
{
   Template1<TestClass> t1;
   Template2<TestClass> t2;
   ...
   Template20<TestClass> t20;
}

```
Voilà -- since all you inquired about is how to *instantiate* an object, the code above should suffice.  Of course, replace "Template" with your real class names.

---

### Post by nvteighen on 2011-07-18
If this was about Lisp macros, I would have posted an elegant way to do it. But as this is about C++ templates, I think dwhitney67's solution is the only possible one.

---

### Post by Blackbug on 2011-07-19
Yes I already implemented the same
But, was wondering if there could be any other possible way to test templates.
 
In this case, but what if I will pass any type how to test it, consider in the example above if i want to use a type <template 110> which i havent either specialized or taken into account in my main template class.
 
I am not clear myself.
I wanted to find a way to limit my template class for instantiating a particular set of types say from <template1> ... <template10> beyond this it should not work..
 
thanks for the suggestion though..

---

### Post by dwhitney67 on 2011-07-19
I'm not sure what you are asking.

You could try automating the tests with a script; say something like:

Template.h:
```

#include <iostream>

template <typename T>
class MyTemplate
{
public:
   MyTemplate(T& obj) : myObject(obj) {}

   void print(std::ostream& os) { os << myObject << std::endl; }

private:
   T myObject;
};

```

TestTemplate.sh:
```

#!/bin/bash

set -e

# Test with these object types
#
OBJ_TYPES="int float double NonExistentClass"

TESTCPP="test.cpp"

for obj in $OBJ_TYPES; do

   cat <<-EOF > $TESTCPP
      #include "Template.h"
      int main()
      {
         $obj obj;
         MyTemplate<$obj> mt(obj);
         mt.print(std::cout);
      }
   EOF

   g++ -Wall -pedantic $TESTCPP
   ./a.out

   rm -f $TESTCPP a.out
done

```

---

