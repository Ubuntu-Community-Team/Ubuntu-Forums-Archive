---
title: "Python.h missing, yet python-dev installed!"
date: 2008-01-08
forum: Programming Talk
---

### Post by sipickles on 2008-01-08
Hi,

this is very frustrating.

Can anyone explain why I cannot find python.h even tho python and python-dev packages are both installed?

Here is the output from locate python.h:

```
simon@simon-linux:~$ locate python.h
/usr/include/dbus-1.0/dbus/dbus-python.h
/usr/include/boost/parameter/python.hpp
/usr/include/boost/python.hpp
/usr/include/boost/python/converter/shared_ptr_to_python.hpp
/usr/include/boost/python/converter/return_from_python.hpp
/usr/include/boost/python/converter/shared_ptr_from_python.hpp
/usr/include/boost/python/converter/arg_to_python.hpp
/usr/include/boost/python/converter/arg_from_python.hpp
/usr/include/boost/python/converter/from_python.hpp
/usr/include/boost/python/converter/obj_mgr_arg_from_python.hpp
/usr/include/boost/python/register_ptr_to_python.hpp
/usr/include/boost/python/detail/wrap_python.hpp
/usr/include/boost/python/arg_from_python.hpp
/usr/local/boost_1_34_1/libs/parameter/doc/html/python.html
/usr/local/boost_1_34_1/libs/graph/doc/python.html
/usr/local/boost_1_34_1/libs/python/doc/v2/register_ptr_to_python.html
/usr/local/boost_1_34_1/libs/python/doc/v2/python.html
/usr/local/boost_1_34_1/boost/parameter/python.hpp
/usr/local/boost_1_34_1/boost/python.hpp
/usr/local/boost_1_34_1/boost/python/converter/shared_ptr_to_python.hpp
/usr/local/boost_1_34_1/boost/python/converter/return_from_python.hpp
/usr/local/boost_1_34_1/boost/python/converter/shared_ptr_from_python.hpp
/usr/local/boost_1_34_1/boost/python/converter/arg_to_python.hpp
/usr/local/boost_1_34_1/boost/python/converter/arg_from_python.hpp
/usr/local/boost_1_34_1/boost/python/converter/from_python.hpp
/usr/local/boost_1_34_1/boost/python/converter/obj_mgr_arg_from_python.hpp
/usr/local/boost_1_34_1/boost/python/register_ptr_to_python.hpp
/usr/local/boost_1_34_1/boost/python/detail/wrap_python.hpp
/usr/local/boost_1_34_1/boost/python/arg_from_python.hpp
/usr/share/doc/libxslt1-dev/python.html
/usr/share/doc/python2.5/html/lib/python.html
/usr/share/doc/python/python-policy.html/ch-python.html
/home/simon/.Trash/test/libs/graph/doc/python.html
/home/simon/.Trash/test/libs/python/doc/v2/register_ptr_to_python.html
/home/simon/.Trash/test/libs/python/doc/v2/python.html
/home/simon/.Trash/test/libs/parameter/doc/html/python.html
/home/simon/.Trash/test/boost/python.hpp
/home/simon/.Trash/test/boost/python/detail/wrap_python.hpp
/home/simon/.Trash/test/boost/python/arg_from_python.hpp
/home/simon/.Trash/test/boost/python/converter/return_from_python.hpp
/home/simon/.Trash/test/boost/python/converter/from_python.hpp
/home/simon/.Trash/test/boost/python/converter/shared_ptr_to_python.hpp
/home/simon/.Trash/test/boost/python/converter/arg_from_python.hpp
/home/simon/.Trash/test/boost/python/converter/obj_mgr_arg_from_python.hpp
/home/simon/.Trash/test/boost/python/converter/arg_to_python.hpp
/home/simon/.Trash/test/boost/python/converter/shared_ptr_from_python.hpp
/home/simon/.Trash/test/boost/python/register_ptr_to_python.hpp
/home/simon/.Trash/test/boost/parameter/python.hpp
 
```

Thanks for your help

Simon

---

### Post by sipickles on 2008-01-08
doh!

python.h is actually Python.h

---

