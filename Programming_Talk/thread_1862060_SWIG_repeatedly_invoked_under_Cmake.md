---
title: "SWIG repeatedly invoked under Cmake"
date: 2011-10-16
forum: Programming Talk
---

### Post by Colin@oxford on 2011-10-16
I have have a small, mainly C++,  project that uses CMake as its build system.  I need to add a Python interface to it.  The CMakeLists.txt for the swig/python directory looks like this:
```


FIND_PACKAGE(SWIG )

if (NOT SWIG_FOUND)
   return()
endif()

INCLUDE(${SWIG_USE_FILE})

FIND_PACKAGE(PythonLibs)
INCLUDE_DIRECTORIES(${PYTHON_INCLUDE_PATH})

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/../headers)
SET(FILES my_code.i)
SET(CMAKE_SWIG_FLAGS "")


SET_SOURCE_FILES_PROPERTIES(${FILES} PROPERTIES CPLUSPLUS ON)
SWIG_ADD_MODULE(my_extension python ${FILES})
SWIG_LINK_LIBRARIES(my_extension my_lib ${PYTHON_LIBRARIES})

```

This works but, rather annoyingly, it runs SWIG every time.

How I can make swig aware of the non-changing nature of the .i (and included .h) files?

Secondly, how do I get this to install the generated files (both my_extension.py and _my_extension.so) to the right place?  Preferably taking note of the CMAKE_INSTALL_PREFIX so that it can be installed locally rather than under /usr.

---

