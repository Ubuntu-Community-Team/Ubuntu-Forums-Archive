---
title: "C++ Templated Classes with CC compiler"
date: 2008-11-21
forum: Programming Talk
---

### Post by Sneaky07 on 2008-11-21
I am getting a very peculiar error and I'm not sure what is causing the issue. 
I am really sure I have the syntax right and I have tried on multiple machines.  They have both given me the same error.
This is the error I received: 

"linkedlist.cpp", line 38: Error: "}" expected instead of "item". 
"testdivideat.cpp", line 32:     Where: While instantiating 
"linkedListType<int>::divideAt(linkedListType<int>&, const int&)". 
"testdivideat.cpp", line 32:     Where: Instantiated from non-template code. 
1 Error(s) detected. 

**"testdivideat.cpp" is the driver.**

This is how I declare the function as well:
```
template <class Type> 
void linkedListType<Type>::divideAt(linkedListType<Type> &secondList, const Type& item) 
{ 

}
```

The class I use in the driver inherits the linkedListType class.  So basically this function is in a class that is inherited by another class that is used in the driver.  Would that be an issue?  Can you inherit templated classes like regular classes?  (I didn't think it would cause an issue but I could be wrong.)  Has anyone seen this type of error before?

Thanks in advance!

---

