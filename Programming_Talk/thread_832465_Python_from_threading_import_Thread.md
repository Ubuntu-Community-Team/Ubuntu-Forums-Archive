---
title: "Python: from threading import Thread"
date: 2008-06-17
forum: Programming Talk
---

### Post by iXombie on 2008-06-17
I have been trying to learn threading in python but have ran into an issue when running the following code
```
#!/usr/bin/env python
import os
import re
import time
import sys
from threading import Thread

class testit(Thread):
   def __init__ (self,ip):
      Thread.__init__(self)
      self.ip = ip
      self.status = -1
   def run(self):
      pingaling = os.popen("ping -q -c2 "+self.ip,"r")
      while 1:
        line = pingaling.readline()
        if not line: break
        igot = re.findall(testit.lifeline,line)
        if igot:
           self.status = int(igot[0])

testit.lifeline = re.compile(r"(\d) received")
report = ("No response","Partial Response","Alive")

print time.ctime()
timer = time.time()
pinglist = []

for host in range(60,70):
   ip = "192.168.200."+str(host)
   current = testit(ip)
   pinglist.append(current)
   current.start()

for pingle in pinglist:
   pingle.join()
   print "Status from ",pingle.ip,"is",report[pingle.status]

print time.time() - timer
```

When I run this I get the following error.

```
Traceback (most recent call last):
  File "./threading.py", line 6, in <module>
    from threading import Thread
  File "/home/jeremy/Desktop/threading.py", line 6, in <module>
    from threading import Thread
ImportError: cannot import name Thread

```

The code runs fine in a windows environment. Any ideas are welcome. So far I have reinstalled Python. I have also tried importing the module in IDLE with out any errors.

---

### Post by LaRoza on 2008-06-17
What OS are you using and what version? What version of Python are you using?
```

~$python --version

```

(Btw, I like Russell Peters also :-))

---

### Post by iXombie on 2008-06-17
I am using Ubuntu 8.04 and Python 2.5.2.

Thanks for that version command, I'm rather new and was looking for that command yesterday.

Russell Peters is hilarious. I just recently missed a chance to see him live. Still kicking myself over that one.

---

### Post by LaRoza on 2008-06-17
> **iXombie said:**
> I am using Ubuntu 8.04 and Python 2.5.2.

Thanks for that version command, I'm rather new and was looking for that command yesterday.

Russell Peters is hilarious. I just recently missed a chance to see him live. Still kicking myself over that one.

I can't find a problem with the code.

Try using just a plain "import threading" and specifying the namespace in the code?

I would love to see him live also :-)

---

### Post by iXombie on 2008-06-17
changed:

```
#!/usr/bin/env python
import os
import re
import time
import sys
from threading import Thread

class testit(Thread):
```
to
```
#!/usr/bin/env python
import os
import re
import time
import sys
import threading

class testit(threading.Thread):
```
Got:
```
Traceback (most recent call last):
  File "./threading.py", line 6, in <module>
    import threading
  File "/home/jeremy/Desktop/threading.py", line 8, in <module>
    class testit(threading.Thread):
AttributeError: 'module' object has no attribute 'Thread'

```

This error just seems SO weird. I have been playing with python for 3+ months and haven't had any issues that a couple short searches couldn't fix.

---

### Post by iXombie on 2008-06-17
I'm not sure if I write a script as follows:

```
#!/usr/bin/env python
print "start"
import threading

print dir(threading.Thread)
```

I get the same error I did before, but if I do this in IDLE I get results.

```
['_Thread__bootstrap', '_Thread__bootstrap_inner', '_Thread__delete', '_Thread__exc_info', '_Thread__initialized', '_Thread__stop', '__class__', '__delattr__', '__dict__', '__doc__', '__getattribute__', '__hash__', '__init__', '__module__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__str__', '__weakref__', '_note', '_set_daemon', 'getName', 'isAlive', 'isDaemon', 'join', 'run', 'setDaemon', 'setName', 'start']
```

---

### Post by LaRoza on 2008-06-17
```

~$python
Python 2.5.2 (r252:60911, Apr 21 2008, 11:12:42) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import threading
>>> threading.Thread
<class 'threading.Thread'>
>>> 

```

I am sorry, I don't know what to say. Did you alter the installation of Python in anyway?

---

### Post by iXombie on 2008-06-17
I get the same read in IDLE as you. I didn't make any changes to the installation at all. *sigh*

---

### Post by LaRoza on 2008-06-17
I ran the code:

```

~$./p.py
Tue Jun 17 20:28:34 2008

Status from  192.168.200.60 is No response
Status from  192.168.200.61 is No response
Status from  192.168.200.62 is No response
Status from  192.168.200.63 is No response
Status from  192.168.200.64 is No response
Status from  192.168.200.65 is No response
Status from  192.168.200.66 is No response
Status from  192.168.200.67 is No response
Status from  192.168.200.68 is No response
Status from  192.168.200.69 is No response
11.0330607891
~$

```

I don't understand why your code isn't working. Hopefully someone more informed in this area will post.

---

### Post by iXombie on 2008-06-17
SO, When I use the GUI for IDLE everything is fine but when i use the terminal I get the following
```
Python 2.5.2 (r252:60911, Jun 16 2008, 22:21:51) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import threading
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/jeremy/Desktop/threading.py", line 8, in <module>
    class testit(threading.Thread):
AttributeError: 'module' object has no attribute 'Thread'
>>> 
```

Guess i should had done that from the beginning. That changes things a bit.

---

### Post by Can+~ on 2008-06-17
Are you calling your file "threading.py"?

please rename it to something so python doesn't reimport your own module.

---

### Post by iXombie on 2008-06-17
yes. :o 
I think i see what you're saying here.

---

### Post by Can+~ on 2008-06-17
> **iXombie said:**
> yes. :o 
I think i see what you're saying here.

I got a clue from your error:

```
File "/home/jeremy/Desktop/threading.py", line 8, in <module>
```

It's a common error.

---

### Post by iXombie on 2008-06-17
Thank you very much for that insight. It didn't fix the error but it did give me a new error message... kinda.

```
Traceback (most recent call last):
  File "./a.py", line 6, in <module>
    from threading import Thread
  File "/usr/local/lib/python2.5/threading.py", line 8, in <module>
    del _sys.modules[__name__]
AttributeError: 'module' object has no attribute 'Thread'

```
i renamed it to a.py.

---

### Post by Can+~ on 2008-06-17
Could you run it using

python filename.py

So it can recompile the .pyc files? Although this time it looks like it pointed to the right direction.

---

### Post by iXombie on 2008-06-17
Alright so I have apparently fixed the issue. Thank you all for you your assistance. The fix is as follows.

When I had originally ran the program the file was named "threading.py". It would seem that when I ran it the first time it compiled the pyc and left it behind. Since naming a file after a module you are using is a No No, I renamed the file to "a.py". For some reason when I was to run the renamed py file it would reference the module then not be able to find Threads. This all fixed when i deleted the pyc that was left on my desktop from the poorly named py file that I had earlier.

I wish I knew more about what was really going on here but I have a LOT more to learn about this programming language. Thanks again to everyone that helped.

---

### Post by Can+~ on 2008-06-17
> **iXombie said:**
> Alright so I have apparently fixed the issue. Thank you all for you your assistance. The fix is as follows.

When I had originally ran the program the file was named "threading.py". It would seem that when I ran it the first time it compiled the pyc and left it behind. Since naming a file after a module you are using is a No No, I renamed the file to "a.py". For some reason when I was to run the renamed py file it would reference the module then not be able to find Threads. This all fixed when i deleted the pyc that was left on my desktop from the poorly named py file that I had earlier.

I wish I knew more about what was really going on here but I have a LOT more to learn about this programming language. Thanks again to everyone that helped.

When you run a program with:

```
python filename.py
```

It compiles the first it and stores it next to the original .py. When you use the python command again, it will check which is newer, if the .py has no changes, it will run the .pyc, otherwise it will recompile it.

I suggest you to stick to that command, instead of running with "./" to avoid this sort of problems. Or use geany so that you don't have to type anything.

Happy coding.

---

### Post by pmasiar on 2008-06-17
when your program a.py called threading.py, it found your leftover threading.pyc and used it, even if wrongly. You need to delete your own threading.pyc, removing your own threading.py is not enough.

Never, ever name your modules as core Python modules - look them up, and be aware what is in your namespace. Only experts who want to tweak core modules do that (put your own module into pythonpath before code modules).

---

### Post by gje on 2009-01-02
iXombie,

I'm flattered ... the code you've posted here comes straight off my own website ... now why didn't you ask me when it wouldn't work for you :D

You'll find a full page describing the application [[here]]("http://www.wellho.net/solutions/python-python-threads-a-first-example.html") and you'll note that I've called the two examples of that page **alive** and **kicking** so that they don't get confused with standard modules.

---

### Post by Denz Choe on 2011-03-25
> **iXombie said:**
> Alright so I have apparently fixed the issue. Thank you all for you your assistance. The fix is as follows.

When I had originally ran the program the file was named "threading.py". It would seem that when I ran it the first time it compiled the pyc and left it behind. Since naming a file after a module you are using is a No No, I renamed the file to "a.py". For some reason when I was to run the renamed py file it would reference the module then not be able to find Threads. This all fixed when i deleted the pyc that was left on my desktop from the poorly named py file that I had earlier.

I wish I knew more about what was really going on here but I have a LOT more to learn about this programming language. Thanks again to everyone that helped.



you have no idea, after 2 years from your post.. users like me would still bump into the same issue like u had (while learning about threading.. coincidentally too.lol); on a Windows machine. Thankfully your post came up 1st in google search. Saves me great deal of time.

Thanks guys

p/s: fyi, I did name my .py file to *threading.py* too and couldn't figure out the problem why didn't it work on cmd line, when it was working on IDLE.

---

