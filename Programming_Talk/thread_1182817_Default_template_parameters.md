---
title: "Default template parameters"
date: 2009-06-09
forum: Programming Talk
---

### Post by kjohansen on 2009-06-09
EDIT:When I break this down into a small test it seems to work, so it must be some other part of the code I am working on....


I came across:[http://publib.boulder.ibm.com/infocenter/lnxpcomp/v8v101/index.jsp?topic=/com.ibm.xlcpp8l.doc/language/ref/default_args_for_templ_params.htm](http://publib.boulder.ibm.com/infocenter/lnxpcomp/v8v101/index.jsp?topic=/com.ibm.xlcpp8l.doc/language/ref/default_args_for_templ_params.htm)

but this does not appear to be standard compliant and work with g++.  Is there a way to do something like:


[php]
template <class A=int, class B=int>
class Alpha {};

...

Alpha < > instance1;  //this would be like Alpha<int, int>
Alpha <float,float> instance2;
[\php]

in g++?

---

### Post by kjohansen on 2009-06-09
Problem: I was modifying an exisiting class that had a header and an implementation file.  Template classes cannot have separate implementation files...

---

### Post by dwhitney67 on 2009-06-09
> **kjohansen said:**
> Problem: I was modifying an exisiting class that had a header and an implementation file.  Template classes cannot have separate implementation files...
They can, but the implementation file cannot be compiled separately; it must be compiled with the header file.

For instance, here's a sample header file:
```

#ifndef FOO_H
#define FOO_H

template <typename T>
class Foo
{
public:
  Foo(T& d);

  T getData() const;

private:
  T m_data;
};

#include "FooImpl.cpp"

#endif

```

Then the implementation file:
```

template <typename T>
Foo::Foo(T& d) : m_data(d)
{
}

template <typename T>
T Foo::getData() const
{
  return m_data;
}

```

Note that the implementation file does not need to include the header file it implements.

Also note that this file should not be compiled alone.  Only the file(s) that include Foo.h need to be compiled.

P.S.  Certain Makefiles use a wildcard in their statement(s) to find source files (i.e. those ending in .cpp); it might be in ones best interest not to name their template implementation file with the .cpp extension, but instead with a .impl extension.

---

