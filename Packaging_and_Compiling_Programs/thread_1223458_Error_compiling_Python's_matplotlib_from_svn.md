---
title: "Error compiling Python's matplotlib from svn"
date: 2009-07-26
forum: Packaging and Compiling Programs
---

### Post by PC_load_letter on 2009-07-26
Hi everyone, 
   I followed the instructions on the matplotlib's official web page. I installed all the three required external libraries along with their dev versions. They are: libpng, freetype, and of course I have Pythin 2.6 and Numpy installed.  Still I got the following gcc error:

```
~/matplotlib$ python setup.py install
============================================================================
BUILDING MATPLOTLIB
            matplotlib: 0.98.6svn
                python: 2.6.2 (release26-maint, Apr 19 2009, 01:56:41)  [GCC
                        4.3.3]
              platform: linux2

REQUIRED DEPENDENCIES
                 numpy: 1.2.1
             freetype2: found, but unknown version (no pkg-config)

OPTIONAL BACKEND DEPENDENCIES
                libpng: found, but unknown version (no pkg-config)
               Tkinter: no
                        * Using default library and include directories for
                        * Tcl and Tk because a Tk window failed to open.
                        * You may need to define DISPLAY for Tk to work so
                        * that setup can determine where your libraries are
                        * located. Tkinter present, but header files are not
                        * found. You may need to install development
                        * packages.
              wxPython: 2.8.9.1
                        * WxAgg extension not required for wxPython >= 2.8
                        * You may need to install 'dev' package(s) to
                        * provide header files.
                  Gtk+: no
                        * Could not find Gtk+ headers in any of
                        * '/usr/local/include', '/usr/include', '.'
       Mac OS X native: no
                    Qt: no
                   Qt4: no
                 Cairo: 1.4.12

OPTIONAL DATE/TIMEZONE DEPENDENCIES
              datetime: present, version unknown
              dateutil: 1.4.1
                  pytz: 2008h

OPTIONAL USETEX DEPENDENCIES
                dvipng: no
           ghostscript: 8.64
                 latex: 3.141592
               pdftops: 0.10.5

[Edit setup.cfg to suppress the above messages]
============================================================================
pymods ['pylab']
packages ['matplotlib', 'matplotlib.backends', 'matplotlib.projections', 'mpl_toolkits', 'mpl_toolkits.mplot3d', 'mpl_toolkits.axes_grid', 'matplotlib.sphinxext', 'matplotlib.numerix', 'matplotlib.numerix.mlab', 'matplotlib.numerix.ma', 'matplotlib.numerix.linear_algebra', 'matplotlib.numerix.random_array', 'matplotlib.numerix.fft', 'matplotlib.delaunay']
running install
running build
running build_py
copying lib/matplotlib/mpl-data/matplotlibrc -> build/lib.linux-i686-2.6/matplotlib/mpl-data
copying lib/matplotlib/mpl-data/matplotlib.conf -> build/lib.linux-i686-2.6/matplotlib/mpl-data
running build_ext
building 'matplotlib.ft2font' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DPY_ARRAYAUNIQUE_SYMBOL=MPL_ARRAY_API -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/local/include -I/usr/include -I. -I/usr/lib/python2.6/dist-packages/numpy/core/include/freetype2 -I/usr/local/include/freetype2 -I/usr/include/freetype2 -I./freetype2 -I/usr/include/python2.6 -c src/ft2font.cpp -o build/temp.linux-i686-2.6/src/ft2font.o
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from ./CXX/Extensions.hxx:48,
                 from src/ft2font.h:4,
                 from src/ft2font.cpp:1:
./CXX/WrapPython.h:42:20: error: Python.h: No such file or directory
In file included from ./CXX/Extensions.hxx:50,
                 from src/ft2font.h:4,
                 from src/ft2font.cpp:1:
./CXX/Config.hxx:112:2: error: #error not defined PY_MAJOR_VERSION
In file included from /usr/include/c++/4.3/ext/hash_map:64,
                 from ./CXX/Extensions.hxx:68,
                 from src/ft2font.h:4,
                 from src/ft2font.cpp:1:
/usr/include/c++/4.3/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated.
In file included from /usr/lib/python2.6/dist-packages/numpy/core/include/numpy/arrayobject.h:14,
                 from src/ft2font.cpp:5:
/usr/lib/python2.6/dist-packages/numpy/core/include/numpy/ndarrayobject.h:114:2: error: #error Must use Python with unicode enabled.
In file included from ./CXX/Exception.hxx:44,
                 from ./CXX/Objects.hxx:44,
                 from ./CXX/Extensions.hxx:51,
                 from src/ft2font.h:4,
                 from src/ft2font.cpp:1:
./CXX/IndirectPythonInterface.hxx:50: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:51: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:52: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:53: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:55: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:56: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:57: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:58: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:59: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:60: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:61: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:62: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:63: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:64: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:65: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:66: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:67: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:68: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:69: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:70: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:71: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:72: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:73: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:74: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:75: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:76: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:81: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:93: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:95: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:96: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:101: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:102: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:102: error: ‘o’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:104: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:105: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:105: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:107: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:108: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:108: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:110: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:111: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:111: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:113: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:114: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:114: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:116: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:117: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:117: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:119: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:120: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:120: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:122: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:123: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:123: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:125: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:126: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:126: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:128: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:129: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:129: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:131: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:132: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:132: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:134: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:135: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:135: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:137: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:138: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:138: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:140: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:141: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:141: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:143: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:144: error: redefinition of ‘bool Py::_List_Check’
./CXX/IndirectPythonInterface.hxx:102: error: ‘bool Py::_List_Check’ previously defined here
./CXX/IndirectPythonInterface.hxx:144: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:144: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:146: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:147: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:147: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:149: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:150: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:150: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:152: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:153: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:153: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:155: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:156: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:156: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:158: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:159: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:159: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:161: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:162: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:162: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:164: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:165: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:165: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:167: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:168: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:168: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:170: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:171: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:171: error: ‘v’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:173: error: expected constructor, destructor, or type conversion before ‘*’ token
./CXX/IndirectPythonInterface.hxx:174: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:174: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:192: error: variable or field ‘_XINCREF’ declared void
./CXX/IndirectPythonInterface.hxx:192: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:192: error: ‘op’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:193: error: variable or field ‘_XDECREF’ declared void
./CXX/IndirectPythonInterface.hxx:193: error: ‘PyObject’ was not declared in this scope
./CXX/IndirectPythonInterface.hxx:193: error: ‘op’ was not declared in this scope
In file included from ./CXX/Objects.hxx:44,
                 from ./CXX/Extensions.hxx:51,
                 from src/ft2font.h:4,
                 from src/ft2font.cpp:1:
./CXX/Exception.hxx:70: error: expected `)' before ‘*’ token
./CXX/Exception.hxx:75: error: expected `)' before ‘*’ token
./CXX/Exception.hxx: In constructor ‘Py::Exception::Exception(const std::string&)’:
./CXX/Exception.hxx:67: error: ‘_Exc_RuntimeError’ is not a member of ‘Py’
./CXX/Exception.hxx:67: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In member function ‘void Py::Exception::clear()’:
./CXX/Exception.hxx:80: error: ‘PyErr_Clear’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::TypeError::TypeError(const std::string&)’:
./CXX/Exception.hxx:122: error: ‘_Exc_TypeError’ is not a member of ‘Py’
./CXX/Exception.hxx:122: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::IndexError::IndexError(const std::string&)’:
./CXX/Exception.hxx:132: error: ‘_Exc_IndexError’ is not a member of ‘Py’
./CXX/Exception.hxx:132: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::AttributeError::AttributeError(const std::string&)’:
./CXX/Exception.hxx:142: error: ‘_Exc_AttributeError’ is not a member of ‘Py’
./CXX/Exception.hxx:142: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::NameError::NameError(const std::string&)’:
./CXX/Exception.hxx:152: error: ‘_Exc_NameError’ is not a member of ‘Py’
./CXX/Exception.hxx:152: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::RuntimeError::RuntimeError(const std::string&)’:
./CXX/Exception.hxx:162: error: ‘_Exc_RuntimeError’ is not a member of ‘Py’
./CXX/Exception.hxx:162: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::SystemError::SystemError(const std::string&)’:
./CXX/Exception.hxx:172: error: ‘_Exc_SystemError’ is not a member of ‘Py’
./CXX/Exception.hxx:172: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::KeyError::KeyError(const std::string&)’:
./CXX/Exception.hxx:182: error: ‘_Exc_KeyError’ is not a member of ‘Py’
./CXX/Exception.hxx:182: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::ValueError::ValueError(const std::string&)’:
./CXX/Exception.hxx:193: error: ‘_Exc_ValueError’ is not a member of ‘Py’
./CXX/Exception.hxx:193: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::OverflowError::OverflowError(const std::string&)’:
./CXX/Exception.hxx:203: error: ‘_Exc_OverflowError’ is not a member of ‘Py’
./CXX/Exception.hxx:203: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::ZeroDivisionError::ZeroDivisionError(const std::string&)’:
./CXX/Exception.hxx:213: error: ‘_Exc_ZeroDivisionError’ is not a member of ‘Py’
./CXX/Exception.hxx:213: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::FloatingPointError::FloatingPointError(const std::string&)’:
./CXX/Exception.hxx:223: error: ‘_Exc_FloatingPointError’ is not a member of ‘Py’
./CXX/Exception.hxx:223: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::MemoryError::MemoryError(const std::string&)’:
./CXX/Exception.hxx:233: error: ‘_Exc_MemoryError’ is not a member of ‘Py’
./CXX/Exception.hxx:233: error: ‘PyErr_SetString’ was not declared in this scope
./CXX/Exception.hxx: In constructor ‘Py::SystemExit::SystemExit(const std::string&)’:
./CXX/Exception.hxx:243: error: ‘_Exc_SystemExit’ is not a member of ‘Py’
./CXX/Exception.hxx:243: error: ‘PyErr_SetString’ was not declared in this scope
In file included from ./CXX/Extensions.hxx:51,
                 from src/ft2font.h:4,
                 from src/ft2font.cpp:1:
./CXX/Objects.hxx: At global scope:
./CXX/Objects.hxx:66: error: expected initializer before ‘*’ token
./CXX/Objects.hxx:74: error: expected initializer before ‘*’ token
./CXX/Objects.hxx:150: error: ISO C++ forbids declaration of ‘PyObject’ with no type
./CXX/Objects.hxx:150: error: expected ‘;’ before ‘*’ token
./CXX/Objects.hxx:154: error: ‘PyObject’ has not been declared
./CXX/Objects.hxx:175: error: expected `)' before ‘*’ token
src/ft2font.cpp:1936: error: expected `}' at end of input
./CXX/Objects.hxx: In member function ‘void Py::Object::set(int*, bool)’:
./CXX/Objects.hxx:157: error: ‘p’ was not declared in this scope
./CXX/Objects.hxx:160: error: ‘_XINCREF’ is not a member of ‘Py’
./CXX/Objects.hxx: In member function ‘void Py::Object::release()’:
./CXX/Objects.hxx:167: error: ‘_XDECREF’ is not a member of ‘Py’
./CXX/Objects.hxx:167: error: ‘p’ was not declared in this scope
./CXX/Objects.hxx: At global scope:
./CXX/Objects.hxx:169: error: expected unqualified-id at end of input
./CXX/Objects.hxx:169: error: expected `}' at end of input
error: command 'gcc' failed with exit status 1

```

Any idea what's missing, or what did I do wrong? 

Thanks.

---

### Post by PC_load_letter on 2009-07-26
ok, so here is an update. Using the **apt-get build-dep** command I built all the dependencies for python-matplotlib (for the installed version), which installed 248 MB of stuff.

Anyway, I then proceeded to install the latest version of matplotlib from svn as in 1st post, got a permission denied somewhere so I went with: **sudo python setup.py install** from the /matplotlib directory as above. Everything went without a hitch and I included the output below. 

```
============================================================================
BUILDING MATPLOTLIB
            matplotlib: 0.98.6svn
                python: 2.6.2 (release26-maint, Apr 19 2009, 01:56:41)  [GCC
                        4.3.3]
              platform: linux2

REQUIRED DEPENDENCIES
                 numpy: 1.2.1
             freetype2: 9.20.3

OPTIONAL BACKEND DEPENDENCIES
                libpng: 1.2.27
               Tkinter: Tkinter: 70220, Tk: 8.5, Tcl: 8.5
              wxPython: 2.8.9.1
                        * WxAgg extension not required for wxPython >= 2.8
                  Gtk+: gtk+: 2.16.1, glib: 2.20.1, pygtk: 2.14.1,
                        pygobject: 2.16.1
       Mac OS X native: no
                    Qt: Qt: 3.3.8, PyQt: 3.17.6
                   Qt4: Qt: 4.5.0, PyQt4: 4.4.4
                 Cairo: 1.4.12

OPTIONAL DATE/TIMEZONE DEPENDENCIES
              datetime: present, version unknown
              dateutil: 1.4.1
                  pytz: 2008h

OPTIONAL USETEX DEPENDENCIES
                dvipng: 1.11
           ghostscript: 8.64
                 latex: 3.141592
               pdftops: 0.10.5

[Edit setup.cfg to suppress the above messages]
============================================================================
pymods ['pylab']
packages ['matplotlib', 'matplotlib.backends', 'matplotlib.projections', 'mpl_toolkits', 'mpl_toolkits.mplot3d', 'mpl_toolkits.axes_grid', 'matplotlib.sphinxext', 'matplotlib.numerix', 'matplotlib.numerix.mlab', 'matplotlib.numerix.ma', 'matplotlib.numerix.linear_algebra', 'matplotlib.numerix.random_array', 'matplotlib.numerix.fft', 'matplotlib.delaunay']
running install
running build
running build_py
copying lib/matplotlib/mpl-data/matplotlibrc -> build/lib.linux-i686-2.6/matplotlib/mpl-data
copying lib/matplotlib/mpl-data/matplotlib.conf -> build/lib.linux-i686-2.6/matplotlib/mpl-data
running build_ext
running install_lib
copying build/lib.linux-i686-2.6/matplotlib/mpl-data/matplotlib.conf -> /usr/local/lib/python2.6/dist-packages/matplotlib/mpl-data
copying build/lib.linux-i686-2.6/matplotlib/mpl-data/matplotlibrc -> /usr/local/lib/python2.6/dist-packages/matplotlib/mpl-data
running install_egg_info
Removing /usr/local/lib/python2.6/dist-packages/matplotlib-0.98.6svn.egg-info
Writing /usr/local/lib/python2.6/dist-packages/matplotlib-0.98.6svn.egg-info

```

Problem is that I still get the following from the Python terminal

```
$ python 
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from pylab import *
>>> print matplotlib.__version__
0.98.5.2

```
The svn version I was trying to install is 0.98.6, now what?
Any help is appreciated. Thanks.

---

### Post by PC_load_letter on 2009-07-26
Another update: 

So I installed the egg file with the **easy_install**, I'm still a Python newbie I guess :redface:

Now, when I try to import functions from the module pylab I get the message:
```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python2.6/dist-packages/matplotlib-0.98.6svn-py2.6-linux-i686.egg/pylab.py", line 1, in <module>
    from matplotlib.pylab import *
ImportError: No module named pylab

```

This error is displayed when I try to import from the Python terminal, but when I do it from the interactive terminal 'ipython' everything works and it now shows that matplotlib w/ the new version. 

So, what's the deal? Why can't Python terminal find pyplot?

---

### Post by PC_load_letter on 2009-07-27
I tried all the above on my other Ubuntu 9.04 laptop and everything went very smoothly, with no single error. Only difference I could tell is that my 2nd laptop did not have the matplotlib installed from the repos. So I went back to the 1st laptop and uninstalled matplotlib from Synaptic, then repeated the install-from-svn procedure and it was a winner!

---

### Post by eddin on 2009-08-01
Thank you. I have tried to build matplotlib from the svn version without success. So much so that I have to log on to my windows machine, and matplotlib rc 0.99 install in windows without a hitch.

Your instruction on using apt-get build-dep python-matplotlib really helps.

Now I need to do some 3D plots.

---

### Post by PC_load_letter on 2009-08-02
You're welcome! Yeah the 3D plotting was probably the only reason why I wanted to install this version. Have fun!

---

### Post by Felix_ on 2009-11-08
That helped a lot.  Thank you!  Time to play with some 3D plot animations :p

---

