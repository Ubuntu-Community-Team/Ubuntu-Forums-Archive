---
title: "[SOLVED] Python: os.popen() issues"
date: 2008-06-09
forum: Programming Talk
---

### Post by molotov00 on 2008-06-09
Hey Guys,

I have a script that finds then downloads a PDF to /tmp/filename. Here's the relevant part:

```
print "Displaying report"
os.popen("evince file://"+dir+filename)
sys.exit(0)
```

It displays fine, in xfce's default PDF viewer (evince).

Problem:
Closing the terminal window closes my PDF. I'd like the script to exit and leave my PDF open.

Forking comes to mind, just not sure how to do it in Python.

Any help would be appreciated.

---

### Post by altonbr on 2008-06-09
> **molotov00 said:**
> Hey Guys,

I have a script that finds then downloads a PDF to /tmp/filename. Here's the relevant part:

```
print "Displaying report"
os.popen("evince file://"+dir+filename)
sys.exit(0)
```

It displays fine, in xfce's default PDF viewer (evince).

Problem:
Closing the terminal window closes my PDF. I'd like the script to exit and leave my PDF open.

Forking comes to mind, just not sure how to do it in Python.

Any help would be appreciated.

Anytime you run a program through the terminal, the program becomes dependant on the terminal.

Example: open your terminal, type Firefox and then close the terminal. You will see Firefox close. I think you should have your script call evince outside of bash, or using another executable that loads evince for you, so you no longer have the dependancy.

But I don't program in Python, so what do I know?

---

### Post by molotov00 on 2008-06-09
Brilliantly simple.

I think you might be right. Although, I have a hard time believing there's no way to avoid the issue in Python. But you've at least given me another idea to work with. Thanks.

---

### Post by Steveway on 2008-06-09
How about adding a & at the end of the command in your terminal?
For example opening gedit with gedit & will open it but not close it if you close the terminal.

---

### Post by rye_ on 2008-06-09
> **Steveway said:**
> How about adding a & at the end of the command in your terminal?
For example opening gedit with gedit & will open it but not close it if you close the terminal.

nice tip.
This is not something I was aware of.

---

### Post by molotov00 on 2008-06-09
Update:

& trick works in terminal but I can't get it to work with Python using popen()

This code works:
```
os.spawnlp(os.P_NOWAIT, 'evince', 'evince', dir+filename)
```

HOWEVER... it only works when I call my script (python /home/jordan/python/mstar.py) from the terminal. When I call the script using a Panel button in XFCE then evince doesn't load.

This is an entirely different problem that seems to be Xubuntu related rather than Python related so maybe someone has ideas?

---

### Post by unutbu on 2008-06-09
Maybe the panel executes the script with an environment that does not include DISPLAY.

Try this command instead
```
/usr/bin/env /home/jordan/python/mstar.py
```
or maybe

```
DISPLAY=:0.0 /home/jordan/python/mstar.py
```

---

### Post by imdano on 2008-06-09
Give this code a shot, it uses the subprocess module, which is intended to replace os.system, os.popen, os.spawn*, etc.:
[php]#!/usr/bin/python
from subprocess import Popen

path_to_pdf = "your_path_here"  # Change this line! 

Popen(["evince", path_to_pdf])[/php]Though unutbu may be right, it's possible that launching from the panel isn't giving the proper environment.  You might want to try passing the full path to evince, instead of just the executable name.

---

### Post by molotov00 on 2008-06-09
The original problem was SOLVED with the above code (spawnlp) I posted.

imdano's method also works, and is in fact the one I went with in the end.

The Panel issue wasn't fixed but I'm happy with what I have now, which is a command line app that's easy to open from the terminal. (mstar <symbol>) downloads a PDF stock report from Morningstar.com and then opens it. I access these reports quite a bit, both on and off the job, and it's a nuisance to login and click through a bunch of pages. Now Python takes care of it, transparently ;)

Unutbu, thanks for your contribution. I wasn't aware that environments might play a role. Know it now though.

---

### Post by StephenF on 2008-06-21
Here is some code I knocked together. The 10 second delay was added to give you time to delete the console window before evince pops up. :)

```

#!/usr/bin/python

import os, sys, time

class Redirect:         # your handling of print statements goes here
   def __init__(self):
      self.write = self._write
   def close(self):
      self.write = self._closed
   def _write(self, text):
      try:
         # indicate that a print statement was intercepted
         os.mknod("/tmp/console_write_intercepted")
      except:
         pass
      # real programs would normally just use 'pass' here
   def _closed(self):
      pass      # silently ignore additional write attempts

try:
   os.mknod("/tmp/i_am_running")        # just so you know ;)
except:
   print "another instance is already running or its lock file exists"
   sys.exit(5)

pid = os.fork()
if pid:
   sys.exit(0)
else:
   os.setsid()
   pid2 = os.fork()
   if pid2 < 0:
      print "second fork failed"
   else:
      if pid2 > 0:
         sys.exit(0)
      else:
         sys.stdin.close()
         sys.stdout.close()
         sys.stderr.close()
         sys.stdout = Redirect() # prevent lock-up on print statements
         sys.stderr = Redirect()
         os.umask(0)
         os.close(0)             # really close that terminal access
         os.close(1)
         os.close(2)
         os.chdir("/")           # prevent directory locking

         # rest of your program goes here
         print "This will 'Redirect'"
         time.sleep(10)         # give time to close terminal window
         os.popen("evince")     # can't be bothered with an actual PDF
         os.unlink("/tmp/i_am_running")
         sys.exit(0)

```

---

