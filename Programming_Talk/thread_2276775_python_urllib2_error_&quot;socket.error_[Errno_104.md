---
title: "python urllib2 error &quot;socket.error: [Errno 104] Connection reset by peer&quot;"
date: 2015-05-04
forum: Programming Talk
---

### Post by chjustc on 2015-05-04
Hi there,

I have the error below when trying to download the html content of a webpage. I can open this webpage in a browser without any problem. I am using Ubuntu 14.04. Thanks.

Python 2.7.6 (default, Mar 22 2014, 22:59:56)
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import urllib2
request = urllib2.Request('http://guggenheiminvestments.com/products/etf/gsy/holdings')
response = urllib2.urlopen(request)
>>> >>> Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.7/urllib2.py", line 127, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 404, in open
    response = self._open(req, data)
  File "/usr/lib/python2.7/urllib2.py", line 422, in _open
    '_open', req)
  File "/usr/lib/python2.7/urllib2.py", line 382, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 1214, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.7/urllib2.py", line 1187, in do_open
    r = h.getresponse(buffering=True)
  File "/usr/lib/python2.7/httplib.py", line 1045, in getresponse
    response.begin()
  File "/usr/lib/python2.7/httplib.py", line 409, in begin
    version, status, reason = self._read_status()
  File "/usr/lib/python2.7/httplib.py", line 365, in _read_status
    line = self.fp.readline(_MAXLINE + 1)
  File "/usr/lib/python2.7/socket.py", line 476, in readline
    data = self._sock.recv(self._rbufsize)
socket.error: [Errno 104] Connection reset by peer
>>>

---

### Post by ofnuts on 2015-05-05
Works for me (same OS, same Python), so not a python issue?

---

