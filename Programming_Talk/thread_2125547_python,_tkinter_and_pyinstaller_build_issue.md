---
title: "python, tkinter and pyinstaller build issue"
date: 2013-03-14
forum: Programming Talk
---

### Post by thor0298 on 2013-03-14
I've done python scripting but this is my first shot at making a self contained executable.  
I have run it in pyscriptor and the code works.  I also tried py2exe but was not a self 
contained exe file.

here is my code 

import Tkinter 
from random import Random 
class simpleapp_tk(Tkinter.Tk):    
def [B]init__(self,parent):        
Tkinter.Tk.__init__(self,parent)        
self.parent = parent        
self.initialize() 

here is the error: Traceback (most recent call last):  
File "build.py", line 839, in <module>    
build(sys.argv[1])  File "build.py", line 76, in build    
exec open(spec, 'r').read()+'\n'  
File "<string>", line 113, in <module>  
File "<string>", line 18, in __init
[/B]NameError: global name 'Tkinter' is not defined

---

### Post by nidzo732 on 2013-03-14
Please use the code tags. As you know, indentation in Python is very important so we can only guess what you are trying to do here.
One more question, which version of Python are you using? If you are using Python 3, you should replace 
```

import Tkinter

```
with
```

import tkinter

```
The "T" in tkinter is lowercase in Python 3.

---

