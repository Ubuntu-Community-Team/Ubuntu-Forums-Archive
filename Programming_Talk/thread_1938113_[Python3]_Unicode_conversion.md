---
title: "[Python3] Unicode conversion"
date: 2012-03-09
forum: Programming Talk
---

### Post by ntanitime on 2012-03-09
Hi,
which is the best way to convert a <class 'bytes'> in a <class 'str'>?

using "decode()"

```

import urllib.request
import urllib.error

def get_page( link ):
     try:
          f = urllib.request.urlopen( link )
     except:
          return False
     else:
          page = f.read().decode()
          return page 

F = get_page('http://www.wordreference.com/enit/ultimately')
```Or is better to use "str()" :

```

import urllib.request
import urllib.error

def get_page( link ):
     try:
          f = urllib.request.urlopen( link )
     except:
          return False
     else:
          page = f.read()
          return str(page) ####### 

F = get_page('http://www.wordreference.com/enit/ultimately')
```

---

### Post by ofnuts on 2012-03-09
str() has nothing to do with Unicode. It is just a printable version of the object. Use decode() with an explicit encoding.

---

