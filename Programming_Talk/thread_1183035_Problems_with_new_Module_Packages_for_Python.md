---
title: "Problems with new Module Packages for Python"
date: 2009-06-09
forum: Programming Talk
---

### Post by Krijk on 2009-06-09
I'm trying to publish some modules I've written and I'm having errors with publishing packages. The structure is (files in attachment):

```
testpackage1/
	__init__.py
	test1/
		__init__.py
		test1.py
	test2/
		__init__.py
		test2.py
```


```

#!/usr/bin/env python!#


def print2(s):
	print (s)

```

I published them to /usr/lib/python2.5/site-packages/ which is included in the Search Path ( sys.path ). When I import them and try to run a function I keep getting this error:

**AttributeError: 'module' object has no attribute 'print2'**

I imported the package manually and through distutils (followed the instructions of [http://docs.python.org/distutils/introduction.html](http://docs.python.org/distutils/introduction.html) ) but every time I get the same AtributeError. When put the test1.py and test2.py in the root of site-packages the functions work.

Obviously I'm doing something wrong?  I've searched the Internet and tried a lot of alternatives, so any advice is welcome.

---

### Post by sub2007 on 2009-06-12
What import function are you using? Should be something like:
[php]from testpackage1.test2 import test2[/php]
Then call the function as
[php]test2.print2("string")[/php]

Or any variation of that. Important thing is that there are two test2 modules that both need to be referenced.

---

