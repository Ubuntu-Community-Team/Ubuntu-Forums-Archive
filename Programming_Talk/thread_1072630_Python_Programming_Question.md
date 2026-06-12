---
title: "Python Programming Question"
date: 2009-02-17
forum: Programming Talk
---

### Post by kylehotchkiss on 2009-02-17
Hey!

I am learning python slowly but surely and was wondering how you would execute another program (like handbrake) in the background of a computer (so that the python application does not wait for handbrake to finish, and then you can check on the status of handbrake running whenever. Is that possible?

---

### Post by nvteighen on 2009-02-17
That sounds to multithreading... it's a really hard topic, as far as I heard (I never did it either...).

---

### Post by PythonPower on 2009-02-17
I've never used multithreading in Python, but in C it's easy.

The relevent doc page for Python appears to be:

[http://docs.python.org/3.0/library/multiprocessing.html?highlight=multithreading](http://docs.python.org/3.0/library/multiprocessing.html?highlight=multithreading)

---

### Post by jimi_hendrix on 2009-02-17
> **nvteighen said:**
> That sounds to multithreading... it's a really hard topic, as far as I heard (I never did it either...).

depends on the language...

i advise reading [this]("http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/1/") and using the os.system() method to call the other program

---

### Post by imdano on 2009-02-17
I think you want the subprocess module, and the subprocess.Popen class specifically.  It lets you spawn a non-blocking child process and check its pid/return code (if it's finished running)/etc.

edit: See the documentation here: [http://docs.python.org/library/subprocess.html](http://docs.python.org/library/subprocess.html)

edit edit: In the simplest case, you would use it like this:
[php]
import subprocess
import time

pobj = subprocess.Popen("ls")
while pobj.poll() is None:
    print "ls is still running"
    time.sleep(3)
print "ls return code is %s" % pobj.poll()[/php]

---

### Post by kylehotchkiss on 2009-02-17
Thanks, yeah that is what I was looking for, I have been playing with that a little, and yours seems to tell me what to do. 


> **imdano said:**
> I think you want the subprocess module, and the subprocess.Popen class specifically.  It lets you spawn a non-blocking child process and check its pid/return code (if it's finished running)/etc.

edit: See the documentation here: [http://docs.python.org/library/subprocess.html](http://docs.python.org/library/subprocess.html)

edit edit: In the simplest case, you would use it like this:
[php]
import subprocess
import time

pobj = subprocess.Popen("ls")
while pobj.poll() is None:
    print "ls is still running"
    time.sleep(3)
print "ls return code is %s" % pobj.poll()[/php]

---

