---
title: "[c++] Request For Member ... In ... Which Is Of Nonclass Type ..."
date: 2010-11-22
forum: Programming Talk
---

### Post by josephellengar on 2010-11-22
Hi! I'm using c++ here.
I can't figure this error out. My program works perfectly when I do not use this class, but this one class claims that the functions that I am testing do not exist:

```

LinkedListDriver.cpp:22: error: request for member 'addElement' in 'Ross', which is of non-class type 'LinkedList<int>()'

LinkedListDriver.cpp:23: error: request for member 'addElement' in 'Ross', which is of non-class type 'LinkedList<int>()'

LinkedListDriver.cpp:24: error: request for member 'addElement' in 'Ross', which is of non-class type 'LinkedList<int>()'

LinkedListDriver.cpp:25: error: request for member 'addElement' in 'Ross', which is of non-class type 'LinkedList<int>()'

LinkedListDriver.cpp:26: error: request for member 'displayList' in 'Ross', which is of non-class type 'LinkedList<int>()'

LinkedListDriver.cpp:27: error: request for member 'removeElement' in 'Ross', which is of non-class type 'LinkedList<int>()'

LinkedListDriver.cpp:28: error: request for member 'displayList' in 'Ross', which is of non-class type 'LinkedList<int>()'

LinkedListDriver.cpp:30: error: request for member 'nodeArray' in 'Ross', which is of non-class type 'LinkedList<int>()'

LinkedListDriver.cpp:33: error: request for member 'isEmpty' in 'Ross', which is of non-class type 'LinkedList<int>()'

LinkedListDriver.cpp:34: error: request for member 'removeElementFmHead' in 'Ross', which is of non-class type 'LinkedList<int>()'

LinkedListDriver.cpp:35: error: request for member 'displayList' in 'Ross', which is of non-class type 'LinkedList<int>()'

```

I have made sure that the header file is included. I have checked for spelling and capitalization errors in all of the functino names. I have checked the parameter list. I have checked that the respective functions have good parameters and work on their own. Everything checks out. I just can't figure out what is wrong. Any help would be greatly appreciated. Code attached below.

---

### Post by dwhitney67 on 2010-11-22
Fix the following in LinkedListDriver.cpp:
```

LinkedList<int> Ross;
...
int arr[100];
...

```
As for your template class, LinkedList, the code must be implemented within the header file.  You cannot place this code in a separate .cpp file, unless of course you are careful not to compile it directly.

What I recommend is that you rename the LinkedList.cpp file to LinkedList.impl, and then include this at the end of the LinkedList.h file.

Btw, never add a using namespace directive to a header file.  Only include header files that are necessary to compile a particular module.  Also, and this is important, insert the multiple-inclusion guards in your header files.  For example:
```

#ifndef LINKED_LIST_H
#define LINKED_LIST_H

template <typename T>
class LinkedList
{
...
};

#include "LinkedList.impl"

#endif

```

Aside from that, you will have other compilation errors, but hopefully you can sort that out.  After all, that is the purpose of homework!

P.S.  Node.h is also a template class; you will also need to insert its implementation within the header file.

P.S. #2  In the future, code a little, then compile/test a little.  Don't wait until you are 1000 lines into your code to see if the thing compiles or not.

---

### Post by josephellengar on 2010-11-22
Thank you so much! That was incredibly helpful. And I'm definitely going to be using your advice about incremental development in the future.

If I may ask, why is it necessary to have the code in the header file for these functions? Also, do you know of any way to get Code::Blocks to use syntax highlighting a .impl file?

---

### Post by dwhitney67 on 2010-11-22
> **rossholley said:**
> 
If I may ask, why is it necessary to have the code in the header file for these functions? Also, do you know of any way to get Code::Blocks to use syntax highlighting a .impl file?

I cannot recollect why it is required to implement the template within the header file, but it was a "feature" that was added to the standard about a decade ago.

I do not know anything about Code::Blocks, but I also have the same issue as you when I use vim.  It is not necessary to employ the use of an .impl file; you could implement the templated class below the declaration of the class, or merely insert the code within the class itself.  The latter is what is typically done.  I would suggest this over my previous recommendation, which is more the CORBA-like way of doing things:
```

#ifndef LINKED_LIST_H
#define LINKED_LIST_H

template <typename T>
class LinkedList
{
public:
   LinkedList() : headPtr(0} {}

   ~LinkedList()
   {
      // whatever goes here
   }

   etc.

private:
   ...
};

#endif

```

---

### Post by dribeas on 2010-11-24
> **dwhitney67 said:**
> Fix the following in LinkedListDriver.cpp:
```

LinkedList<int> Ross;

```


Just to extend in a correct answer, this is many times called the "most vexing parsing". The issue is that while it might seem at first look that "LinkedList<int> Ross();" is defining a variable "Ross" of type "LinkedList<int>" initialized by calling the no-argument (default) constructor. The fact is that for the compiler that line of code is actually declaring a function called "Ross" that takes no arguments and returns a "LinkedList<int>". There is some more details in the C++FAQ lite:

[http://www.parashift.com/c++-faq-lite/ctors.html#faq-10.2](http://www.parashift.com/c++-faq-lite/ctors.html#faq-10.2)

---

