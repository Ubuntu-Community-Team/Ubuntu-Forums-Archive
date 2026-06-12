---
title: "Python - urllib2 question about .read() and .close()"
date: 2012-10-20
forum: Programming Talk
---

### Post by kpuz on 2012-10-20
Hi,

I have a question for python hackers.

I am writing my first program (a plugin for xbmc) that requires the use of urllib2.  I open the webpages of interest using 
```
urllib2.urlopen(url).read()
```
where url is the string that points to the webpage.

However, I am seeing that other plugins that use urllib2 use the .close() function at some point. I am wondering if there is some reason for this. 

Is this done to avoid memory leaks? I am seeing memory leaks in the xbmc.log and would like to know if closing (using .close()) can help with getting rid of these memory leaks.  

Thanks in advance

---

### Post by PatrickD-52761 on 2012-10-21
> **kpuz said:**
> Hi,

I have a question for python hackers.

I am writing my first program (a plugin for xbmc) that requires the use of urllib2.  I open the webpages of interest using 
```
urllib2.urlopen(url).read()
```
where url is the string that points to the webpage.

However, I am seeing that other plugins that use urllib2 use the .close() function at some point. I am wondering if there is some reason for this. 

Is this done to avoid memory leaks? I am seeing memory leaks in the xbmc.log and would like to know if closing (using .close()) can help with getting rid of these memory leaks.  

Thanks in advance

I'm not sure about the answer to your question, but I wanted to show you an alternative to the method that you're using. Someone else can comment on whether my method introduces the memory leaks or not, as I'm not an expert in this at all.  

```

    request = urllib2.Request(url)
    response = urllib2.urlopen(request)
    return response.read()

```

Have a great day:)
Patrick.

P.S. I should note that my script is a run once and stop type of script. So, if it's running continuously, there may be issues.

---

### Post by MadCow108 on 2012-10-21
the default python implementation follows reference counting semantics
this means the object will be deleted when nothing references it anymore so you don't have to expliticly close.

but not all implementations use this method, most others use a standard garbage collector
this means the descriptor will not be closed imediately

so for portability always close explicitly.

a good way to do that is context managers:

```
from contextlib import closing
import urllib

with closing(urllib.urlopen('http://www.python.org')) as page:
    for line in page:
        print line
```

here the descriptor will be closed after the with block, even if an exception is thrown.

I in python3.2 urllib.request is a contexmanager already so then you can just use it like files without the contextlib help:
```
with urllib.request.urlopen('http://www.python.org') as page:
```

---

