---
title: "type cast questions"
date: 2007-01-06
forum: Programming Talk
---

### Post by cocteau on 2007-01-06
Hi

I've been googling for the answer to this and I'm slightly confused by the answers I'm finding. I'm trying to find a way to do casts correctly in c++. As far as I can tell you can do (from [http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.xlcpp8a.doc/language/ref/cplr188.htm):](http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.xlcpp8a.doc/language/ref/cplr188.htm):)

  float num = 98.76;
  int x1 = (int) num;
  int x2 = int(num);
  int x3 = static_cast<int>(num);

as far as I understand it x1 is c, x2 and x3 is c++. However what's the difference between x2 and x3 and does the use of static_cast imply that there is  a dynamic_cast as well, and if so what's the difference?

---

### Post by gpolo on 2007-01-06
dynamic_cast can be used only with pointers and references to objects. Its purpose is to ensure that the result of the type conversion is a valid complete object of the requested class.

Therefore, dynamic_cast is always successful when we cast a class to one of its base classes:

```

class CBase { };
class CDerived: public CBase { };

CBase b; CBase* pb;
CDerived d; CDerived* pd;

pb = dynamic_cast<CBase*>(&d);     // ok: derived-to-base
pd = dynamic_cast<CDerived*>(&b);  // wrong: base-to-derived

```

The second conversion in this piece of code would produce a compilation error since base-to-derived conversions are not allowed with dynamic_cast unless the base class is polymorphic.

--------

static_cast can perform conversions between pointers to related classes, not only from the derived class to its base, but also from a base class to its derived. This ensures that at least the classes are compatible if the proper object is converted, but no safety check is performed during runtime to check if the object being converted is in fact a full object of the destination type. Therefore, it is up to the programmer to ensure that the conversion is safe. On the other side, the overhead of the type-safety checks of dynamic_cast is avoided.

```

class CBase {};
class CDerived: public CBase {};
CBase * a = new CBase;
CDerived * b = static_cast<CDerived*>(a);

```

This would be valid, although b would point to an incomplete object of the class and could lead to runtime errors if dereferenced.

static_cast can also be used to perform any other non-pointer conversion that could also be performed implicitly, like for example standard conversion between fundamental types:

```

double d=3.14159265;
int i = static_cast<int>(d); 

```

---

### Post by cocteau on 2007-01-06
Thanks for your help.

I'll remember the pointer thing for later, which seems brilliant! I'm going the c++ learn it yourself route and is trying hard not to pick up any lazy programming habits, like ignoring compiler warnings regarding casts. I would prefer to declare my casts explicitly.

---

### Post by gpolo on 2007-01-06
yeh, I did this "learn it yourself" for several languages and with some time (years), experience and reading a lot of documents, articles, etc.. it works better than taking classes ;)

---

### Post by hod139 on 2007-01-06
There are two other c++ casts that haven't been mentioned yet, const_cast and reinterpret_cast.  This page seems to have a nice description of the 4 C++ casts: [http://uwyn.com/resources/uwyn_cpp_coding_standard/x629.html](http://uwyn.com/resources/uwyn_cpp_coding_standard/x629.html)

---

