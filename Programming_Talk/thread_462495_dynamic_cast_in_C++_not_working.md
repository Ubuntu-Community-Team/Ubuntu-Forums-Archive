---
title: "dynamic_cast in C++ not working"
date: 2007-06-02
forum: Programming Talk
---

### Post by bluedalmatian on 2007-06-02
I've got several classes, call them B, C, D which all inherit from A.

Given a pointer to A

A* aninstance;

I need to check which subclass it points to which Im trying to do like this:

if (  (B* bp = (dynamic_cast<B*>(aninstance))   ) 
{  
			//its an instace of B
}

But the compiler is saying:

 cannot dynamic_cast  aninstance (of type ‘class A*’) to type ‘class B*’ (source type is not polymorphic).

What have I done wrong?

Thanks

---

### Post by duff on 2007-06-02
it won't work unless there is a method in class A that is virtual.

**EDIT**:  Your A destructor should be virtual for sure.

---

### Post by bluedalmatian on 2007-06-05
thanks for that, thats solved it. BUT... when it runs it crashes with the following:

./a.out: relocation error: ./a.out: symbol __dynamic_cast, version libmysqlclient_15 not defined in file libmysqlclient.so.15 with link time reference


I dont see why libmysqlclient is involved here, although my program is linked against it because it accesses a database, the dynamic casts are for very simple classes that ive written (just one attribute with a getter method, attribute is nothing more exotic than an int or c++ string)

any suggestions would be appreciated.

thanks

---

