---
title: "Inheritance and templates in C++"
date: 2007-06-15
forum: Programming Talk
---

### Post by aquavitae on 2007-06-15
Hi

I have a problem with a C++ program I am wrting.  I'm using Qt, but I don't think that has anything to do with the problem.  This is the structure of the program:
```

class Base : public QObject { ... }

template <typename T> class TemplateClass : public Base { ... }

class MyType { ... }

typedef TemplateClass<MyType> ClassMyType;

class InheritedMyType : public ClassMyType { ... }

Base* const some_function(ClassMyType* const var) {
   return var;
}
```

And this is the compile error I'm getting: 
```

error: cannot convert `ClassMyType* const' to `Base* const' in return
```

I think this may have something to do with the template class, but don't know enough about it to know what the problem is, or how to fix it.  Can anyone give me any advice please.

---

### Post by duff on 2007-06-15
Works for me (without QObject)...
```
# cat temp.cpp 

class Base { };

template <typename T> class TemplateClass : public Base { };

class MyType { };

typedef TemplateClass<MyType> ClassMyType;

class InheritedMyType : public ClassMyType { };

Base* const some_function(ClassMyType* const var) {
   return var;
}

# g++ -c temp.cpp 

# echo $?
0

```

---

### Post by aquavitae on 2007-06-15
I think I must have made a typo somewhere then - can't image QObject making any difference.

Thanks for the help!

---

