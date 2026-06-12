---
title: "Py2exe error: Missing Cairo module"
date: 2007-05-14
forum: Programming Talk
---

### Post by jae1227 on 2007-05-14
I an using py2exe to make a exe for DeVeDe. I used a standard setup.py file:
```
from distutils.core import setup
import py2exe

setup(console=['devede.py']
```

Then I ran:
```
python setup.py install
python setup.py py2exe
```

It works with out any error. But when I execute the .exe it gives me this:
```
C:\cygwin_program\devede-2.13\dist>devede.exe
Traceback (most recent call last):
  File "devede.py", line 25, in <module>
  File "gtk\__init__.pyc", line 48, in <module>
  File "gtk\_gtk.pyc", line 12, in <module>
  File "gtk\_gtk.pyc", line 10, in __load
ImportError: No module named cairo
```

I really don't know what to do. I think there might be a way just to drag a file over to get it to work but don't know where to put it. I am uploading my dist folder so anyone that wants to look at it can. Here is the link: [HTML]http://www.sharebigfile.com/file/169102/dist-zip.html[/HTML]. Hope someone can help. I have DeVeDe running fine on windows. If use python to run the .py it works great.

---

