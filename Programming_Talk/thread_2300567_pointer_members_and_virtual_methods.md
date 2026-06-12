---
title: "pointer members and virtual methods"
date: 2015-10-26
forum: Programming Talk
---

### Post by chuchi on 2015-10-26
Hi there!

When using a virtual method in a class that has a pointer member, it seems the pointer is initialized somehow. Here is an example

```


#include <iostream>
using namespace std;

class Test
{
public:
  int var;
  int *ptr;
  
  /*virtual*/ void doNothing(){
    
  };
  
};

int main()
{
  Test t0;
  cout << (t0.ptr == NULL) << endl;
  return 0;
}


```

The output is 1, but if you change ‘doNothing’ to be virtual, the output is 0.

Could someone explain to me why??

Thanks a lot!

---

### Post by TheFu on 2015-10-26
Those are implementation specific questions. I'm not current on C++, but when I learned, unassigned variables could get junk values. This is why classes should have constructors that set all members to known values.

Virtual methods a useful with inheritance.  [http://www.cplusplus.com/doc/tutorial/polymorphism/](http://www.cplusplus.com/doc/tutorial/polymorphism/)
They are dynamic function pointers based on the class structure and aren't known until runtime. A subclass may  or may not have implemented the specific method. I suspect  in  the example above, the virtual  FP has been optimized by the compiler  since it doesn't actually do anything. Add a return();  and see what happens.


BTW, would really  help to specify the language in the thread title. Could  be 500 different languages discussed in  this forum - and  that number is actually a little less than the current count of languages at rosettacode.org.

---

### Post by spjackson on 2015-10-27
The pointer t0.ptr is not initialised. When you use its value you have undefined behaviour, so don't do it.

Why are the results of the undefined behaviour different in the 2 cases? Well a difference is that if a class has at least one virtual function then it has a vtable (virtual function table) but if there are no virtual functions then there is no vtable. sizeof(Test) will be different for the 2 cases and therefore the objects are laid out differently across uninitialised memory.

However, you might also get different results by adding further members to the class or compiling for debug or using a different compiler. Undefined behaviour is just that: undefined.

---

