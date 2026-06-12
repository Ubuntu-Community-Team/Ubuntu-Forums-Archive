---
title: "Help needed with boost python.. Plz.."
date: 2009-11-20
forum: Programming Talk
---

### Post by python.noob on 2009-11-20
Hai friends,
              I've installed boost python from ubuntu 9.04 repositories.. I've successfully run the 
**[SIZE=1][Build a Simple Program Using Boost]("http://www.boost.org/doc/libs/1_41_0/more/getting_started/unix-variants.html#id24")[/SIZE]**

from the tutorial [http://www.boost.org/doc/libs/1_41_0/more/getting_started/unix-variants.html](http://www.boost.org/doc/libs/1_41_0/more/getting_started/unix-variants.html) . So i ensured that boost python is installed in my system.. 
But for the program below
```
#include <string>

namespace { // Avoid cluttering the global namespace.

  // A couple of simple C++ functions that we want to expose to Python.
  std::string greet() { return "hello, world"; }
  int square(int number) { return number * number; }
}
#include <boost/python.hpp>
using namespace boost::python;

BOOST_PYTHON_MODULE(getting_started1)
{
    // Add regular functions to the module.
    def("greet", greet);
    def("square", square);
}
```
when i tried to execute the first step from the below two steps to create a shared library
```
g++ -c -fPIC hello.cpp -o hello.o
g++ -shared -Wl,-soname,libhello.so -o libhello.so  hello.o
```
(i hope these are the steps. Am i right?)

i got the following error
```
In file included from /usr/include/boost/python/detail/prefix.hpp:13,
                 from /usr/include/boost/python/args.hpp:8,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/wrap_python.hpp:50:23: error: pyconfig.h: No such file or directory
/usr/include/boost/python/detail/wrap_python.hpp:75:24: error: patchlevel.h: No such file or directory
/usr/include/boost/python/detail/wrap_python.hpp:78:2: error: #error Python 2.2 or higher is required for this version of Boost.Python.
/usr/include/boost/python/detail/wrap_python.hpp:142:21: error: Python.h: No such file or directory
In file included from /usr/include/boost/python/cast.hpp:13,
                 from /usr/include/boost/python/handle.hpp:10,
                 from /usr/include/boost/python/args_fwd.hpp:10,
                 from /usr/include/boost/python/args.hpp:10,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/base_type_traits.hpp:24: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/base_type_traits.hpp:24: error: template argument 1 is invalid
/usr/include/boost/python/base_type_traits.hpp:30: error: ‘PyTypeObject’ was not declared in this scope
/usr/include/boost/python/base_type_traits.hpp:30: error: template argument 1 is invalid
/usr/include/boost/python/base_type_traits.hpp:36: error: ‘PyMethodObject’ was not declared in this scope
/usr/include/boost/python/base_type_traits.hpp:36: error: template argument 1 is invalid
In file included from /usr/include/boost/python/handle.hpp:11,
                 from /usr/include/boost/python/args_fwd.hpp:10,
                 from /usr/include/boost/python/args.hpp:10,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/errors.hpp:51: error: expected constructor, destructor, or type conversion before ‘*’ token
In file included from /usr/include/boost/python/handle.hpp:13,
                 from /usr/include/boost/python/args_fwd.hpp:10,
                 from /usr/include/boost/python/args.hpp:10,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/handle_fwd.hpp:12: error: expected type-specifier before ‘PyObject’
/usr/include/boost/python/handle_fwd.hpp:12: error: expected ‘>’ before ‘PyObject’
In file included from /usr/include/boost/python/handle.hpp:14,
                 from /usr/include/boost/python/args_fwd.hpp:10,
                 from /usr/include/boost/python/args.hpp:10,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/refcount.hpp: In function ‘T* boost::python::incref(T*)’:
/usr/include/boost/python/refcount.hpp:16: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/refcount.hpp: In function ‘T* boost::python::xincref(T*)’:
/usr/include/boost/python/refcount.hpp:23: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/refcount.hpp: In function ‘void boost::python::decref(T*)’:
/usr/include/boost/python/refcount.hpp:30: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/refcount.hpp: In function ‘void boost::python::xdecref(T*)’:
/usr/include/boost/python/refcount.hpp:36: error: ‘PyObject’ was not declared in this scope
In file included from /usr/include/boost/python/args_fwd.hpp:10,
                 from /usr/include/boost/python/args.hpp:10,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/handle.hpp: In constructor ‘boost::python::handle<T>::handle(boost::python::detail::borrowed_reference_t*)’:
/usr/include/boost/python/handle.hpp:130: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/handle.hpp:130: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/handle.hpp: At global scope:
/usr/include/boost/python/handle.hpp:157: error: ‘PyTypeObject’ was not declared in this scope
/usr/include/boost/python/handle.hpp:157: error: template argument 1 is invalid
/usr/include/boost/python/handle.hpp:157: error: invalid type in declaration before ‘;’ token
/usr/include/boost/python/handle.hpp:256: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/python/args.hpp:10,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/args_fwd.hpp:26: error: template argument 1 is invalid
In file included from /usr/include/boost/python/object/pointer_holder.hpp:14,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/instance_holder.hpp:34: error: ‘PyObject’ has not been declared
/usr/include/boost/python/instance_holder.hpp:41: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/instance_holder.hpp:45: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/python/object/pointer_holder.hpp:21,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/wrapper_base.hpp:21: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/wrapper_base.hpp:23: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/wrapper_base.hpp:30: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/wrapper_base.hpp:34: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/wrapper_base.hpp:43: error: ‘PyObject’ has not been declared
/usr/include/boost/python/detail/wrapper_base.hpp:44: error: ‘PyObject’ is neither function nor member function; cannot be declared friend
/usr/include/boost/python/detail/wrapper_base.hpp:44: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/detail/wrapper_base.hpp:49: error: ‘PyTypeObject’ has not been declared
/usr/include/boost/python/detail/wrapper_base.hpp:55: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/detail/wrapper_base.hpp: In constructor ‘boost::python::detail::wrapper_base::wrapper_base()’:
/usr/include/boost/python/detail/wrapper_base.hpp:46: error: class ‘boost::python::detail::wrapper_base’ does not have any field named ‘m_self’
/usr/include/boost/python/detail/wrapper_base.hpp: At global scope:
/usr/include/boost/python/detail/wrapper_base.hpp:61: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/wrapper_base.hpp:71: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/wrapper_base.hpp:77: error: variable or field ‘initialize_wrapper’ declared void
/usr/include/boost/python/detail/wrapper_base.hpp:77: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/detail/wrapper_base.hpp:77: error: ‘self’ was not declared in this scope
/usr/include/boost/python/detail/wrapper_base.hpp:77: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/detail/wrapper_base.hpp:77: error: ‘w’ was not declared in this scope
/usr/include/boost/python/detail/wrapper_base.hpp:82: error: variable or field ‘initialize_wrapper’ declared void
/usr/include/boost/python/detail/wrapper_base.hpp:82: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/detail/wrapper_base.hpp:82: error: expected primary-expression before ‘,’ token
/usr/include/boost/python/detail/wrapper_base.hpp:82: error: expected primary-expression before ‘...’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:47,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/object/pointer_holder.hpp:63,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:176: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:47,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/object/pointer_holder.hpp:99,
                 from /usr/include/boost/python/to_python_indirect.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/pointer_holder.hpp:199: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/python/object/make_instance.hpp:9,
                 from /usr/include/boost/python/object/make_ptr_instance.hpp:8,
                 from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/instance.hpp:23: error: ‘PyObject_VAR_HEAD’ does not name a type
/usr/include/boost/python/object/instance.hpp:25: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/python/converter/registry.hpp:8,
                 from /usr/include/boost/python/converter/registered.hpp:8,
                 from /usr/include/boost/python/object/make_instance.hpp:10,
                 from /usr/include/boost/python/object/make_ptr_instance.hpp:8,
                 from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/to_python_function_type.hpp:15: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/python/converter/rvalue_from_python_data.hpp:8,
                 from /usr/include/boost/python/converter/registry.hpp:9,
                 from /usr/include/boost/python/converter/registered.hpp:8,
                 from /usr/include/boost/python/object/make_instance.hpp:10,
                 from /usr/include/boost/python/object/make_ptr_instance.hpp:8,
                 from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/constructor_function.hpp:13: error: typedef ‘boost::python::converter::constructor_function’ is initialized (use __typeof__ instead)
/usr/include/boost/python/converter/constructor_function.hpp:13: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/constructor_function.hpp:13: error: ‘source’ was not declared in this scope
/usr/include/boost/python/converter/constructor_function.hpp:13: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/converter/constructor_function.hpp:13: error: expected primary-expression before ‘)’ token
In file included from /usr/include/boost/python/converter/registry.hpp:9,
                 from /usr/include/boost/python/converter/registered.hpp:8,
                 from /usr/include/boost/python/object/make_instance.hpp:10,
                 from /usr/include/boost/python/object/make_ptr_instance.hpp:8,
                 from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/rvalue_from_python_data.hpp:65: error: ‘constructor_function’ does not name a type
In file included from /usr/include/boost/python/converter/registry.hpp:11,
                 from /usr/include/boost/python/converter/registered.hpp:8,
                 from /usr/include/boost/python/object/make_instance.hpp:10,
                 from /usr/include/boost/python/object/make_ptr_instance.hpp:8,
                 from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/convertible_function.hpp:10: error: typedef ‘boost::python::converter::convertible_function’ is initialized (use __typeof__ instead)
/usr/include/boost/python/converter/convertible_function.hpp:10: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/convertible_function.hpp:10: error: expected primary-expression before ‘)’ token
In file included from /usr/include/boost/python/converter/registered.hpp:8,
                 from /usr/include/boost/python/object/make_instance.hpp:10,
                 from /usr/include/boost/python/object/make_ptr_instance.hpp:8,
                 from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/registry.hpp:30: error: variable or field ‘insert’ declared void
/usr/include/boost/python/converter/registry.hpp:30: error: ‘to_python_function_t’ was not declared in this scope
/usr/include/boost/python/converter/registry.hpp:30: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/converter/registry.hpp:33: error: expected ‘,’ or ‘...’ before ‘(’ token
/usr/include/boost/python/converter/registry.hpp:37: error: variable or field ‘insert’ declared void
/usr/include/boost/python/converter/registry.hpp:37: error: ‘convertible_function’ was not declared in this scope
/usr/include/boost/python/converter/registry.hpp:38: error: ‘constructor_function’ was not declared in this scope
/usr/include/boost/python/converter/registry.hpp:40: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/converter/registry.hpp:45: error: variable or field ‘push_back’ declared void
/usr/include/boost/python/converter/registry.hpp:45: error: ‘convertible_function’ was not declared in this scope
/usr/include/boost/python/converter/registry.hpp:46: error: ‘constructor_function’ was not declared in this scope
/usr/include/boost/python/converter/registry.hpp:48: error: expected primary-expression before ‘)’ token
In file included from /usr/include/boost/python/converter/registered.hpp:9,
                 from /usr/include/boost/python/object/make_instance.hpp:10,
                 from /usr/include/boost/python/object/make_ptr_instance.hpp:8,
                 from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/registrations.hpp:22: error: ‘convertible_function’ does not name a type
/usr/include/boost/python/converter/registrations.hpp:28: error: ‘convertible_function’ does not name a type
/usr/include/boost/python/converter/registrations.hpp:29: error: ‘constructor_function’ does not name a type
/usr/include/boost/python/converter/registrations.hpp:39: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/registrations.hpp:43: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/registrations.hpp:55: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/registrations.hpp:58: error: ‘to_python_function_t’ does not name a type
/usr/include/boost/python/converter/registrations.hpp: In constructor ‘boost::python::converter::registration::registration(boost::python::type_info, bool)’:
/usr/include/boost/python/converter/registrations.hpp:77: error: class ‘boost::python::converter::registration’ does not have any field named ‘m_class_object’
/usr/include/boost/python/converter/registrations.hpp:78: error: class ‘boost::python::converter::registration’ does not have any field named ‘m_to_python’
In file included from /usr/include/boost/python/object/make_instance.hpp:11,
                 from /usr/include/boost/python/object/make_ptr_instance.hpp:8,
                 from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/decref_guard.hpp: At global scope:
/usr/include/boost/python/detail/decref_guard.hpp:12: error: expected `)' before ‘*’ token
/usr/include/boost/python/detail/decref_guard.hpp:16: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/detail/decref_guard.hpp: In destructor ‘boost::python::detail::decref_guard::~decref_guard()’:
/usr/include/boost/python/detail/decref_guard.hpp:13: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/detail/decref_guard.hpp:13: error: ‘Py_XDECREF’ was not declared in this scope
/usr/include/boost/python/detail/decref_guard.hpp: In member function ‘void boost::python::detail::decref_guard::cancel()’:
/usr/include/boost/python/detail/decref_guard.hpp:14: error: ‘obj’ was not declared in this scope
In file included from /usr/include/boost/python/object/make_instance.hpp:12,
                 from /usr/include/boost/python/object/make_ptr_instance.hpp:8,
                 from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/none.hpp: At global scope:
/usr/include/boost/python/detail/none.hpp:16: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/python/object/make_ptr_instance.hpp:8,
                 from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/make_instance.hpp:22: error: expected initializer before ‘*’ token
/usr/include/boost/python/object/make_instance.hpp:61: error: expected initializer before ‘*’ token
/usr/include/boost/python/object/make_instance.hpp:66: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/python/to_python_indirect.hpp:11,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/make_ptr_instance.hpp:22: error: ‘PyObject’ has not been declared
/usr/include/boost/python/object/make_ptr_instance.hpp:28: error: expected initializer before ‘*’ token
/usr/include/boost/python/object/make_ptr_instance.hpp:35: error: expected initializer before ‘*’ token
/usr/include/boost/python/object/make_ptr_instance.hpp:49: error: expected initializer before ‘*’ token
/usr/include/boost/python/object/make_ptr_instance.hpp:58: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/python/converter/arg_to_python.hpp:10,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/to_python_indirect.hpp:34: error: expected initializer before ‘*’ token
/usr/include/boost/python/to_python_indirect.hpp:42: error: expected initializer before ‘*’ token
/usr/include/boost/python/to_python_indirect.hpp:52: error: expected initializer before ‘*’ token
/usr/include/boost/python/to_python_indirect.hpp:72: error: expected initializer before ‘*’ token
/usr/include/boost/python/to_python_indirect.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/python/converter/arg_to_python.hpp:14,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/arg_to_python_base.hpp:17: error: template argument 1 is invalid
In file included from /usr/include/boost/python/converter/shared_ptr_to_python.hpp:9,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:15,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/shared_ptr_deleter.hpp:12: error: template argument 1 is invalid
/usr/include/boost/python/converter/shared_ptr_deleter.hpp:17: error: template argument 1 is invalid
In file included from /usr/include/boost/python/converter/arg_to_python.hpp:15,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/shared_ptr_to_python.hpp:16: error: expected constructor, destructor, or type conversion before ‘*’ token
In file included from /usr/include/boost/python/converter/arg_to_python.hpp:17,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/builtin_converters.hpp:27: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:28: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:29: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:30: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:98: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:98: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:98: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:98: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:98: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:98: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:98: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<bool>::arg_to_python(const bool&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:98: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:98: error: ‘::PyInt_FromLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<signed char>::arg_to_python(const signed char&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: ‘::PyInt_FromLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<unsigned char>::arg_to_python(const unsigned char&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: ‘::PyLong_FromUnsignedLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp:102: error: ‘::PyInt_FromLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<short int>::arg_to_python(const short int&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: ‘::PyInt_FromLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<short unsigned int>::arg_to_python(const short unsigned int&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: ‘::PyLong_FromUnsignedLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp:104: error: ‘::PyInt_FromLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<int>::arg_to_python(const int&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: ‘::PyInt_FromLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<unsigned int>::arg_to_python(const unsigned int&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: ‘::PyLong_FromUnsignedLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp:105: error: ‘::PyInt_FromLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<long int>::arg_to_python(const long int&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: ‘::PyInt_FromLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<long unsigned int>::arg_to_python(const long unsigned int&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: ‘::PyLong_FromUnsignedLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp:106: error: ‘::PyInt_FromLong’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:117: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:117: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:117: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:117: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:117: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:117: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:117: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<char>::arg_to_python(const char&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:117: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:117: error: ‘do_return_to_python’ is not a member of ‘boost::python::converter’
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:118: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:118: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:118: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:118: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:118: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:118: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:118: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<const char*>::arg_to_python(const char* const&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:118: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:118: error: ‘do_return_to_python’ is not a member of ‘boost::python::converter’
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:119: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:119: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:119: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:119: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:119: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:119: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:119: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >::arg_to_python(const std::string&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:119: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:119: error: ‘::PyString_FromStringAndSize’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:123: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:123: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:123: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:123: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:123: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:123: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:123: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<float>::arg_to_python(const float&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:123: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:123: error: ‘::PyFloat_FromDouble’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:124: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:124: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:124: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:124: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:124: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:124: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:124: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<double>::arg_to_python(const double&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:124: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:124: error: ‘::PyFloat_FromDouble’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:125: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:125: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:125: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:125: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:125: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:125: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:125: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<long double>::arg_to_python(const long double&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:125: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:125: error: ‘::PyFloat_FromDouble’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:126: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/builtin_converters.hpp:126: error: `&' cannot appear in a constant-expression
/usr/include/boost/python/converter/builtin_converters.hpp:126: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:126: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/builtin_converters.hpp:126: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:127: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:127: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:127: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:127: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:127: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:127: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:127: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<std::complex<float> >::arg_to_python(const std::complex<float>&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:127: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:127: error: ‘::PyComplex_FromDoubles’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:128: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:128: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:128: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:128: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:128: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:128: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:128: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<std::complex<double> >::arg_to_python(const std::complex<double>&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:128: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:128: error: ‘::PyComplex_FromDoubles’ has not been declared
/usr/include/boost/python/converter/builtin_converters.hpp: At global scope:
/usr/include/boost/python/converter/builtin_converters.hpp:129: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:129: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:129: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:129: error: ‘PyObject’ declared as an ‘inline’ field
/usr/include/boost/python/converter/builtin_converters.hpp:129: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/builtin_converters.hpp:129: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/builtin_converters.hpp:129: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp: In constructor ‘boost::python::converter::arg_to_python<std::complex<long double> >::arg_to_python(const std::complex<long double>&)’:
/usr/include/boost/python/converter/builtin_converters.hpp:129: error: template argument 1 is invalid
/usr/include/boost/python/converter/builtin_converters.hpp:129: error: ‘::PyComplex_FromDoubles’ has not been declared
In file included from /usr/include/boost/python/converter/pyobject_traits.hpp:9,
                 from /usr/include/boost/python/converter/object_manager.hpp:10,
                 from /usr/include/boost/python/to_python_value.hpp:16,
                 from /usr/include/boost/python/detail/invoke.hpp:21,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/pyobject_type.hpp: At global scope:
/usr/include/boost/python/converter/pyobject_type.hpp:12: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/boost/python/converter/pyobject_type.hpp:16: error: ‘PyTypeObject’ has not been declared
/usr/include/boost/python/converter/pyobject_type.hpp:19: error: ‘PyObject’ has not been declared
/usr/include/boost/python/converter/pyobject_type.hpp:24: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/converter/pyobject_type.hpp:30: error: expected `;' before ‘}’ token
/usr/include/boost/python/converter/pyobject_type.hpp: In static member function ‘static bool boost::python::converter::pyobject_type<Object, pytype>::check(int*)’:
/usr/include/boost/python/converter/pyobject_type.hpp:21: error: ‘::PyObject_IsInstance’ has not been declared
/usr/include/boost/python/converter/pyobject_type.hpp:21: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_type.hpp:21: error: expected primary-expression before ‘)’ token
In file included from /usr/include/boost/python/converter/object_manager.hpp:10,
                 from /usr/include/boost/python/to_python_value.hpp:16,
                 from /usr/include/boost/python/detail/invoke.hpp:21,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/pyobject_traits.hpp: At global scope:
/usr/include/boost/python/converter/pyobject_traits.hpp:16: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:16: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:32: error: ‘PyTypeObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:32: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:32: error: ‘PyTypeObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:32: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:32: error: template argument 2 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:33: error: ‘PyListObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:33: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:33: error: ‘PyListObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:33: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:33: error: template argument 2 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:34: error: ‘PyIntObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:34: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:34: error: ‘PyIntObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:34: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:34: error: template argument 2 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:35: error: ‘PyLongObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:35: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:35: error: ‘PyLongObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:35: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:35: error: template argument 2 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:36: error: ‘PyDictObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:36: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:36: error: ‘PyDictObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:36: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:36: error: template argument 2 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:37: error: ‘PyTupleObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:37: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:37: error: ‘PyTupleObject’ was not declared in this scope
/usr/include/boost/python/converter/pyobject_traits.hpp:37: error: template argument 1 is invalid
/usr/include/boost/python/converter/pyobject_traits.hpp:37: error: template argument 2 is invalid
In file included from /usr/include/boost/python/to_python_value.hpp:16,
                 from /usr/include/boost/python/detail/invoke.hpp:21,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/object_manager.hpp:89: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/converter/object_manager.hpp:93: error: expected `;' before ‘}’ token
In file included from /usr/include/boost/python/detail/invoke.hpp:21,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/to_python_value.hpp:37: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/to_python_value.hpp:51: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/to_python_value.hpp:64: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/to_python_value.hpp:96: error: expected initializer before ‘*’ token
/usr/include/boost/python/to_python_value.hpp:107: error: expected initializer before ‘*’ token
/usr/include/boost/python/to_python_value.hpp:116: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:47,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/detail/invoke.hpp:63,
                 from /usr/include/boost/python/detail/caller.hpp:14,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/invoke.hpp:73: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:79: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:86: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/invoke.hpp:92: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/python/converter/arg_from_python.hpp:9,
                 from /usr/include/boost/python/arg_from_python.hpp:9,
                 from /usr/include/boost/python/detail/caller.hpp:18,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/from_python.hpp:17: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:17: error: ‘source’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:17: error: expected primary-expression before ‘const’
/usr/include/boost/python/converter/from_python.hpp:17: error: initializer expression list treated as compound expression
/usr/include/boost/python/converter/from_python.hpp:20: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:20: error: ‘source’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:20: error: expected primary-expression before ‘const’
/usr/include/boost/python/converter/from_python.hpp:20: error: initializer expression list treated as compound expression
/usr/include/boost/python/converter/from_python.hpp:23: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:23: error: ‘source’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:23: error: expected primary-expression before ‘const’
/usr/include/boost/python/converter/from_python.hpp:26: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:26: error: ‘source’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:26: error: expected primary-expression before ‘&’ token
/usr/include/boost/python/converter/from_python.hpp:26: error: expected primary-expression before ‘,’ token
/usr/include/boost/python/converter/from_python.hpp:26: error: expected primary-expression before ‘const’
/usr/include/boost/python/converter/from_python.hpp:26: error: initializer expression list treated as compound expression
/usr/include/boost/python/converter/from_python.hpp:29: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:29: error: expected primary-expression before ‘,’ token
/usr/include/boost/python/converter/from_python.hpp:29: error: expected primary-expression before ‘&’ token
/usr/include/boost/python/converter/from_python.hpp:29: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/converter/from_python.hpp:29: error: initializer expression list treated as compound expression
/usr/include/boost/python/converter/from_python.hpp:31: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:31: error: expected primary-expression before ‘,’ token
/usr/include/boost/python/converter/from_python.hpp:31: error: expected primary-expression before ‘const’
/usr/include/boost/python/converter/from_python.hpp:31: error: initializer expression list treated as compound expression
/usr/include/boost/python/converter/from_python.hpp:32: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:32: error: expected primary-expression before ‘,’ token
/usr/include/boost/python/converter/from_python.hpp:32: error: expected primary-expression before ‘const’
/usr/include/boost/python/converter/from_python.hpp:32: error: initializer expression list treated as compound expression
/usr/include/boost/python/converter/from_python.hpp:34: error: variable or field ‘void_result_from_python’ declared void
/usr/include/boost/python/converter/from_python.hpp:34: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:34: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/converter/from_python.hpp:36: error: variable or field ‘throw_no_pointer_from_python’ declared void
/usr/include/boost/python/converter/from_python.hpp:36: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:36: error: expected primary-expression before ‘,’ token
/usr/include/boost/python/converter/from_python.hpp:36: error: expected primary-expression before ‘const’
/usr/include/boost/python/converter/from_python.hpp:37: error: variable or field ‘throw_no_reference_from_python’ declared void
/usr/include/boost/python/converter/from_python.hpp:37: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/from_python.hpp:37: error: expected primary-expression before ‘,’ token
/usr/include/boost/python/converter/from_python.hpp:37: error: expected primary-expression before ‘const’
In file included from /usr/include/boost/python/converter/arg_from_python.hpp:24,
                 from /usr/include/boost/python/arg_from_python.hpp:9,
                 from /usr/include/boost/python/detail/caller.hpp:18,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/back_reference.hpp:24: error: expected `)' before ‘*’ token
/usr/include/boost/python/back_reference.hpp:82: error: expected constructor, destructor, or type conversion before ‘(’ token
In file included from /usr/include/boost/python/converter/arg_from_python.hpp:26,
                 from /usr/include/boost/python/arg_from_python.hpp:9,
                 from /usr/include/boost/python/detail/caller.hpp:18,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:27: error: expected `)' before ‘*’ token
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:31: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:48: error: expected `)' before ‘*’ token
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:61: error: ‘boost::python::converter::object_manager_value_arg_from_python<T>::object_manager_value_arg_from_python’ declared as an ‘inline’ variable
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:61: error: ‘int boost::python::converter::object_manager_value_arg_from_python<T>::object_manager_value_arg_from_python’ is not a static member of ‘struct boost::python::converter::object_manager_value_arg_from_python<T>’
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:61: error: template definition of non-template ‘int boost::python::converter::object_manager_value_arg_from_python<T>::object_manager_value_arg_from_python’
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:61: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:61: error: ‘x’ was not declared in this scope
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp: In member function ‘bool boost::python::converter::object_manager_value_arg_from_python<T>::convertible() const’:
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:69: error: ‘m_source’ was not declared in this scope
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp: In member function ‘T boost::python::converter::object_manager_value_arg_from_python<T>::operator()() const’:
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:75: error: ‘m_source’ was not declared in this scope
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp: At global scope:
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:79: error: ‘boost::python::converter::object_manager_ref_arg_from_python<Ref>::object_manager_ref_arg_from_python’ declared as an ‘inline’ variable
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:79: error: ‘int boost::python::converter::object_manager_ref_arg_from_python<Ref>::object_manager_ref_arg_from_python’ is not a static member of ‘struct boost::python::converter::object_manager_ref_arg_from_python<Ref>’
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:79: error: template definition of non-template ‘int boost::python::converter::object_manager_ref_arg_from_python<Ref>::object_manager_ref_arg_from_python’
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:79: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp:79: error: ‘x’ was not declared in this scope
In file included from /usr/include/boost/python/arg_from_python.hpp:9,
                 from /usr/include/boost/python/detail/caller.hpp:18,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/arg_from_python.hpp:50: error: expected `)' before ‘*’ token
/usr/include/boost/python/converter/arg_from_python.hpp:80: error: expected `)' before ‘*’ token
/usr/include/boost/python/converter/arg_from_python.hpp:90: error: expected `)' before ‘*’ token
/usr/include/boost/python/converter/arg_from_python.hpp:115: error: expected `)' before ‘*’ token
/usr/include/boost/python/converter/arg_from_python.hpp:125: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/arg_from_python.hpp:139: error: expected `)' before ‘*’ token
/usr/include/boost/python/converter/arg_from_python.hpp:143: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/arg_from_python.hpp:239: error: ‘boost::python::converter::pointer_cref_arg_from_python<T>::pointer_cref_arg_from_python’ declared as an ‘inline’ variable
/usr/include/boost/python/converter/arg_from_python.hpp:239: error: ‘int boost::python::converter::pointer_cref_arg_from_python<T>::pointer_cref_arg_from_python’ is not a static member of ‘struct boost::python::converter::pointer_cref_arg_from_python<T>’
/usr/include/boost/python/converter/arg_from_python.hpp:239: error: template definition of non-template ‘int boost::python::converter::pointer_cref_arg_from_python<T>::pointer_cref_arg_from_python’
/usr/include/boost/python/converter/arg_from_python.hpp:239: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp:239: error: ‘p’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp: In member function ‘T boost::python::converter::pointer_cref_arg_from_python<T>::operator()() const’:
/usr/include/boost/python/converter/arg_from_python.hpp:258: error: ‘Py_None’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp: At global scope:
/usr/include/boost/python/converter/arg_from_python.hpp:267: error: ‘boost::python::converter::pointer_arg_from_python<T>::pointer_arg_from_python’ declared as an ‘inline’ variable
/usr/include/boost/python/converter/arg_from_python.hpp:267: error: ‘int boost::python::converter::pointer_arg_from_python<T>::pointer_arg_from_python’ is not a static member of ‘struct boost::python::converter::pointer_arg_from_python<T>’
/usr/include/boost/python/converter/arg_from_python.hpp:267: error: template definition of non-template ‘int boost::python::converter::pointer_arg_from_python<T>::pointer_arg_from_python’
/usr/include/boost/python/converter/arg_from_python.hpp:267: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp:267: error: ‘p’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp: In member function ‘T boost::python::converter::pointer_arg_from_python<T>::operator()() const’:
/usr/include/boost/python/converter/arg_from_python.hpp:276: error: ‘Py_None’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp: At global scope:
/usr/include/boost/python/converter/arg_from_python.hpp:282: error: ‘boost::python::converter::reference_arg_from_python<T>::reference_arg_from_python’ declared as an ‘inline’ variable
/usr/include/boost/python/converter/arg_from_python.hpp:282: error: ‘int boost::python::converter::reference_arg_from_python<T>::reference_arg_from_python’ is not a static member of ‘struct boost::python::converter::reference_arg_from_python<T>’
/usr/include/boost/python/converter/arg_from_python.hpp:282: error: template definition of non-template ‘int boost::python::converter::reference_arg_from_python<T>::reference_arg_from_python’
/usr/include/boost/python/converter/arg_from_python.hpp:282: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp:282: error: ‘p’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp:297: error: ‘boost::python::converter::arg_rvalue_from_python<T>::arg_rvalue_from_python’ declared as an ‘inline’ variable
/usr/include/boost/python/converter/arg_from_python.hpp:297: error: ‘int boost::python::converter::arg_rvalue_from_python<T>::arg_rvalue_from_python’ is not a static member of ‘struct boost::python::converter::arg_rvalue_from_python<T>’
/usr/include/boost/python/converter/arg_from_python.hpp:297: error: template definition of non-template ‘int boost::python::converter::arg_rvalue_from_python<T>::arg_rvalue_from_python’
/usr/include/boost/python/converter/arg_from_python.hpp:297: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp:297: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp: In member function ‘typename boost::python::converter::arg_rvalue_from_python<T>::result_type boost::python::converter::arg_rvalue_from_python<T>::operator()()’:
/usr/include/boost/python/converter/arg_from_python.hpp:314: error: ‘m_source’ was not declared in this scope
/usr/include/boost/python/converter/arg_from_python.hpp: At global scope:
/usr/include/boost/python/converter/arg_from_python.hpp:322: error: expected constructor, destructor, or type conversion before ‘(’ token
/usr/include/boost/python/converter/arg_from_python.hpp: In member function ‘T boost::python::converter::back_reference_arg_from_python<T>::operator()()’:
/usr/include/boost/python/converter/arg_from_python.hpp:331: error: ‘m_source’ was not declared in this scope
In file included from /usr/include/boost/python/detail/caller.hpp:18,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/arg_from_python.hpp: At global scope:
/usr/include/boost/python/arg_from_python.hpp:37: error: expected `)' before ‘*’ token
/usr/include/boost/python/arg_from_python.hpp:42: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/arg_from_python.hpp:42: error: template argument 1 is invalid
/usr/include/boost/python/arg_from_python.hpp:54: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/arg_from_python.hpp:54: error: template argument 1 is invalid
/usr/include/boost/python/arg_from_python.hpp:69: error: ‘boost::python::arg_from_python<T>::arg_from_python’ declared as an ‘inline’ variable
/usr/include/boost/python/arg_from_python.hpp:69: error: ‘int boost::python::arg_from_python<T>::arg_from_python’ is not a static member of ‘struct boost::python::arg_from_python<T>’
/usr/include/boost/python/arg_from_python.hpp:69: error: template definition of non-template ‘int boost::python::arg_from_python<T>::arg_from_python’
/usr/include/boost/python/arg_from_python.hpp:69: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/arg_from_python.hpp:69: error: ‘source’ was not declared in this scope
In file included from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:45: error: expected initializer before ‘*’ token
/usr/include/boost/python/detail/caller.hpp:50: error: ‘boost::python::detail::arity’ declared as an ‘inline’ variable
/usr/include/boost/python/detail/caller.hpp:50: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/detail/caller.hpp:50: error: expected primary-expression before ‘const’
/usr/include/boost/python/detail/caller.hpp:51: error: expected ‘,’ or ‘;’ before ‘{’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:47,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:127,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:172: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:127,
                 from /usr/include/boost/python/detail/caller.hpp:110,
                 from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:204: error: expected `;' before ‘static’
In file included from /usr/include/boost/python/object/function_handle.hpp:8,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/detail/caller.hpp:150: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/python/object/function_handle.hpp:9,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/default_call_policies.hpp:45: error: expected initializer before ‘*’ token
/usr/include/boost/python/default_call_policies.hpp:51: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/default_call_policies.hpp:77: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/default_call_policies.hpp:77: error: template argument 1 is invalid
/usr/include/boost/python/default_call_policies.hpp:78: error: explicit specialization of non-template ‘boost::python::<anonymous struct>’
/usr/include/boost/python/default_call_policies.hpp:79: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/default_call_policies.hpp:79: error: template argument 1 is invalid
/usr/include/boost/python/default_call_policies.hpp:80: error: abstract declarator ‘boost::python::<anonymous struct>’ used as declaration
In file included from /usr/include/boost/python/object/function_handle.hpp:10,
                 from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/py_function.hpp:23: error: ‘PyObject’ declared as a ‘virtual’ field
/usr/include/boost/python/object/py_function.hpp:23: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object/py_function.hpp:36: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object/py_function.hpp:41: error: expected `;' before ‘virtual’
/usr/include/boost/python/object/py_function.hpp:62: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object/py_function.hpp:67: error: expected `;' before ‘virtual’
/usr/include/boost/python/object/py_function.hpp:90: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object/py_function.hpp:95: error: expected `;' before ‘virtual’
/usr/include/boost/python/object/py_function.hpp:137: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object/py_function.hpp:142: error: expected `;' before ‘unsigned’
In file included from /usr/include/boost/python/converter/arg_to_python.hpp:19,
                 from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object/function_handle.hpp:15: error: template argument 1 is invalid
/usr/include/boost/python/object/function_handle.hpp:15: error: invalid type in declaration before ‘;’ token
/usr/include/boost/python/object/function_handle.hpp:21: error: template argument 1 is invalid
/usr/include/boost/python/object/function_handle.hpp:37: error: template argument 1 is invalid
In file included from /usr/include/boost/python/call.hpp:15,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/arg_to_python.hpp:42: error: template argument 1 is invalid
/usr/include/boost/python/converter/arg_to_python.hpp:48: error: template argument 1 is invalid
/usr/include/boost/python/converter/arg_to_python.hpp:52: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/arg_to_python.hpp:56: error: template argument 1 is invalid
/usr/include/boost/python/converter/arg_to_python.hpp:60: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/arg_to_python.hpp:78: error: template argument 1 is invalid
/usr/include/boost/python/converter/arg_to_python.hpp:83: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/arg_to_python.hpp:92: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/arg_to_python.hpp:97: error: expected `;' before ‘private’
/usr/include/boost/python/converter/arg_to_python.hpp: In function ‘void boost::python::converter::detail::reject_raw_object_ptr(T*)’:
/usr/include/boost/python/converter/arg_to_python.hpp:190: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/arg_to_python.hpp:190: error: template argument 1 is invalid
/usr/include/boost/python/converter/arg_to_python.hpp: In constructor ‘boost::python::converter::detail::function_arg_to_python<T>::function_arg_to_python(const T&)’:
/usr/include/boost/python/converter/arg_to_python.hpp:203: error: template argument 1 is invalid
/usr/include/boost/python/converter/arg_to_python.hpp: At global scope:
/usr/include/boost/python/converter/arg_to_python.hpp:221: error: expected initializer before ‘*’ token
/usr/include/boost/python/converter/arg_to_python.hpp: In constructor ‘boost::python::converter::detail::reference_arg_to_python<T>::reference_arg_to_python(T&)’:
/usr/include/boost/python/converter/arg_to_python.hpp:229: error: template argument 1 is invalid
/usr/include/boost/python/converter/arg_to_python.hpp: In constructor ‘boost::python::converter::detail::shared_ptr_arg_to_python<T>::shared_ptr_arg_to_python(const T&)’:
/usr/include/boost/python/converter/arg_to_python.hpp:235: error: template argument 1 is invalid
/usr/include/boost/python/converter/arg_to_python.hpp: In constructor ‘boost::python::converter::detail::pointer_shallow_arg_to_python<Ptr>::pointer_shallow_arg_to_python(Ptr)’:
/usr/include/boost/python/converter/arg_to_python.hpp:241: error: template argument 1 is invalid
/usr/include/boost/python/converter/arg_to_python.hpp: At global scope:
/usr/include/boost/python/converter/arg_to_python.hpp:247: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/python/call.hpp:16,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/converter/return_from_python.hpp:31: error: ‘PyObject’ has not been declared
/usr/include/boost/python/converter/return_from_python.hpp:38: error: ‘PyObject’ has not been declared
/usr/include/boost/python/converter/return_from_python.hpp:47: error: ‘PyObject’ has not been declared
/usr/include/boost/python/converter/return_from_python.hpp:56: error: ‘PyObject’ has not been declared
/usr/include/boost/python/converter/return_from_python.hpp:99: error: ‘PyObject’ has not been declared
/usr/include/boost/python/converter/return_from_python.hpp: In member function ‘void boost::python::converter::return_from_python<void>::operator()(int*) const’:
/usr/include/boost/python/converter/return_from_python.hpp:101: error: ‘void_result_from_python’ was not declared in this scope
/usr/include/boost/python/converter/return_from_python.hpp: At global scope:
/usr/include/boost/python/converter/return_from_python.hpp:123: error: declaration of ‘operator()’ as non-function
/usr/include/boost/python/converter/return_from_python.hpp:123: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/return_from_python.hpp:123: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/converter/return_from_python.hpp:136: error: declaration of ‘operator()’ as non-function
/usr/include/boost/python/converter/return_from_python.hpp:136: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/return_from_python.hpp:136: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/converter/return_from_python.hpp:144: error: declaration of ‘operator()’ as non-function
/usr/include/boost/python/converter/return_from_python.hpp:144: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/return_from_python.hpp:144: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/converter/return_from_python.hpp:152: error: declaration of ‘operator()’ as non-function
/usr/include/boost/python/converter/return_from_python.hpp:152: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/return_from_python.hpp:152: error: ‘obj’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:47,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/call.hpp:33,
                 from /usr/include/boost/python/object_core.hpp:12,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/call.hpp:53: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call’
/usr/include/boost/python/call.hpp:53: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call.hpp:53: error: ‘callable’ was not declared in this scope
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:54: error: expected primary-expression before ‘const’
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call.hpp:55: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_core.hpp:83: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_core.hpp:104: error: expected type-specifier before ‘bool_type’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&, const A13&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/object_core.hpp:100,
                 from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_call.hpp: In member function ‘typename boost::python::detail::dependent<boost::python::api::object, A0>::type boost::python::api::object_operators<U>::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&, const A13&, const A14&) const’:
/usr/include/boost/python/object_call.hpp:19: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_call.hpp:19: error: expected primary-expression before ‘>’ token
In file included from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/object_core.hpp: At global scope:
/usr/include/boost/python/object_core.hpp:214: error: expected `)' before ‘*’ token
/usr/include/boost/python/object_core.hpp:220: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object_core.hpp:223: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object_core.hpp:278: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/boost/python/object_core.hpp:314: error: template argument 1 is invalid
/usr/include/boost/python/object_core.hpp:358: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object_core.hpp:364: error: expected `;' before ‘template’
/usr/include/boost/python/object_core.hpp:365: error: expected initializer before ‘*’ token
/usr/include/boost/python/object_core.hpp:376: error: expected initializer before ‘*’ token
/usr/include/boost/python/object_core.hpp:387: error: expected initializer before ‘*’ token
/usr/include/boost/python/object_core.hpp: In constructor ‘boost::python::api::object::object()’:
/usr/include/boost/python/object_core.hpp:414: error: ‘Py_None’ was not declared in this scope
/usr/include/boost/python/object_core.hpp: In copy constructor ‘boost::python::api::object_base::object_base(const boost::python::api::object_base&)’:
/usr/include/boost/python/object_core.hpp:419: error: class ‘boost::python::api::object_base’ does not have any field named ‘m_ptr’
/usr/include/boost/python/object_core.hpp:419: error: ‘const struct boost::python::api::object_base’ has no member named ‘m_ptr’
/usr/include/boost/python/object_core.hpp: At global scope:
/usr/include/boost/python/object_core.hpp:422: error: expected `)' before ‘*’ token
/usr/include/boost/python/object_core.hpp: In member function ‘boost::python::api::object_base& boost::python::api::object_base::operator=(const boost::python::api::object_base&)’:
/usr/include/boost/python/object_core.hpp:428: error: ‘const struct boost::python::api::object_base’ has no member named ‘m_ptr’
/usr/include/boost/python/object_core.hpp:428: error: ‘Py_INCREF’ was not declared in this scope
/usr/include/boost/python/object_core.hpp:429: error: ‘struct boost::python::api::object_base’ has no member named ‘m_ptr’
/usr/include/boost/python/object_core.hpp:429: error: ‘Py_DECREF’ was not declared in this scope
/usr/include/boost/python/object_core.hpp:430: error: ‘struct boost::python::api::object_base’ has no member named ‘m_ptr’
/usr/include/boost/python/object_core.hpp:430: error: ‘const struct boost::python::api::object_base’ has no member named ‘m_ptr’
/usr/include/boost/python/object_core.hpp: In destructor ‘boost::python::api::object_base::~object_base()’:
/usr/include/boost/python/object_core.hpp:436: error: ‘m_ptr’ was not declared in this scope
/usr/include/boost/python/object_core.hpp:436: error: ‘Py_DECREF’ was not declared in this scope
/usr/include/boost/python/object_core.hpp: In constructor ‘boost::python::api::object::object(boost::python::detail::borrowed_reference_t*)’:
/usr/include/boost/python/object_core.hpp:440: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/object_core.hpp:440: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_core.hpp: In constructor ‘boost::python::api::object::object(boost::python::detail::new_reference_t*)’:
/usr/include/boost/python/object_core.hpp:444: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/object_core.hpp:444: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_core.hpp: In constructor ‘boost::python::api::object::object(boost::python::detail::new_non_null_reference_t*)’:
/usr/include/boost/python/object_core.hpp:448: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/object_core.hpp:448: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_core.hpp: At global scope:
/usr/include/boost/python/object_core.hpp:451: error: expected initializer before ‘*’ token
/usr/include/boost/python/object_core.hpp:467: error: ‘PyObject’ has not been declared
/usr/include/boost/python/object_core.hpp:469: error: ‘PyObject’ has not been declared
/usr/include/boost/python/object_core.hpp:476: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/python.hpp:11,
                 from first.cpp:9:
/usr/include/boost/python/args.hpp: In member function ‘boost::python::arg& boost::python::detail::keywords<1u>::operator=(const T&)’:
/usr/include/boost/python/args.hpp:75: error: template argument 1 is invalid
/usr/include/boost/python/args.hpp:75: error: ‘class boost::python::api::object’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:47,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp: At global scope:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/call_method.hpp:32,
                 from /usr/include/boost/python.hpp:17,
                 from first.cpp:9:
/usr/include/boost/python/call_method.hpp:52: error: template declaration of ‘typename boost::python::detail::returnable<T>::type boost::python::call_method’
/usr/include/boost/python/call_method.hpp:52: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: ‘self’ was not declared in this scope
/usr/include/boost/python/call_method.hpp:52: error: expected primary-expression before ‘char’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:53: error: expected primary-expression before ‘const’
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/call_method.hpp:54: error: expected primary-expression before ‘=’ token
In file included from /usr/include/boost/python/proxy.hpp:9,
                 from /usr/include/boost/python/object_attributes.hpp:10,
                 from /usr/include/boost/python/object.hpp:10,
                 from /usr/include/boost/python/class.hpp:15,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object_operators.hpp: In member function ‘boost::python::api::object boost::python::api::object_operators<U>::operator()() const’:
/usr/include/boost/python/object_operators.hpp:54: error: ‘call’ was not declared in this scope
/usr/include/boost/python/object_operators.hpp:54: error: expected primary-expression before ‘>’ token
/usr/include/boost/python/object_operators.hpp:54: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_operators.hpp: At global scope:
/usr/include/boost/python/object_operators.hpp:60: error: expected type-specifier before ‘bool_type’
/usr/include/boost/python/object_operators.hpp: In member function ‘bool boost::python::api::object_operators<U>::operator!() const’:
/usr/include/boost/python/object_operators.hpp:71: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_operators.hpp:71: error: there are no arguments to ‘PyObject_IsTrue’ that depend on a template parameter, so a declaration of ‘PyObject_IsTrue’ must be available
/usr/include/boost/python/object_operators.hpp:71: error: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
In file included from /usr/include/boost/python/object_protocol.hpp:10,
                 from /usr/include/boost/python/object_attributes.hpp:12,
                 from /usr/include/boost/python/object.hpp:10,
                 from /usr/include/boost/python/class.hpp:15,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object_protocol_core.hpp: At global scope:
/usr/include/boost/python/object_protocol_core.hpp:34: error: template argument 1 is invalid
/usr/include/boost/python/object_protocol_core.hpp:34: error: template argument 1 is invalid
/usr/include/boost/python/object_protocol_core.hpp:35: error: template argument 1 is invalid
/usr/include/boost/python/object_protocol_core.hpp:35: error: template argument 1 is invalid
/usr/include/boost/python/object_protocol_core.hpp:36: error: template argument 1 is invalid
/usr/include/boost/python/object_protocol_core.hpp:36: error: template argument 1 is invalid
In file included from /usr/include/boost/python/object.hpp:12,
                 from /usr/include/boost/python/class.hpp:15,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object_slices.hpp:20: error: template argument 1 is invalid
/usr/include/boost/python/object_slices.hpp:20: error: template argument 1 is invalid
/usr/include/boost/python/object_slices.hpp:20: error: template argument 1 is invalid
/usr/include/boost/python/object_slices.hpp:20: error: template argument 2 is invalid
/usr/include/boost/python/object_slices.hpp: In member function ‘boost::python::api::object_slice boost::python::api::object_operators<U>::slice(const boost::python::api::object&, const boost::python::api::object&)’:
/usr/include/boost/python/object_slices.hpp:38: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp:38: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp: In member function ‘boost::python::api::const_object_slice boost::python::api::object_operators<U>::slice(const boost::python::api::object&, const boost::python::api::object&) const’:
/usr/include/boost/python/object_slices.hpp:46: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp:46: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp: In member function ‘boost::python::api::object_slice boost::python::api::object_operators<U>::slice(boost::python::api::slice_nil, const boost::python::api::object&)’:
/usr/include/boost/python/object_slices.hpp:54: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/object_slices.hpp:54: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp:54: error: expected primary-expression before ‘(’ token
/usr/include/boost/python/object_slices.hpp:54: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_slices.hpp:54: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp: In member function ‘boost::python::api::const_object_slice boost::python::api::object_operators<U>::slice(boost::python::api::slice_nil, const boost::python::api::object&) const’:
/usr/include/boost/python/object_slices.hpp:62: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/object_slices.hpp:62: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp:62: error: expected primary-expression before ‘(’ token
/usr/include/boost/python/object_slices.hpp:62: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_slices.hpp:62: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp: In member function ‘boost::python::api::object_slice boost::python::api::object_operators<U>::slice(boost::python::api::slice_nil, boost::python::api::slice_nil)’:
/usr/include/boost/python/object_slices.hpp:70: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/object_slices.hpp:70: error: expected primary-expression before ‘(’ token
/usr/include/boost/python/object_slices.hpp:70: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_slices.hpp:70: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_slices.hpp: In member function ‘boost::python::api::const_object_slice boost::python::api::object_operators<U>::slice(boost::python::api::slice_nil, boost::python::api::slice_nil) const’:
/usr/include/boost/python/object_slices.hpp:78: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/object_slices.hpp:78: error: expected primary-expression before ‘(’ token
/usr/include/boost/python/object_slices.hpp:78: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_slices.hpp:78: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_slices.hpp: In member function ‘boost::python::api::object_slice boost::python::api::object_operators<U>::slice(const boost::python::api::object&, boost::python::api::slice_nil)’:
/usr/include/boost/python/object_slices.hpp:86: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp:86: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/object_slices.hpp:86: error: expected primary-expression before ‘(’ token
/usr/include/boost/python/object_slices.hpp:86: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp:86: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_slices.hpp: In member function ‘boost::python::api::const_object_slice boost::python::api::object_operators<U>::slice(const boost::python::api::object&, boost::python::api::slice_nil) const’:
/usr/include/boost/python/object_slices.hpp:94: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp:94: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/object_slices.hpp:94: error: expected primary-expression before ‘(’ token
/usr/include/boost/python/object_slices.hpp:94: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object_slices.hpp:94: error: expected primary-expression before ‘)’ token
/usr/include/boost/python/object_slices.hpp: In static member function ‘static boost::python::api::object boost::python::api::const_slice_policies::get(const boost::python::api::object&, const int&)’:
/usr/include/boost/python/object_slices.hpp:121: error: request for member ‘first’ in ‘key’, which is of non-class type ‘const int’
/usr/include/boost/python/object_slices.hpp:121: error: request for member ‘second’ in ‘key’, which is of non-class type ‘const int’
/usr/include/boost/python/object_slices.hpp: In static member function ‘static const boost::python::api::object& boost::python::api::slice_policies::set(const boost::python::api::object&, const int&, const boost::python::api::object&)’:
/usr/include/boost/python/object_slices.hpp:129: error: request for member ‘first’ in ‘key’, which is of non-class type ‘const int’
/usr/include/boost/python/object_slices.hpp:129: error: request for member ‘second’ in ‘key’, which is of non-class type ‘const int’
/usr/include/boost/python/object_slices.hpp: In static member function ‘static void boost::python::api::slice_policies::del(const boost::python::api::object&, const int&)’:
/usr/include/boost/python/object_slices.hpp:137: error: request for member ‘first’ in ‘key’, which is of non-class type ‘const int’
/usr/include/boost/python/object_slices.hpp:137: error: request for member ‘second’ in ‘key’, which is of non-class type ‘const int’
In file included from /usr/include/boost/python/class.hpp:15,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object.hpp: In function ‘boost::python::ssize_t boost::python::len(const boost::python::api::object&)’:
/usr/include/boost/python/object.hpp:20: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/object.hpp:20: error: ‘PyObject_Length’ was not declared in this scope
/usr/include/boost/python/object.hpp:21: error: ‘PyErr_Occurred’ was not declared in this scope
In file included from /usr/include/boost/python/with_custodian_and_ward.hpp:11,
                 from /usr/include/boost/python/return_internal_reference.hpp:12,
                 from /usr/include/boost/python/data_members.hpp:14,
                 from /usr/include/boost/python/class.hpp:17,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/life_support.hpp: At global scope:
/usr/include/boost/python/object/life_support.hpp:11: error: expected constructor, destructor, or type conversion before ‘*’ token
In file included from /usr/include/boost/python/return_internal_reference.hpp:12,
                 from /usr/include/boost/python/data_members.hpp:14,
                 from /usr/include/boost/python/class.hpp:17,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/with_custodian_and_ward.hpp:22: error: expected initializer before ‘*’ token
/usr/include/boost/python/with_custodian_and_ward.hpp:32: error: expected initializer before ‘*’ token
/usr/include/boost/python/with_custodian_and_ward.hpp: In static member function ‘static bool boost::python::with_custodian_and_ward<custodian, ward, BasePolicy_>::precall(const ArgumentPackage&)’:
/usr/include/boost/python/with_custodian_and_ward.hpp:56: error: ‘PyExc_IndexError’ was not declared in this scope
/usr/include/boost/python/with_custodian_and_ward.hpp:58: error: there are no arguments to ‘PyErr_SetString’ that depend on a template parameter, so a declaration of ‘PyErr_SetString’ must be available
/usr/include/boost/python/with_custodian_and_ward.hpp:62: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/with_custodian_and_ward.hpp:62: error: ‘patient’ was not declared in this scope
/usr/include/boost/python/with_custodian_and_ward.hpp:63: error: ‘nurse’ was not declared in this scope
/usr/include/boost/python/with_custodian_and_ward.hpp:65: error: ‘life_support’ was not declared in this scope
/usr/include/boost/python/with_custodian_and_ward.hpp:65: error: ‘make_nurse_and_patient’ is not a member of ‘boost::python::objects’
/usr/include/boost/python/with_custodian_and_ward.hpp:72: error: there are no arguments to ‘Py_DECREF’ that depend on a template parameter, so a declaration of ‘Py_DECREF’ must be available
/usr/include/boost/python/with_custodian_and_ward.hpp: At global scope:
/usr/include/boost/python/with_custodian_and_ward.hpp:84: error: expected initializer before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:47,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/object/make_holder.hpp:38,
                 from /usr/include/boost/python/detail/make_keyword_range_fn.hpp:11,
                 from /usr/include/boost/python/init.hpp:16,
                 from /usr/include/boost/python/class.hpp:20,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/make_holder.hpp:76: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/python/object/class_metadata.hpp:6,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/converter/shared_ptr_from_python.hpp:26: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/converter/shared_ptr_from_python.hpp:34: error: expected `;' before ‘static’
/usr/include/boost/python/converter/shared_ptr_from_python.hpp:34: error: ‘PyObject’ has not been declared
/usr/include/boost/python/converter/shared_ptr_from_python.hpp: In constructor ‘boost::python::converter::shared_ptr_from_python<T>::shared_ptr_from_python()’:
/usr/include/boost/python/converter/shared_ptr_from_python.hpp:22: error: ‘convertible’ was not declared in this scope
/usr/include/boost/python/converter/shared_ptr_from_python.hpp: In static member function ‘static void boost::python::converter::shared_ptr_from_python<T>::construct(int*, boost::python::converter::rvalue_from_python_stage1_data*)’:
/usr/include/boost/python/converter/shared_ptr_from_python.hpp:43: error: template argument 1 is invalid
In file included from /usr/include/boost/python/to_python_converter.hpp:11,
                 from /usr/include/boost/python/object/class_wrapper.hpp:8,
                 from /usr/include/boost/python/object/class_metadata.hpp:9,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/converter/as_to_python_function.hpp: At global scope:
/usr/include/boost/python/converter/as_to_python_function.hpp:25: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/converter/as_to_python_function.hpp:42: error: expected `;' before ‘}’ token
In file included from /usr/include/boost/python/object/class_metadata.hpp:9,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/class_wrapper.hpp:24: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object/class_wrapper.hpp:28: error: expected `;' before ‘}’ token
/usr/include/boost/python/object/class_wrapper.hpp:34: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object/class_wrapper.hpp:38: error: expected `;' before ‘}’ token
In file included from /usr/include/boost/python/override.hpp:13,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/extract.hpp:45: error: expected `)' before ‘*’ token
/usr/include/boost/python/extract.hpp:51: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/extract.hpp:59: error: expected `)' before ‘*’ token
/usr/include/boost/python/extract.hpp:65: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/extract.hpp:78: error: expected `)' before ‘*’ token
/usr/include/boost/python/extract.hpp:83: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/extract.hpp:91: error: expected `)' before ‘*’ token
/usr/include/boost/python/extract.hpp:96: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/extract.hpp:141: error: expected `)' before ‘*’ token
/usr/include/boost/python/extract.hpp:149: error: ‘boost::python::extract<T>::extract’ declared as an ‘inline’ variable
/usr/include/boost/python/extract.hpp:149: error: ‘int boost::python::extract<T>::extract’ is not a static member of ‘struct boost::python::extract<T>’
/usr/include/boost/python/extract.hpp:149: error: template definition of non-template ‘int boost::python::extract<T>::extract’
/usr/include/boost/python/extract.hpp:149: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/extract.hpp:149: error: ‘o’ was not declared in this scope
/usr/include/boost/python/extract.hpp: In constructor ‘boost::python::extract<T>::extract(const boost::python::api::object&)’:
/usr/include/boost/python/extract.hpp:156: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/extract.hpp: At global scope:
/usr/include/boost/python/extract.hpp:163: error: ‘boost::python::converter::extract_rvalue<T>::extract_rvalue’ declared as an ‘inline’ variable
/usr/include/boost/python/extract.hpp:163: error: ‘int boost::python::converter::extract_rvalue<T>::extract_rvalue’ is not a static member of ‘struct boost::python::converter::extract_rvalue<T>’
/usr/include/boost/python/extract.hpp:163: error: template definition of non-template ‘int boost::python::converter::extract_rvalue<T>::extract_rvalue’
/usr/include/boost/python/extract.hpp:163: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/extract.hpp:163: error: ‘x’ was not declared in this scope
/usr/include/boost/python/extract.hpp: In member function ‘typename boost::python::converter::extract_rvalue<T>::result_type boost::python::converter::extract_rvalue<T>::operator()() const’:
/usr/include/boost/python/extract.hpp:186: error: ‘m_source’ was not declared in this scope
/usr/include/boost/python/extract.hpp: At global scope:
/usr/include/boost/python/extract.hpp:191: error: ‘boost::python::converter::extract_reference<Ref>::extract_reference’ declared as an ‘inline’ variable
/usr/include/boost/python/extract.hpp:191: error: ‘int boost::python::converter::extract_reference<Ref>::extract_reference’ is not a static member of ‘struct boost::python::converter::extract_reference<Ref>’
/usr/include/boost/python/extract.hpp:191: error: template definition of non-template ‘int boost::python::converter::extract_reference<Ref>::extract_reference’
/usr/include/boost/python/extract.hpp:191: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/extract.hpp:191: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/extract.hpp: In member function ‘Ref boost::python::converter::extract_reference<Ref>::operator()() const’:
/usr/include/boost/python/extract.hpp:209: error: ‘throw_no_reference_from_python’ was not declared in this scope
/usr/include/boost/python/extract.hpp:209: error: ‘m_source’ was not declared in this scope
/usr/include/boost/python/extract.hpp: At global scope:
/usr/include/boost/python/extract.hpp:215: error: ‘boost::python::converter::extract_pointer<Ptr>::extract_pointer’ declared as an ‘inline’ variable
/usr/include/boost/python/extract.hpp:215: error: ‘int boost::python::converter::extract_pointer<Ptr>::extract_pointer’ is not a static member of ‘struct boost::python::converter::extract_pointer<Ptr>’
/usr/include/boost/python/extract.hpp:215: error: template definition of non-template ‘int boost::python::converter::extract_pointer<Ptr>::extract_pointer’
/usr/include/boost/python/extract.hpp:215: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/extract.hpp:215: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/extract.hpp: In member function ‘bool boost::python::converter::extract_pointer<Ptr>::check() const’:
/usr/include/boost/python/extract.hpp:226: error: ‘m_source’ was not declared in this scope
/usr/include/boost/python/extract.hpp:226: error: ‘Py_None’ was not declared in this scope
/usr/include/boost/python/extract.hpp: In member function ‘Ptr boost::python::converter::extract_pointer<Ptr>::operator()() const’:
/usr/include/boost/python/extract.hpp:232: error: ‘m_source’ was not declared in this scope
/usr/include/boost/python/extract.hpp:232: error: ‘Py_None’ was not declared in this scope
/usr/include/boost/python/extract.hpp:233: error: ‘throw_no_pointer_from_python’ was not declared in this scope
/usr/include/boost/python/extract.hpp: At global scope:
/usr/include/boost/python/extract.hpp:239: error: ‘boost::python::converter::extract_object_manager<T>::extract_object_manager’ declared as an ‘inline’ variable
/usr/include/boost/python/extract.hpp:239: error: ‘int boost::python::converter::extract_object_manager<T>::extract_object_manager’ is not a static member of ‘struct boost::python::converter::extract_object_manager<T>’
/usr/include/boost/python/extract.hpp:239: error: template definition of non-template ‘int boost::python::converter::extract_object_manager<T>::extract_object_manager’
/usr/include/boost/python/extract.hpp:239: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/extract.hpp:239: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/extract.hpp: In member function ‘bool boost::python::converter::extract_object_manager<T>::check() const’:
/usr/include/boost/python/extract.hpp:247: error: ‘m_source’ was not declared in this scope
/usr/include/boost/python/extract.hpp: In member function ‘T boost::python::converter::extract_object_manager<T>::operator()() const’:
/usr/include/boost/python/extract.hpp:254: error: ‘m_source’ was not declared in this scope
In file included from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: At global scope:
/usr/include/boost/python/override.hpp:37: error: expected `)' before ‘*’ token
/usr/include/boost/python/override.hpp:83: error: template argument 1 is invalid
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result::operator T()’:
/usr/include/boost/python/override.hpp:46: error: request for member ‘release’ in ‘((boost::python::detail::method_result*)this)->boost::python::detail::method_result::m_obj’, which is of non-class type ‘int’
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result::operator T&() const’:
/usr/include/boost/python/override.hpp:66: error: template argument 1 is invalid
/usr/include/boost/python/override.hpp:66: error: expected `>' before ‘&’ token
/usr/include/boost/python/override.hpp:66: error: expected `(' before ‘&’ token
/usr/include/boost/python/override.hpp:66: error: expected primary-expression before ‘>’ token
/usr/include/boost/python/override.hpp:66: error: request for member ‘release’ in ‘((const boost::python::detail::method_result*)this)->boost::python::detail::method_result::m_obj’, which is of non-class type ‘int’
/usr/include/boost/python/override.hpp: In member function ‘T boost::python::detail::method_result::as(boost::type<Target>*)’:
/usr/include/boost/python/override.hpp:74: error: request for member ‘release’ in ‘((boost::python::detail::method_result*)this)->boost::python::detail::method_result::m_obj’, which is of non-class type ‘int’
/usr/include/boost/python/override.hpp: At global scope:
/usr/include/boost/python/override.hpp:91: error: template argument 1 is invalid
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()() const’:
/usr/include/boost/python/override.hpp:101: error: ‘const class boost::python::override’ has no member named ‘ptr’
/usr/include/boost/python/override.hpp:103: error: ‘PyEval_CallFunction’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&, const A13&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/override.hpp:111,
                 from /usr/include/boost/python/wrapper.hpp:8,
                 from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/override.hpp: In member function ‘boost::python::detail::method_result boost::python::override::operator()(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&, const A13&, const A14&) const’:
/usr/include/boost/python/override.hpp:135: error: ‘const class boost::python::override’ has no member named ‘ptr’
In file included from /usr/include/boost/python/object/value_holder.hpp:15,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/wrapper.hpp: In member function ‘boost::python::override boost::python::wrapper<T>::get_override(const char*) const’:
/usr/include/boost/python/wrapper.hpp:27: error: ‘PyTypeObject’ was not declared in this scope
/usr/include/boost/python/wrapper.hpp:27: error: missing template arguments before ‘=’ token
/usr/include/boost/python/wrapper.hpp:27: error: ‘const struct boost::python::converter::registration’ has no member named ‘get_class_object’
/usr/include/boost/python/wrapper.hpp:29: error: missing template arguments before ‘)’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:47,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp: At global scope:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/object/value_holder.hpp:50,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:131: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:47,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/object/value_holder.hpp:77,
                 from /usr/include/boost/python/object/class_metadata.hpp:11,
                 from /usr/include/boost/python/class.hpp:23,
                 from /usr/include/boost/python.hpp:18,
                 from first.cpp:9:
/usr/include/boost/python/object/value_holder.hpp:155: error: expected `)' before ‘*’ token
In file included from /usr/include/boost/python/def.hpp:14,
                 from /usr/include/boost/python.hpp:22,
                 from first.cpp:9:
/usr/include/boost/python/scope.hpp:19: error: expected initializer before ‘*’ token
/usr/include/boost/python/scope.hpp:32: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/scope.hpp: In constructor ‘boost::python::scope::scope(const boost::python::api::object&)’:
/usr/include/boost/python/scope.hpp:40: error: class ‘boost::python::scope’ does not have any field named ‘m_previous_scope’
/usr/include/boost/python/scope.hpp:40: error: ‘current_scope’ is not a member of ‘boost::python::detail’
/usr/include/boost/python/scope.hpp:42: error: ‘current_scope’ is not a member of ‘boost::python::detail’
/usr/include/boost/python/scope.hpp:42: error: ‘const class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/scope.hpp: In constructor ‘boost::python::scope::scope()’:
/usr/include/boost/python/scope.hpp:47: error: ‘current_scope’ is not a member of ‘boost::python::detail’
/usr/include/boost/python/scope.hpp:47: error: ‘current_scope’ is not a member of ‘boost::python::detail’
/usr/include/boost/python/scope.hpp:47: error: ‘Py_None’ was not declared in this scope
/usr/include/boost/python/scope.hpp:49: error: class ‘boost::python::scope’ does not have any field named ‘m_previous_scope’
/usr/include/boost/python/scope.hpp:49: error: ‘current_scope’ is not a member of ‘boost::python::detail’
/usr/include/boost/python/scope.hpp: In destructor ‘boost::python::scope::~scope()’:
/usr/include/boost/python/scope.hpp:55: error: ‘current_scope’ is not a member of ‘boost::python::detail’
/usr/include/boost/python/scope.hpp:56: error: ‘current_scope’ is not a member of ‘boost::python::detail’
/usr/include/boost/python/scope.hpp:56: error: ‘m_previous_scope’ was not declared in this scope
/usr/include/boost/python/scope.hpp: In copy constructor ‘boost::python::scope::scope(const boost::python::scope&)’:
/usr/include/boost/python/scope.hpp:71: error: class ‘boost::python::scope’ does not have any field named ‘m_previous_scope’
/usr/include/boost/python/scope.hpp:71: error: ‘current_scope’ is not a member of ‘boost::python::detail’
/usr/include/boost/python/scope.hpp:73: error: ‘current_scope’ is not a member of ‘boost::python::detail’
/usr/include/boost/python/scope.hpp:73: error: ‘const class boost::python::scope’ has no member named ‘ptr’
In file included from /usr/include/boost/python/list.hpp:11,
                 from /usr/include/boost/python/dict.hpp:11,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp: At global scope:
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:23: error: ‘PyTypeObject’ has not been declared
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:28: error: ‘PyObject’ has not been declared
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:34: error: ‘PyTypeObject’ has not been declared
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:35: error: ‘boost::python::converter::pytype_object_manager_traits<pytype, T>::adopt’ declared as an ‘inline’ variable
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:35: error: ‘boost::python::detail::new_reference_t* boost::python::converter::pytype_object_manager_traits<pytype, T>::adopt’ is not a static member of ‘struct boost::python::converter::pytype_object_manager_traits<pytype, T>’
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:35: error: template definition of non-template ‘boost::python::detail::new_reference_t* boost::python::converter::pytype_object_manager_traits<pytype, T>::adopt’
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:35: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:35: error: ‘x’ was not declared in this scope
In file included from /usr/include/boost/python/dict.hpp:11,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/list.hpp:135: error: wrong number of template arguments (1, should be 2)
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:24: error: provided for ‘template<int* pytype, class T> struct boost::python::converter::pytype_object_manager_traits’
In file included from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/tuple.hpp:56: error: wrong number of template arguments (1, should be 2)
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:24: error: provided for ‘template<int* pytype, class T> struct boost::python::converter::pytype_object_manager_traits’
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&, const A13&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&, const A13&, const A14&)’:
/usr/include/boost/python/detail/make_tuple.hpp:24: error: ‘::PyTuple_New’ has not been declared
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::tuple’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘class boost::python::api::object’ has no member named ‘ptr’
/usr/include/boost/python/detail/make_tuple.hpp:25: error: there are no arguments to ‘PyTuple_SET_ITEM’ that depend on a template parameter, so a declaration of ‘PyTuple_SET_ITEM’ must be available
In file included from /usr/include/boost/python.hpp:24,
                 from first.cpp:9:
/usr/include/boost/python/dict.hpp: At global scope:
/usr/include/boost/python/dict.hpp:144: error: wrong number of template arguments (1, should be 2)
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:24: error: provided for ‘template<int* pytype, class T> struct boost::python::converter::pytype_object_manager_traits’
In file included from /usr/include/boost/python/docstring_options.hpp:8,
                 from /usr/include/boost/python.hpp:25,
                 from first.cpp:9:
/usr/include/boost/python/object/function.hpp:18: error: expected class-name before ‘{’ token
/usr/include/boost/python/object/function.hpp:26: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object/function.hpp:45: error: ‘PyObject’ has not been declared
/usr/include/boost/python/object/function.hpp:45: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/python/enum.hpp:10,
                 from /usr/include/boost/python.hpp:26,
                 from first.cpp:9:
/usr/include/boost/python/object/enum_base.hpp:21: error: ‘boost::python::converter::to_python_function_t’ has not been declared
/usr/include/boost/python/object/enum_base.hpp:22: error: ‘boost::python::converter::convertible_function’ has not been declared
/usr/include/boost/python/object/enum_base.hpp:23: error: ‘boost::python::converter::constructor_function’ has not been declared
/usr/include/boost/python/object/enum_base.hpp:29: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/python.hpp:26,
                 from first.cpp:9:
/usr/include/boost/python/enum.hpp:31: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/enum.hpp:32: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/enum.hpp:33: error: ‘PyObject’ has not been declared
/usr/include/boost/python/enum.hpp:50: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/boost/python/enum.hpp:65: error: ‘void* boost::python::enum_<T>::convertible_from_python’ is not a static member of ‘struct boost::python::enum_<T>’
/usr/include/boost/python/enum.hpp:65: error: template definition of non-template ‘void* boost::python::enum_<T>::convertible_from_python’
/usr/include/boost/python/enum.hpp:65: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/enum.hpp:65: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/enum.hpp:78: error: variable or field ‘construct’ declared void
/usr/include/boost/python/enum.hpp:78: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/enum.hpp:78: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/enum.hpp:78: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/enum.hpp:78: error: ‘data’ was not declared in this scope
In file included from /usr/include/boost/python/exec.hpp:9,
                 from /usr/include/boost/python.hpp:29,
                 from first.cpp:9:
/usr/include/boost/python/str.hpp:407: error: wrong number of template arguments (1, should be 2)
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:24: error: provided for ‘template<int* pytype, class T> struct boost::python::converter::pytype_object_manager_traits’
In file included from /usr/include/boost/python/implicit.hpp:10,
                 from /usr/include/boost/python.hpp:33,
                 from first.cpp:9:
/usr/include/boost/python/converter/implicit.hpp:19: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/converter/implicit.hpp:29: error: expected `;' before ‘static’
/usr/include/boost/python/converter/implicit.hpp:29: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/python.hpp:33,
                 from first.cpp:9:
/usr/include/boost/python/implicit.hpp: In function ‘void boost::python::implicitly_convertible(boost::type<Target>*, boost::type<Target>*)’:
/usr/include/boost/python/implicit.hpp:21: error: ‘push_back’ is not a member of ‘boost::python::converter::registry’
In file included from /usr/include/boost/python/iterator.hpp:11,
                 from /usr/include/boost/python.hpp:37,
                 from first.cpp:9:
/usr/include/boost/python/object/iterator.hpp: In function ‘boost::python::api::object boost::python::objects::detail::demand_iterator_class(const char*, Iterator*, const NextPolicies&)’:
/usr/include/boost/python/object/iterator.hpp:120: error: template argument 1 is invalid
/usr/include/boost/python/object/iterator.hpp:120: error: invalid type in declaration before ‘(’ token
/usr/include/boost/python/object/iterator.hpp:123: error: request for member ‘get’ in ‘class_obj’, which is of non-class type ‘int’
In file included from /usr/include/boost/python.hpp:39,
                 from first.cpp:9:
/usr/include/boost/python/long.hpp: At global scope:
/usr/include/boost/python/long.hpp:61: error: wrong number of template arguments (1, should be 2)
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:24: error: provided for ‘template<int* pytype, class T> struct boost::python::converter::pytype_object_manager_traits’
In file included from /usr/include/boost/python.hpp:40,
                 from first.cpp:9:
/usr/include/boost/python/lvalue_from_pytype.hpp:33: error: ‘execute’ declared as an ‘inline’ field
/usr/include/boost/python/lvalue_from_pytype.hpp:33: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/lvalue_from_pytype.hpp:41: error: expected `;' before ‘}’ token
/usr/include/boost/python/lvalue_from_pytype.hpp:83: error: ‘PyTypeObject’ has not been declared
/usr/include/boost/python/lvalue_from_pytype.hpp:92: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/lvalue_from_pytype.hpp:101: error: expected `;' before ‘}’ token
/usr/include/boost/python/lvalue_from_pytype.hpp: In constructor ‘boost::python::lvalue_from_pytype<Extractor, python_type>::lvalue_from_pytype()’:
/usr/include/boost/python/lvalue_from_pytype.hpp:89: error: missing template arguments before ‘,’ token
In file included from /usr/include/boost/python.hpp:41,
                 from first.cpp:9:
/usr/include/boost/python/make_constructor.hpp: At global scope:
/usr/include/boost/python/make_constructor.hpp:34: error: expected `)' before ‘*’ token
/usr/include/boost/python/make_constructor.hpp:37: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/make_constructor.hpp:43: error: expected `;' before ‘private’
/usr/include/boost/python/make_constructor.hpp:68: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/make_constructor.hpp:88: error: expected initializer before ‘*’ token
/usr/include/boost/python/make_constructor.hpp:94: error: ‘template<class BaseArgs, class Offset> unsigned int boost::python::detail::arity(const boost::python::detail::offset_args<BaseArgs, Offset>&)’ redeclared as different kind of symbol
/usr/include/boost/python/detail/caller.hpp:50: error: previous declaration of ‘unsigned int boost::python::detail::arity’
In file included from /usr/include/boost/python.hpp:45,
                 from first.cpp:9:
/usr/include/boost/python/numeric.hpp:93: error: ‘PyObject’ has not been declared
/usr/include/boost/python/numeric.hpp:94: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/python/opaque_pointer_converter.hpp:15,
                 from /usr/include/boost/python.hpp:49,
                 from first.cpp:9:
/usr/include/boost/python/detail/dealloc.hpp:11: error: variable or field ‘dealloc’ declared void
/usr/include/boost/python/detail/dealloc.hpp:11: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/detail/dealloc.hpp:11: error: ‘self’ was not declared in this scope
In file included from /usr/include/boost/python.hpp:49,
                 from first.cpp:9:
/usr/include/boost/python/opaque_pointer_converter.hpp:63: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/opaque_pointer_converter.hpp:71: error: expected `;' before ‘static’
/usr/include/boost/python/opaque_pointer_converter.hpp:71: error: expected ‘;’ before ‘*’ token
first.cpp:17: error: expected `;' at end of input
first.cpp:17: error: expected `}' at end of input
/usr/include/boost/python/opaque_pointer_converter.hpp: In constructor ‘boost::python::opaque<Pointee>::opaque()’:
/usr/include/boost/python/opaque_pointer_converter.hpp:48: error: ‘type_object’ was not declared in this scope
/usr/include/boost/python/opaque_pointer_converter.hpp:51: error: there are no arguments to ‘PyType_Ready’ that depend on a template parameter, so a declaration of ‘PyType_Ready’ must be available
/usr/include/boost/python/opaque_pointer_converter.hpp: At global scope:
/usr/include/boost/python/opaque_pointer_converter.hpp:58: error: expected unqualified-id at end of input
/usr/include/boost/python/opaque_pointer_converter.hpp:58: error: expected `}' at end of input
/usr/include/boost/python/opaque_pointer_converter.hpp:58: error: expected `}' at end of input
/usr/include/boost/python/object_core.hpp: In constructor ‘boost::python::api::object::object(const T&) [with T = boost::python::scope]’:
/usr/include/boost/python/scope.hpp:71:   instantiated from here
/usr/include/boost/python/object_core.hpp:309: error: ‘object_base_initializer’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&) [with A0 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:37:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&) [with A0 = long int, A1 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:40:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&) [with A0 = long int, A1 = long int, A2 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:43:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:46:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:49:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:52:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:55:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:58:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:61:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:64:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int, A10 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:67:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int, A10 = long int, A11 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:70:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int, A10 = long int, A11 = long int, A12 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:73:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&, const A13&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int, A10 = long int, A11 = long int, A12 = long int, A13 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:76:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&, const A13&, const A14&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int, A10 = long int, A11 = long int, A12 = long int, A13 = long int, A14 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:79:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
/usr/include/boost/python/object_core.hpp: In constructor ‘boost::python::api::object::object(const T&) [with T = boost::python::tuple]’:
/usr/include/boost/python/numeric.hpp:120:   instantiated from ‘void boost::python::numeric::array::resize(const Sequence&) [with Sequence = boost::python::tuple]’
/usr/include/boost/preprocessor/iteration/detail/local.hpp:37:   instantiated from here
/usr/include/boost/python/object_core.hpp:309: error: ‘object_base_initializer’ was not declared in this scope
```

Can u tell me how to resolve this... #-o:cry:

---

### Post by dwhitney67 on 2009-11-20
The first error that stood out was:
```

/usr/include/boost/python/detail/wrap_python.hpp:50:23: error: pyconfig.h: No such file or directory

```

Upon attempting to locate pyconfig.h in /usr/include, I got these results:
```

$ find /usr/include -name pyconfig.h
/usr/include/python2.5/pyconfig.h
/usr/include/python2.6/pyconfig.h

```
Thus, augmenting your 'g++' statement, I came up with this:
```

g++ -c -fPIC -I/usr/include/python2.6 hello.cpp -o hello.o

```
Hopefully that works for you too.

P.S.  The -o option above is not necessary unless you plan to change the name of the object file.  It will always default to <modulename>.o

---

### Post by TheStatsMan on 2009-11-20
Boost Python has such terrible documentation. It is very frustrating. Anyway I found some working examples on the web the other day that should help you with your problem.

[http://www.shocksolution.com/math_tools/boost.python/index.html](http://www.shocksolution.com/math_tools/boost.python/index.html)

---

### Post by python.noob on 2009-11-21
> **dwhitney67 said:**
> The first error that stood out was:
```

/usr/include/boost/python/detail/wrap_python.hpp:50:23: error: pyconfig.h: No such file or directory

```Upon attempting to locate pyconfig.h in /usr/include, I got these results:
```

$ find /usr/include -name pyconfig.h
/usr/include/python2.5/pyconfig.h
/usr/include/python2.6/pyconfig.h

```Thus, augmenting your 'g++' statement, I came up with this:
```

g++ -c -fPIC -I/usr/include/python2.6 hello.cpp -o hello.o

```Hopefully that works for you too.

P.S.  The -o option above is not necessary unless you plan to change the name of the object file.  It will always default to <modulename>.o
Many thanks buddy... Problem solved..

---

### Post by python.noob on 2009-11-21
> **TheStatsMan said:**
> Boost Python has such terrible documentation. It is very frustrating. Anyway I found some working examples on the web the other day that should help you with your problem.

[http://www.shocksolution.com/math_tools/boost.python/index.html](http://www.shocksolution.com/math_tools/boost.python/index.html)
Ya you are absolutely right. It's all vauge. Nothing is clear.. Thanks for your help..

---

