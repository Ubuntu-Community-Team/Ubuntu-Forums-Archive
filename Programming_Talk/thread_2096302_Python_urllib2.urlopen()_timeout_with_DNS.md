---
title: "Python urllib2.urlopen() timeout with DNS"
date: 2012-12-19
forum: Programming Talk
---

### Post by jegger on 2012-12-19
I am working with python2.7 under Ubuntu 12.04.
If I plug the ethernet cable out  of my pc, so that I don't have any connection to the internet for sure, I run into a strange issue.

I have the problem that setting the timeout is useless when the url isn't already resolved to an IP address. 

If I try the following:
```
urllib2.urlopen('http://www.google.com', timeout=3).read()
```
I get after +/- 40sec the following exception:
```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 400, in open
    response = self._open(req, data)
  File "/usr/lib/python2.7/urllib2.py", line 418, in _open
    '_open', req)
  File "/usr/lib/python2.7/urllib2.py", line 378, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 1207, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.7/urllib2.py", line 1177, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error [Errno -3] Temporary failure in name resolution>
```

I think it should fail after 3sec with a different exception. 
All works like it should when I use the google IP directly:
```
urllib2.urlopen('http://173.194.35.40', timeout=3).read()
```
Than I get the "correct" exception after 3sec:
```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 400, in open
    response = self._open(req, data)
  File "/usr/lib/python2.7/urllib2.py", line 418, in _open
    '_open', req)
  File "/usr/lib/python2.7/urllib2.py", line 378, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 1207, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.7/urllib2.py", line 1177, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error timed out>
```

I testet this on a mac (also python2.7) - there it is working perfect.
I used urllib2 often on earlier versions of ubunut and never had this problem. I expect that some change (up to 12.04) might be the issue. 
I heard that the DNS resolving in 12.04 changed: [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/")

Does anyone know how to fix this issue?

---

### Post by mirrorz on 2013-02-10
I was having the same problem. But i found out that it was due to python using system set proxy. So in order to disable you can make the following changes:

import os
os.environ['http_proxy']=''

This worked for me.
Good Luck!

---

