---
title: "Problem compiling code utilyzing boost_python library"
date: 2012-07-16
forum: Programming Talk
---

### Post by alfa_80 on 2012-07-16
I am having problem with using command line to compile a code that utilizes boost_python library. My code is just a "hello world" code as below:

```

#include <boost/python.hpp>
#include <iostream>

int main() {

  std::cout << "Yes, it works :-)" << std::endl;


  return 0;

}


```I've used:
```
g++ try.cpp -o try -lboost_python
```It gives the following error message:
```
:api::object’ has no member named ‘ptr’
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
                 from try.cpp:1:
/usr/include/boost/python/dict.hpp: At global scope:
/usr/include/boost/python/dict.hpp:144: error: wrong number of template arguments (1, should be 2)
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:24: error: provided for ‘template<int* pytype, class T> struct boost::python::converter::pytype_object_manager_traits’
In file included from /usr/include/boost/python/docstring_options.hpp:8,
                 from /usr/include/boost/python.hpp:25,
                 from try.cpp:1:
/usr/include/boost/python/object/function.hpp:19: error: expected class-name before ‘{’ token
/usr/include/boost/python/object/function.hpp:27: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/object/function.hpp:46: error: ‘PyObject’ has not been declared
/usr/include/boost/python/object/function.hpp:46: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/python/enum.hpp:10,
                 from /usr/include/boost/python.hpp:26,
                 from try.cpp:1:
/usr/include/boost/python/object/enum_base.hpp:21: error: ‘boost::python::converter::to_python_function_t’ has not been declared
/usr/include/boost/python/object/enum_base.hpp:22: error: ‘boost::python::converter::convertible_function’ has not been declared
/usr/include/boost/python/object/enum_base.hpp:23: error: ‘boost::python::converter::constructor_function’ has not been declared
/usr/include/boost/python/object/enum_base.hpp:31: error: expected ‘;’ before ‘*’ token
In file included from /usr/include/boost/python.hpp:26,
                 from try.cpp:1:
/usr/include/boost/python/enum.hpp:31: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/enum.hpp:32: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/enum.hpp:33: error: ‘PyObject’ has not been declared
/usr/include/boost/python/enum.hpp:52: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/boost/python/enum.hpp:67: error: ‘void* boost::python::enum_<T>::convertible_from_python’ is not a static member of ‘struct boost::python::enum_<T>’
/usr/include/boost/python/enum.hpp:67: error: template definition of non-template ‘void* boost::python::enum_<T>::convertible_from_python’
/usr/include/boost/python/enum.hpp:67: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/enum.hpp:67: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/enum.hpp:80: error: variable or field ‘construct’ declared void
/usr/include/boost/python/enum.hpp:80: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/enum.hpp:80: error: ‘obj’ was not declared in this scope
/usr/include/boost/python/enum.hpp:80: error: expected primary-expression before ‘*’ token
/usr/include/boost/python/enum.hpp:80: error: ‘data’ was not declared in this scope
In file included from /usr/include/boost/python/exec.hpp:9,
                 from /usr/include/boost/python.hpp:29,
                 from try.cpp:1:
/usr/include/boost/python/str.hpp:407: error: wrong number of template arguments (1, should be 2)
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:24: error: provided for ‘template<int* pytype, class T> struct boost::python::converter::pytype_object_manager_traits’
In file included from /usr/include/boost/python/implicit.hpp:10,
                 from /usr/include/boost/python.hpp:33,
                 from try.cpp:1:
/usr/include/boost/python/converter/implicit.hpp:19: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/converter/implicit.hpp:29: error: expected ‘;’ before ‘static’
/usr/include/boost/python/converter/implicit.hpp:29: error: ‘PyObject’ has not been declared
In file included from /usr/include/boost/python.hpp:33,
                 from try.cpp:1:
/usr/include/boost/python/implicit.hpp: In function ‘void boost::python::implicitly_convertible(boost::type<Target>*, boost::type<U>*)’:
/usr/include/boost/python/implicit.hpp:24: error: ‘push_back’ is not a member of ‘boost::python::converter::registry’
In file included from /usr/include/boost/python/iterator.hpp:11,
                 from /usr/include/boost/python.hpp:37,
                 from try.cpp:1:
/usr/include/boost/python/object/iterator.hpp: In function ‘boost::python::api::object boost::python::objects::detail::demand_iterator_class(const char*, Iterator*, const NextPolicies&)’:
/usr/include/boost/python/object/iterator.hpp:120: error: template argument 1 is invalid
/usr/include/boost/python/object/iterator.hpp:120: error: invalid type in declaration before ‘(’ token
/usr/include/boost/python/object/iterator.hpp:123: error: request for member ‘get’ in ‘class_obj’, which is of non-class type ‘int’
In file included from /usr/include/boost/python.hpp:39,
                 from try.cpp:1:
/usr/include/boost/python/long.hpp: At global scope:
/usr/include/boost/python/long.hpp:61: error: wrong number of template arguments (1, should be 2)
/usr/include/boost/python/converter/pytype_object_mgr_traits.hpp:24: error: provided for ‘template<int* pytype, class T> struct boost::python::converter::pytype_object_manager_traits’
In file included from /usr/include/boost/python.hpp:40,
                 from try.cpp:1:
/usr/include/boost/python/lvalue_from_pytype.hpp:36: error: ‘execute’ declared as an ‘inline’ field
/usr/include/boost/python/lvalue_from_pytype.hpp:36: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/lvalue_from_pytype.hpp:44: error: expected ‘;’ before ‘}’ token
/usr/include/boost/python/lvalue_from_pytype.hpp:86: error: ‘PyTypeObject’ has not been declared
/usr/include/boost/python/lvalue_from_pytype.hpp:100: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/lvalue_from_pytype.hpp:110: error: expected ‘;’ before ‘static’
/usr/include/boost/python/lvalue_from_pytype.hpp:110: error: expected ‘;’ before ‘const’
/usr/include/boost/python/lvalue_from_pytype.hpp:112: error: expected ‘;’ before ‘}’ token
/usr/include/boost/python/lvalue_from_pytype.hpp: In constructor ‘boost::python::lvalue_from_pytype<Extractor, python_type>::lvalue_from_pytype()’:
/usr/include/boost/python/lvalue_from_pytype.hpp:93: error: missing template arguments before ‘,’ token
/usr/include/boost/python/lvalue_from_pytype.hpp:95: error: ‘get_pytype’ was not declared in this scope
In file included from /usr/include/boost/python.hpp:41,
                 from try.cpp:1:
/usr/include/boost/python/make_constructor.hpp: At global scope:
/usr/include/boost/python/make_constructor.hpp:35: error: expected ‘)’ before ‘*’ token
/usr/include/boost/python/make_constructor.hpp:38: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/make_constructor.hpp:44: error: expected ‘;’ before ‘private’
/usr/include/boost/python/make_constructor.hpp:69: error: expected ‘;’ before ‘*’ token
/usr/include/boost/python/make_constructor.hpp:89: error: expected initializer before ‘*’ token
/usr/include/boost/python/make_constructor.hpp:95: error: ‘template<class BaseArgs, class Offset> unsigned int boost::python::detail::arity(const boost::python::detail::offset_args<BaseArgs, Offset>&)’ redeclared as different kind of symbol
/usr/include/boost/python/detail/caller.hpp:53: error: previous declaration of ‘unsigned int boost::python::detail::arity’
In file included from /usr/include/boost/python.hpp:45,
                 from try.cpp:1:
/usr/include/boost/python/numeric.hpp:93: error: ‘PyObject’ has not been declared
/usr/include/boost/python/numeric.hpp:94: error: ‘PyObject’ has not been declared
/usr/include/boost/python/numeric.hpp:95: error: expected ‘;’ before ‘const’
In file included from /usr/include/boost/python/opaque_pointer_converter.hpp:15,
                 from /usr/include/boost/python.hpp:49,
                 from try.cpp:1:
/usr/include/boost/python/detail/dealloc.hpp:11: error: variable or field ‘dealloc’ declared void
/usr/include/boost/python/detail/dealloc.hpp:11: error: ‘PyObject’ was not declared in this scope
/usr/include/boost/python/detail/dealloc.hpp:11: error: ‘self’ was not declared in this scope
In file included from /usr/include/boost/python.hpp:49,
                 from try.cpp:1:
/usr/include/boost/python/opaque_pointer_converter.hpp:63: error: expected ‘;’ before ‘(’ token
/usr/include/boost/python/opaque_pointer_converter.hpp:71: error: expected ‘;’ before ‘static’
/usr/include/boost/python/opaque_pointer_converter.hpp:71: error: expected ‘;’ before ‘*’ token
try.cpp:33: error: expected ‘;’ at end of input
try.cpp:33: error: expected ‘}’ at end of input
In file included from /usr/include/boost/python.hpp:49,
                 from try.cpp:1:
/usr/include/boost/python/opaque_pointer_converter.hpp: In constructor ‘boost::python::opaque<Pointee>::opaque()’:
/usr/include/boost/python/opaque_pointer_converter.hpp:48: error: ‘type_object’ was not declared in this scope
/usr/include/boost/python/opaque_pointer_converter.hpp:51: error: there are no arguments to ‘PyType_Ready’ that depend on a template parameter, so a declaration of ‘PyType_Ready’ must be available
/usr/include/boost/python/opaque_pointer_converter.hpp: At global scope:
/usr/include/boost/python/opaque_pointer_converter.hpp:58: error: expected unqualified-id at end of input
/usr/include/boost/python/opaque_pointer_converter.hpp:58: error: expected ‘}’ at end of input
/usr/include/boost/python/opaque_pointer_converter.hpp:58: error: expected ‘}’ at end of input
In file included from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from try.cpp:1:
/usr/include/boost/python/object_core.hpp: In constructor ‘boost::python::api::object::object(const T&) [with T = boost::python::scope]’:
/usr/include/boost/python/scope.hpp:71:   instantiated from here
/usr/include/boost/python/object_core.hpp:326: error: ‘object_base_initializer’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:52,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&) [with A0 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:37:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:57,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&) [with A0 = long int, A1 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:40:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:62,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&) [with A0 = long int, A1 = long int, A2 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:43:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:67,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:46:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:72,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:49:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:77,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:52:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:82,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:55:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:87,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:58:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:92,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:61:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:97,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:64:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:102,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int, A10 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:67:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:107,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int, A10 = long int, A11 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:70:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:112,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int, A10 = long int, A11 = long int, A12 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:73:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:117,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&, const A13&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int, A10 = long int, A11 = long int, A12 = long int, A13 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:76:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/preprocessor/iteration/detail/iter/forward1.hpp:122,
                 from /usr/include/boost/python/tuple.hpp:65,
                 from /usr/include/boost/python/dict.hpp:12,
                 from /usr/include/boost/python.hpp:24,
                 from try.cpp:1:
/usr/include/boost/python/detail/make_tuple.hpp: In function ‘boost::python::tuple boost::python::make_tuple(const A0&, const A1&, const A2&, const A3&, const A4&, const A5&, const A6&, const A7&, const A8&, const A9&, const A10&, const A11&, const A12&, const A13&, const A14&) [with A0 = long int, A1 = long int, A2 = long int, A3 = long int, A4 = long int, A5 = long int, A6 = long int, A7 = long int, A8 = long int, A9 = long int, A10 = long int, A11 = long int, A12 = long int, A13 = long int, A14 = long int]’:
/usr/include/boost/preprocessor/iteration/detail/local.hpp:79:   instantiated from here
/usr/include/boost/python/detail/make_tuple.hpp:25: error: ‘PyTuple_SET_ITEM’ was not declared in this scope
In file included from /usr/include/boost/python/args.hpp:25,
                 from /usr/include/boost/python.hpp:11,
                 from try.cpp:1:
/usr/include/boost/python/object_core.hpp: In constructor ‘boost::python::api::object::object(const T&) [with T = boost::python::tuple]’:
/usr/include/boost/python/numeric.hpp:121:   instantiated from ‘void boost::python::numeric::array::resize(const Sequence&) [with Sequence = boost::python::tuple]’
/usr/include/boost/preprocessor/iteration/detail/local.hpp:37:   instantiated from here
/usr/include/boost/python/object_core.hpp:326: error: ‘object_base_initializer’ was not declared in this scope

```The strange thing is that when I compile a code utilizing boost_thread, it just compiled successfully. Below are some details of my setting/configuration.

Ubuntu version: 10.04 LTS
GCC version: 4.4.3 
Python: 2.6.5

Thanks in advance.

---

### Post by dwhitney67 on 2012-07-16
Try something like:
```

g++ -I/usr/include/python2.6 try.cpp -lboost_python -lpython2.6

```

---

### Post by alfa_80 on 2012-07-16
> **dwhitney67 said:**
> Try something like:
```

g++ -I/usr/include/python2.6 try.cpp -lboost_python -lpython2.6

```

Thanks a lot [dwhitney67]("http://ubuntuforums.org/member.php?u=322753"). It works. Your are great! What is my mistake actually according to my previous command, I wanna learn my mistake. Why don't we need to include '-I' for lboost_python? Why only for python2.6? Thanks in advance..

---

### Post by dwhitney67 on 2012-07-16
> **alfa_80 said:**
> Thanks a lot [dwhitney67]("http://ubuntuforums.org/member.php?u=322753"). It works. Your are great! What is my mistake actually according to my previous command, I wanna learn my mistake. Why don't we need to include '-I' for lboost_python? Why only for python2.6? Thanks in advance..

The -I option tells g++ where to find the appropriate header files related to Python 2.6; the Boost Python header file is dependent upon those.

As for the Boost Python library, it is dependent upon the Python C API library.

Thus the reason why all three specifications are needed to compile/link your application.

I personally do not dabble with Python, so that is the extent of the information I can offer.  Perhaps someone else can shed more details to satisfy your query.

---

### Post by alfa_80 on 2012-07-16
> **dwhitney67 said:**
> The -I option tells g++ where to find the appropriate header files related to Python 2.6; the Boost Python header file is dependent upon those.

As for the Boost Python library, it is dependent upon the Python C API library.

Thus the reason why all three specifications are needed to compile/link your application.

I personally do not dabble with Python, so that is the extent of the information I can offer.  Perhaps someone else can shed more details to satisfy your query.

Thanks a lot for the clarification and again for the fix, you've saved me from last 5 days tweaking this :-)

---

### Post by alfa_80 on 2012-07-17
> **dwhitney67 said:**
> The -I option tells g++ where to find the appropriate header files related to Python 2.6; the Boost Python header file is dependent upon those.

As for the Boost Python library, it is dependent upon the Python C API library.

Thus the reason why all three specifications are needed to compile/link your application.

I personally do not dabble with Python, so that is the extent of the information I can offer.  Perhaps someone else can shed more details to satisfy your query.

One last question. Why don't we need to put '-L' in our command, which normally people do.

---

### Post by dwhitney67 on 2012-07-17
The system libraries, which include libboost_python.so and libpython2.6.so, are identified/stored in the system's library cache.  The locations where these libraries reside are also referenced by GCC.

You can read more about the library cache by referencing the man-page for 'ldconfig' or running this command to list the search paths and libraries found:
```

ldconfig -v

```
For the search paths known by GCC, run this:
```

g++ --print-search-dirs

```
For libraries that fall outside of the well-known paths or are not identified by ldconfig, the -L option would need to be specified.  During runtime of the application, LD_LIBRARY_PATH would need to be set.

P.S.  I'm not 100% sure that the library cache has a bearing when linking object files, but it is definitely referenced when running an application.

---

### Post by alfa_80 on 2012-07-17
> **dwhitney67 said:**
> The system libraries, which include libboost_python.so and libpython2.6.so, are identified/stored in the system's library cache.  The locations where these libraries reside are also referenced by GCC.

You can read more about the library cache by referencing the man-page for 'ldconfig' or running this command to list the search paths and libraries found:
```

ldconfig -v

```For the search paths known by GCC, run this:
```

g++ --print-search-dirs

```For libraries that fall outside of the well-known paths or are not identified by ldconfig, the -L option would need to be specified.  During runtime of the application, LD_LIBRARY_PATH would need to be set.

P.S.  I'm not 100% sure that the library cache has a bearing when linking object files, but it is definitely referenced when running an application.

Thanks a lot for the detail explanation. That helps a lot :-)

---

