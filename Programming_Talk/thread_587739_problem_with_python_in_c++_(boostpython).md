---
title: "problem with python in c++ (boost::python)"
date: 2007-10-23
forum: Programming Talk
---

### Post by aquavitae on 2007-10-23
I'm having trouble using boost::python.  This is my code:
```

int main(int argc, char *argv[]) {
   Py_Initialize();
   dict globals;
   globals["a"] = 4;

   try {
      object result = eval(str(QString("a+3").toStdString()), globals);
   } catch (error_already_set const &) {
      PyErr_Print();
   }
   return 0;
}


```
 and this is the error I get when I run it:
```

Traceback (most recent call last):
  File "<string>", line 1, in <module>
TypeError: 'NoneType' object is unsubscriptable

```
Can anyone help?

---

### Post by kripkenstein on 2008-08-03
I am having the exact same problem... did you perhaps figure it out meanwhile? Or can someone else help us out here?

---

### Post by catchmeifyoutry on 2008-08-03
> **aquavitae said:**
> I'm having trouble using boost::python.  This is my code:
```

int main(int argc, char *argv[]) {
   Py_Initialize();
   dict globals;
   globals["a"] = 4;

   try {
      object result = eval(str(QString("a+3").toStdString()), globals);
   } catch (error_already_set const &) {
      PyErr_Print();
   }
   return 0;
}


```
 and this is the error I get when I run it:
```

Traceback (most recent call last):
  File "<string>", line 1, in <module>
TypeError: 'NoneType' object is unsubscriptable

```
Can anyone help?


Try something like this?
[PHP]
#include <boost/python.hpp>
#include <iostream>

// compiled as: g++ python.cpp -o p -lpython2.5 -lboost_python -I /usr/include/python2.5

using namespace boost::python;

int main(int argc, char *argv[]) 
{
   Py_Initialize();

   try {
      object main_module = import("__main__");
      object main_namespace = main_module.attr("__dict__");

      dict globals;
      globals["a"] = 4;
      object result = eval(str(std::string("a+3")), main_namespace, globals);
      std::cout << extract<int>(result) << std::endl;

   } catch (error_already_set const &) {
      PyErr_Print();
   }
   return 0;
}

[/PHP]

Documentation with examples on:
[http://www.boost.org/doc/libs/1_35_0/libs/python/doc/v2/exec.html](http://www.boost.org/doc/libs/1_35_0/libs/python/doc/v2/exec.html)

For me this works, but I've take out the QString part ... 
cheers.

---

### Post by kripkenstein on 2008-08-03
catchmeifyoutry, your code worked, and I think I figured it out. It seems that calling eval() with three parameters is fine, as you did, but with only two - as in the tutorial examples - doesn't work (even though it compiles fine).

Thanks!

---

### Post by catchmeifyoutry on 2008-08-03
> **kripkenstein said:**
> catchmeifyoutry, your code worked, and I think I figured it out. It seems that calling eval() with three parameters is fine, as you did, but with only two - as in the tutorial examples - doesn't work (even though it compiles fine).

Thanks!

Sweet!
no problem.

---

