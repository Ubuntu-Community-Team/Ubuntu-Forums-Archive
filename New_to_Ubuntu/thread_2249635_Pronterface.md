---
title: "Pronterface"
date: 2014-10-23
forum: New to Ubuntu
---

### Post by bluecake on 2014-10-23
I have no experience with Ubuntu or Linux in general but managed to install the software needed for printrun.
I'm using xubuntu 12.04

In the terminal when I want to start the application with [INDENT]Quote
**pronterface.py**

[/INDENT] 
I get the following error:

[INDENT]Quote
[B]jim@Ilias:~/Printrun$ ./pronterface.py 
WARNING:root:Memory-efficient GCoder implementation unavailable: No module named gcoder_line
 [WARNING] Could not setup DBus for sleep inhibition:  org.freedesktop.DBus.Error.ServiceUnknown: The name  org.freedesktop.ScreenSaver was not provided by any .service files 
Traceback (most recent call last):  
File "./pronterface.py", line 32, in      from printrun.pronterface import PronterApp   
File "/home/jim/Printrun/printrun/pronterface.py", line 32, in      from . import pronsole  
File "/home/jim/Printrun/printrun/pronsole.py", line 42, in      from .power import powerset_print_start, powerset_print_stop   
File "/home/jim/Printrun/printrun/power/__init__.py", line 90, in      orig_nice = p.get_nice() 
AttributeError: 'Process' object has no attribute 'get_nice'[/B]

[/INDENT] 
Can somebody explain what this error means?

---

