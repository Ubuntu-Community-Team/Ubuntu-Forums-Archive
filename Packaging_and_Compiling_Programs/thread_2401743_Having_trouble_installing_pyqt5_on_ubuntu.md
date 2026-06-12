---
title: "Having trouble installing pyqt5 on ubuntu"
date: 2018-09-22
forum: Packaging and Compiling Programs
---

### Post by lance bermudez on 2018-09-22
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.5 LTS"

can not upgrade yet to the 18 version of ubuntu

python 3.7 compiled from source
```

./configure --prefix=$HOME/Python-3.7.0 --enable-shared --with-pydebug LDFLAGS="-Wl,--rpath=$HOME/Python-3.7.0/lib" CPPFLAGS="-I$HOME/Python-3.7.0/include"; make; make test; make altinstall

```

python -m pip install pyqt5 error
```

:~/Python-3.7.0/bin$ ./python3.7 -m pip install pyqt5
/home/lance/Python-3.7.0/lib/python3.7/site-packages/pip/_vendor/html5lib/_trie/_base.py:3: DeprecationWarning: Using or importing the ABCs from 'collections' instead of from 'collections.abc' is deprecated, and in 3.8 it will stop working
  from collections import Mapping
/home/lance/Python-3.7.0/lib/python3.7/site-packages/pip/_vendor/pyparsing.py:943: DeprecationWarning: Using or importing the ABCs from 'collections' instead of from 'collections.abc' is deprecated, and in 3.8 it will stop working
  collections.MutableMapping.register(ParseResults)
/home/lance/Python-3.7.0/lib/python3.7/site-packages/pip/_vendor/pyparsing.py:3245: DeprecationWarning: Using or importing the ABCs from 'collections' instead of from 'collections.abc' is deprecated, and in 3.8 it will stop working
  elif isinstance( exprs, collections.Iterable ):
/home/lance/Python-3.7.0/lib/python3.7/site-packages/pip/_internal/pep425tags.py:255: DeprecationWarning: the imp module is deprecated in favour of importlib; see the module's documentation for alternative uses
  import imp
Collecting pyqt5
/home/lance/Python-3.7.0/lib/python3.7/site-packages/pip/_vendor/msgpack/fallback.py:222: PendingDeprecationWarning: encoding is deprecated, Use raw=False instead.
  PendingDeprecationWarning)
  Using cached https://files.pythonhosted.org/packages/3a/c7/4a9bec78c864051051b41b4cc76672ecc232e6dc7dbb91a5f8ff6f20ff64/PyQt5-5.11.2-5.11.1-cp35.cp36.cp37.cp38-abi3-manylinux1_x86_64.whl
Collecting PyQt5_sip<4.20,>=4.19.11 (from pyqt5)
  Could not find a version that satisfies the requirement PyQt5_sip<4.20,>=4.19.11 (from pyqt5) (from versions: )
No matching distribution found for PyQt5_sip<4.20,>=4.19.11 (from pyqt5)

```

---

