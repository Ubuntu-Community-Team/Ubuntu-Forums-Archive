---
title: "Compiling Sage 4.8?"
date: 2012-03-22
forum: Packaging and Compiling Programs
---

### Post by newhere_m on 2012-03-22
I was trying to install sage-4.8 from source in ubuntu 10.04. I had downloaded the sage-4.8.tar archive, created the sage-4.8 directory and then used the command "make". After nearly two hours, I got the report (only relevant part is shown below):
```
Traceback (most recent call last):
  File "setup.py", line 830, in <module>
    execute_list_of_commands(queue)
  File "setup.py", line 287, in execute_list_of_commands
    execute_list_of_commands_in_parallel(command_list, nthreads)
  File "setup.py", line 238, in execute_list_of_commands_in_parallel
    p = Pool(nthreads)
  File "/home/myname/sage-4.8/local/lib/python/multiprocessing/__init__.py", line 227, in Pool
    return Pool(processes, initializer, initargs)
  File "/home/myname/sage-4.8/local/lib/python/multiprocessing/pool.py", line 84, in __init__
    self._setup_queues()
  File "/home/myname/sage-4.8/local/lib/python/multiprocessing/pool.py", line 131, in _setup_queues
    self._inqueue = SimpleQueue()
  File "/home/myname/sage-4.8/local/lib/python/multiprocessing/queues.py", line 328, in __init__
    self._rlock = Lock()
  File "/home/myname/sage-4.8/local/lib/python/multiprocessing/synchronize.py", line 117, in __init__
    SemLock.__init__(self, SEMAPHORE, 1, 1)
  File "/home/myname/sage-4.8/local/lib/python/multiprocessing/synchronize.py", line 49, in __init__
    sl = self._semlock = _multiprocessing.SemLock(kind, value, maxvalue)

"OSError: [Errno 30] Read-only file system
sage: There was an error installing modified sage library code.
ERROR installing Sage
make[1]: *** [installed/sage-4.8] Error 1
make[1]: Leaving directory `/home/myname/sage-4.8/spkg'

real    126m42.538s
user    121m51.361s
sys    12m44.712s
Error building Sage.
make: *** [build] Error 1"
```

My guess is that I should have used "sudo make" command instead of just "make". The result of uname -a is: ```
Linux myname-desktop 2.6.32-39-generic #86-Ubuntu SMP Mon Feb 13 21:47:32 UTC 2012 i686 GNU/Linux

```
Please suggest what I should do now. Will it be proper to use the "sudo make" command at this stage or should I do something about the already created sage-files and directories (in the failed installation process)?

---

### Post by newhere_m on 2012-03-23
I want to know in general what one should do if one needs to install a program after a failed attempt to install it? My specific query is related to installation of a python-based mathematical package called sage-4.8 ([http://ubuntuforums.org/showthread.php?t=1945151](http://ubuntuforums.org/showthread.php?t=1945151)) for which I have submitted one question in the Education & Science section of this forum. Since very few people visit that and are able to provide suggestion for such specific question, I would like to get some general idea from experts here. Please note that I tried to install from source (not binary) and during two hours of process, some new directories had been created. What do I do about those? I am not supposed to run "sudo make" again in presence of those directories and perhaps established links etc? Generally how does one proceed to solve such problems?

The error message stated: 
```
Traceback (most recent call last):   File "setup.py", line 830, in  <module>     execute_list_of_commands(queue) 

File "setup.py",  line 287, in execute_list_of_commands      execute_list_of_commands_in_parallel(command_list, nthreads)   

File  "setup.py", line 238, in execute_list_of_commands_in_parallel     p =  Pool(nthreads)   

File  "/home/myname/sage-4.8/local/lib/python/multiprocessing/__init__.py",  line 227, in Pool     return Pool(processes, initializer, initargs)    

File "/home/myname/sage-4.8/local/lib/python/multiprocessing/pool.py",  line 84, in __init__     self._setup_queues() 

File  "/home/myname/sage-4.8/local/lib/python/multiprocessing/pool.py", line  131, in _setup_queues     self._inqueue = SimpleQueue()   

File  "/home/myname/sage-4.8/local/lib/python/multiprocessing/queues.py", line  328, in __init__     self._rlock = Lock() 

File  "/home/myname/sage-4.8/local/lib/python/multiprocessing/synchronize.py",  line 117, in __init__     SemLock.__init__(self, SEMAPHORE, 1, 1)    

File  "/home/myname/sage-4.8/local/lib/python/multiprocessing/synchronize.py",  line 49, in __init__     sl = self._semlock =  _multiprocessing.SemLock(kind, value, maxvalue)  

"OSError: [Errno 30]  Read-only file system sage: There was an error installing modified sage  library code. 

ERROR installing Sage make[1]: *** [installed/sage-4.8] 

Error 1 make[1]: Leaving directory `/home/myname/sage-4.8/spkg'  

real     126m42.538s 

user    121m51.361s 

sys    12m44.712s 

Error building Sage.  make: *** [build] Error 1"
```

---

### Post by oldos2er on 2012-03-23
I've combined your threads (please don't start more than one thread per question) and moved them to Packaging and Compiling Programs.

---

