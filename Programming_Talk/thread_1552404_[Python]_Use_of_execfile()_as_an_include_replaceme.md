---
title: "[Python] Use of execfile() as an include replacement"
date: 2010-08-13
forum: Programming Talk
---

### Post by durand on 2010-08-13
Hi,

I'm wondering if there's a better solution than what I'm doing right now in the context of web applications. Basically, I thought it would be pretty efficient to just have one python script which sets up the environment, loads the template engine and so on and then just get all the other scripts (which are also separate web pages) to execfile() that one rather than doing the exact same thing in every file.

I've read a bit about the security risks of execfile() but I'm not too bothered about that because its going to be only trusted code running.

An example of what I'm doing:

initiate.py
```

#!/usr/bin/env python

## Add the right paths into PATH
import os
import sys
sys.path.insert(0, os.path.abspath("libraries"))
sys.path.insert(0, os.path.abspath("../"))

## Enable error catching and nicer tracebacks
import cgitb
cgitb.enable()

## Load up jinja
from jinja2 import Environment, PackageLoader
environment = Environment(loader=PackageLoader('website', 'templates'))

import __builtin__
import cgi

from downloads.pydownloads import downloads as pyd
__builtin__.GET_VARIABLES = cgi.FieldStorage()

def pydo(arguments={}):        
    variables = pyd.CLI_Arguments()
    for argument in arguments:
        if type(arguments[argument]) == type(""):
            exec('variables.%s = "%s"'%(argument, arguments[argument]))
        else:
            exec('variables.%s = %s'%(argument, arguments[argument]))
    __builtin__.CLI_ARGUMENTS = variables.get()
    return pyd.__init__()


```

home.py
```

#!/usr/bin/env python
execfile('initiate.py')
template = environment.get_template('home.html')
print "Content-type: text/html\n"
print template.render({'source':open(__file__).read(), 'pydo':pydo}).encode('utf-8')

```

Is there a better way to do something like this?
Thanks!

---

### Post by Bachstelze on 2010-08-13
```
import initiate
```

should work.

---

### Post by durand on 2010-08-13
The idea is to get all those modules (cgi,sys, etc) directly into the new script without having to use initiate.cgi, etc

---

### Post by DanielWaterworth on 2010-08-13
You are using a PHP mindset. Python has import :)

---

### Post by durand on 2010-08-13
I'm really not. I've pretty much only used python. I just know that php has that but so does django which is where I got the idea from. Import doesn't do it as I want.

---

### Post by durand on 2010-08-14
For future reference, I ended up using
```
import sys, os
os.fchdir(os.open(os.path.abspath('./'), os.O_RDONLY))
sys.path.insert(0, os.getcwd())
from initiate import environment, pydo

```
instead of execfile()

---

### Post by DanielWaterworth on 2010-08-14
```
import sys, os
os.fchdir(os.open(os.path.abspath('./'), os.O_RDONLY))
sys.path.insert(0, os.getcwd())
```

can go in initiate. I assume you only want to do it once.

I'd be very surprised if Django used raw execfile.

---

### Post by durand on 2010-08-14
It can't because initiate.py isn't always in the same directory so I need to change it first. I'm not sure what django internally uses but their templates have an {% include %} tag which is essentially the same thing.

---

### Post by DanielWaterworth on 2010-08-14
That's completely different! And, furthermore, they advise you to use {% extend %} where you can.

__file__ is the filename.
the cwd is different.

---

### Post by durand on 2010-08-14
Yeah, I do use extend. I'm just saying that django does have include :)
When I import initiate without changing directory, jinja can't find its own modules. I don't really know of another way to do it.

---

### Post by DanielWaterworth on 2010-08-14
You want sys.path.append. I have:

```
import os, sys
sys.path.append(os.path.dirname(__file__))
```

At the beginning of my wsgi application. You can't rely on the cwd being what you set it too (in web applications).

---

### Post by durand on 2010-08-14
Oh ok. Thanks for that!

---

