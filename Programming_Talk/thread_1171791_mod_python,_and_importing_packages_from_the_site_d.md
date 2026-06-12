---
title: "mod_python, and importing packages from the site directory"
date: 2009-05-27
forum: Programming Talk
---

### Post by necromantula on 2009-05-27
So i have Python 2.6, Apache2, and MySQL
My SQL server works fine, i can access it through both the python command line, and phpmyadmin.
Apache works fine, i even have it proxying SABnzbd+.
Python works as amazingly as always, and I can even import the package from the python prompt, while in the right directory. 

My files are as such
www/working/index.py
www/working/core/__init__.py
www/working/core/bokuwa.py
www/working/core/sql.py
www/working/core/boards.py

index.py contains the following code
```
from core import bokuwa

def index(req):
        b = bokuwa.bokuwa(req)
```

bokuwa.py defines the bokuwa class, who requests req.

I get this error
```
  File "/var/www/working/index.py", line 1, in <module>
    from core import bokuwa

ImportError: No module named core
```

I would prefer to avoid having to change sys.path to import this, and i want it to run as a package. is there any way to import the package from where it is?

---

### Post by unutbu on 2009-05-27
Edit ~/.profile. Add
```

PYTHONPATH=/var/www/working
export PYTHONPATH
```

Log out, and then log back in. 

See [http://docs.python.org/tutorial/modules.html](http://docs.python.org/tutorial/modules.html) (search for "PYTHONPATH") for more information.

---

### Post by necromantula on 2009-05-28
That would work, but I'm trying to avoid adding things to the path, i'm just confused as to why i can import modules from the folder using just import bokuwa, but not importing packages...

EDIT: Also, I have apache2 as a service, and my user is not usually logged in at all, and then only through SSH
Apache runs as www-data, so how changing my users pythonpath fix it?

---

### Post by unutbu on 2009-05-28
These are the only ways I know how to do it:

[list]
[*] Move /var/www/working into a directory searched by your python installation's sys.path
[*] Edit www-data's PYTHONPATH environment variable. If index.py is being called from a bash script, you can add the PYTHONPATH environment variable there, instead of in ~/.profile.
[*] Alter the sys.path variable from within the index.py script:
```
import sys
sys.path.append('/var/www/working')
```
[/list]

---

### Post by necromantula on 2009-05-29
So i'm currently using import sys, sys.path.append("/var/www/working") as a workaround, but now Im seeing some truly anomalous problems.
I can import my package fine, and use it as i please. However, sometimes it will produce error messages, with no reason.

I have working/index.py, which contains as such
```
import sys
sys.path.append("/var/www/working")

from core import website

def index(req):
        b = website.bokuwa(req)
        b.errors.append("Testing error messages")
        b.header()
```
and website.py contains a bunch of code, the part relevant being
```
import mod_python, time
import config, sql
class bokuwa:
        errors = []
        messages = []
        def __init__(self, req):
                req.content_type = "text/html"
                self.req = req
                self.config = config.config()
                self.sql = sql.SQL(self.config)
                self.errors = []
                self.messages = []
        def addError(self, error):
                self.errors.append(error)

        def addMessage(self, message):
                self.message.append(message)

        def header(self, title="c0re", scripts=[], styles=[]):
                scripts = ["prototype.js", "scriptaculous.js", "bokuwa.js"] + scripts
                styles = ["base.css", "menu.css"] + styles
                self.req.write("""<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">\n<html>\n<head>\n""")
                for i in styles:
                        self.req.write("""<link rel="stylesheet" type="text/css" href="css/%s" />\n""" % i)
                for i in scripts:
                        self.req.write("""<script type="text/javascript" src="js/%s"></script>\n""" % i)
                self.req.write("""<title>Bokuwa | %s</title>\n""" % title)
                self.req.write("""</head>\n<body>""")

                for i in self.errors:
                        self.tag("span", i, attributes="class=\"error\"")
                for i in self.messages:
                        self.tag("span", i, attributes="class=\"message\"")

```

sometimes, when calling functions in index.py, it gives an error stating that class bokuwa does not contain the function. it only happens about 10% of the times the script is loaded, and the rest of the time it outputs the expected
any ideas?

---

### Post by unutbu on 2009-05-29
Hm, that is really strange. I can't think of any reason why that might happen however.

Is index.py being called in exactly the same way, from the same directory, each time?

:confused:

---

