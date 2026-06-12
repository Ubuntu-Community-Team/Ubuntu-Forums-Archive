---
title: "python error i am getting need help fixing"
date: 2009-04-30
forum: Programming Talk
---

### Post by aszxcv on 2009-04-30
> # Split up a URL of the form [http://www.something.com](http://www.something.com)
url = raw_input('Please enter the URL: ')
domain = url[11:-4]
print "Domain name: " + domain


> 
line 2: syntax error near unexpected token `('
line 2: `url = raw_input('Please enter the URL: ')'



:confused:

---

### Post by Arndt on 2009-04-30
> **aszxcv said:**
> :confused:

You are not giving your code to python to execute, but to the shell.

Either put a line similar to this as the first line in your file:

```
#! /usr/bin/python
```

which indicates where the python executable is, and then run your program like this (assuming it's called prog.py):

```
./prog.py
```

or give it to python explicitly:

```
python prog.py
```

---

### Post by aszxcv on 2009-04-30
+1  i ended up figuring it out just came back to the thread to say thanks anyway.

---

### Post by ghostdog74 on 2009-04-30
you don't want to parse url like that.
use the urllib2 module's urlparse() method

---

### Post by aszxcv on 2009-04-30
> **ghostdog74 said:**
> you don't want to parse url like that.
use the urllib2 module's urlparse() method

that was a book example i am  reading

but i'll look into urllib2 once i get my feet under me

---

