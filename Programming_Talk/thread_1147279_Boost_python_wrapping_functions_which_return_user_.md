---
title: "Boost python wrapping functions which return user defined types"
date: 2009-05-03
forum: Programming Talk
---

### Post by hessiess on 2009-05-03
How can you wrap a class which returns an instance of another class with boost python?

for example:
```

#include <boost/python.hpp>

struct a
{
    int x;
};

struct b
{
    a geta()
    {
	a ins_a;
	ins_a.x = 3;
	return ins_a;
    }
};

BOOST_PYTHON_MODULE(test)
{
    using namespace boost::python;

    class_<a>("a");

    class_<b>("b")
	.def("geta", &b::geta);
}

```

which can be compiled fine with:
```

g++ test.cpp -lboost_python -lpython2.5 -fPIC -I /usr/include/python2.5/ -o test.so -shared

```

and loaded into python:
```

>>> import test
>>> b = test.b
>>> b.geta()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unbound method Boost.Python.function object must be called with b instance as first argument (got nothing instead)

```

But python gives an error when the function is ran.

---

### Post by Reiger on 2009-05-03
Without much knowledge of either Python or C or C++ but with deadly dose of self-confidence :) ... 

Isn't there some convention whereby Python implicitly passes around a lot of self arguments? That is to say:

"object.method(param)" is expanded to "object.method(self,param)" ?

From the almighty www with the help of google:
[quote="http://linuxgazette.net/issue56/orr.html"]Note that __init__ is defined with an extra first argument, self. But we don't specify self when we call the method. All Python methods work like this. self is in fact the instance itself, and Python supplies it behind the scenes. You need self because it's the only way the method can access the instance's attributes and other methods. Inside the method, self.rooms means the instance's attribute rooms, but rooms means the local variable rooms. Local variables, of course, vanish when the method ends. Python's use of self is parallelled in Perl and other OO languages as well. 

Michael didn't tell you, but C++ has a this pointer which works like Python's self. However, in C++ you don't have to type this->house if there is no local variable house, and you never type this on a method definition line. In other words, C++ (and Java) do the same thing as Python and Perl; they just hide it from the programmer.[/quote]

Sounds like you must craft your C++ method to pass a pointer to its class (some self) to me?

---

### Post by dwhitney67 on 2009-05-03
Or maybe you need to construct a b instance in python?  I do not have any practical experience with python.

```

b = test.b()
a = b.geta()

```

P.S.  I added the following:
```

struct a
{
    int getx() const { return x; }
    ...
}

...

    class_<a>("a")
        .def("getx", &a::getx);

...

```

Tested with:
```

python
>>> import test
>>> b = test.b()
>>> a = b.geta()
>>> a.getx()
3
>>>

```

---

### Post by hessiess on 2009-05-03
Thanks, I guess that boost.python doesn't like classes with no methods.

---

