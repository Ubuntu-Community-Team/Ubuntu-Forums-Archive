---
title: "SWIG and X11 extension, Python"
date: 2017-10-01
forum: Programming Talk
---

### Post by 3djake on 2017-10-01
Hello,

I want to be able to use Xcomposite from Python, I lack practice in C and have not used SWIG before.

Here are the steps I am using:

Clone libxcomposite from git git://git.debian.org/git/pkg-xorg/lib/libxcomposite

then create a SWIG interface file like this 
```
%module xcomposite
%{
#include "xcompositeint.h"
%}

%include "src/xcompositeint.h"
```

create a setup.py file using distutils

```
from distutils.core import setup, Extension

name = "xcomposite"
version = "0.5"

setup(name=name, version=version,
ext_modules=[Extension(name='_xcomposite',
sources=["xcomposite.i", "src/Xcomposite.c"],
include_dirs=['src', 'include'])
])
```

When I try to import it I get "undefined symbol: _XUnlockMutex_fn" which is defined in Xlibint

I also have other undefined symbols when using ldd -r
```
undefined symbol: _XUnlockMutex_fn	(./_xcomposite.cpython-35m-x86_64-linux-gnu.so)
undefined symbol: _XLockMutex_fn	(./_xcomposite.cpython-35m-x86_64-linux-gnu.so)
undefined symbol: _Xglobal_lock	(./_xcomposite.cpython-35m-x86_64-linux-gnu.so)
undefined symbol: _XReply	(./_xcomposite.cpython-35m-x86_64-linux-gnu.so)
undefined symbol: _XGetRequest	(./_xcomposite.cpython-35m-x86_64-linux-gnu.so)

```

Am I not linking something, or is there a better way to make the Xcomposite library callable from python?

Thanks.
Regards, Jake.

---

### Post by 3djake on 2017-10-01
Linking the X11 library seemed to resolve the issue.

I just added the following to my setup.py script
libraries=["X11"])

---

