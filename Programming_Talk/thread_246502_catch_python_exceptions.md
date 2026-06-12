---
title: "catch python exceptions"
date: 2006-08-29
forum: Programming Talk
---

### Post by G|N| on 2006-08-29
If you execute the following code, you get an error like this: *urllib2.URLError: <urlopen error (-2, 'Name or service not known')>*
```

#!/usr/bin/env python
import urllib2
url = urllib2.urlopen("http://123.456.798")

```

i want to catch the error and print an error message but i have no idea how i can catch the error and receive the message.

i tried this:
```

#!/usr/bin/env python
import urllib2
try:
    url = urllib2.urlopen("http://123.456.798")
except:
    print "message"

```
but this way i don't know what error occured.

---

### Post by jurkki on 2006-08-29
how about

```

try:
    url = urllib2.urlopen("http://www.foobofos.it")
except IOError, (errno):
    print "%s" % (errno)

```

---

### Post by chonger on 2006-08-29
[URL="http://docs.python.org/tut/node10.html#SECTION0010300000000000000000"]From the python tutorial. 
[/URL]

> If an exception has an argument, it is printed as the last part (`detail') of the message for unhandled exceptions.

Exception handlers don't just handle exceptions if they occur immediately in the try clause, but also if they occur inside functions that are called (even indirectly) in the try clause. For example:

>>> def this_fails():
...     x = 1/0
... 
>>> try:
...     this_fails()
... except ZeroDivisionError, detail:
...     print 'Handling run-time error:', detail
... 
Handling run-time error: integer division or modulo by zero


---

### Post by Cryonic on 2006-08-29
When you run your program without the try-except construct, you'll see it throws an URLError.
In a python shell, type 

```

help(urllib2.URLError)

```

and you'll get more info on this particular exception. For instance, it doesn't have the standard two errno and strerror arguments, but just one.

So:

```

#!/usr/bin/env python
import urllib2
try:
    url = urllib2.urlopen("http://123.456.798")
except urllib2.URLError, (err):
    print "URL error(%s)" % (err)

```

---

### Post by dwblas on 2006-08-29
The following will also give you the line number of the offending code as well as the error message.  Keep it as a function somewhere that you can import.
```
   import traceback 
   et, ev, tb = sys.exc_info()                                                 
    while tb :                                                                  
        co = tb.tb_frame.f_code                                                 
        filename = "Filename = " + str(co.co_filename)                          
        line_no =  "Error Line # = " + str(traceback.tb_lineno(tb))             
        print filename                                                          
        print line_no                                                           
        tb = tb.tb_next                                                         
    print "et = ", et                                                                    
    print "ev = ",  ev
```

---

### Post by tleow on 2010-08-26
The following will print the exception, file name and line number:

import traceback
try: a = 1/0
except: traceback.print_exc()

---

### Post by nvteighen on 2010-08-26
> **tleow said:**
> The following will print the exception, file name and line number:

import traceback
try: a = 1/0
except: traceback.print_exc()

Uh... this thread is almost 4 years old.

Anyway, welcome to the forums!

---

