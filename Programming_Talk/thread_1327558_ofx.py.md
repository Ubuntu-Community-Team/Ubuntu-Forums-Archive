---
title: "ofx.py"
date: 2009-11-15
forum: Programming Talk
---

### Post by bradhaack on 2009-11-15
I'm using ofx.py (available from [http://www.jongsma.org/gc/](http://www.jongsma.org/gc/)) a python script which downloads ofx formatted data from banks.  I don't know python, but it's been working for me until today.  I'm using ubunto 9.10, with the latest updates.  I think the last update might have broken the script.  Did some library update break it?  Any ideas?  Here's the error msg:

Traceback (most recent call last):
  File "./ofx.py", line 214, in <module>
    client.doQuery(query, argv[1]+argv[3]+dtnow+".ofx")
  File "./ofx.py", line 179, in doQuery
    f = urllib2.urlopen(request)
  File "/usr/lib/python2.6/urllib2.py", line 124, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 389, in open
    response = self._open(req, data)
  File "/usr/lib/python2.6/urllib2.py", line 407, in _open
    '_open', req)
  File "/usr/lib/python2.6/urllib2.py", line 367, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 1154, in https_open
    return self.do_open(httplib.HTTPSConnection, req)
  File "/usr/lib/python2.6/urllib2.py", line 1119, in do_open
    r = h.getresponse()
  File "/usr/lib/python2.6/httplib.py", line 974, in getresponse
    response.begin()
  File "/usr/lib/python2.6/httplib.py", line 391, in begin
    version, status, reason = self._read_status()
  File "/usr/lib/python2.6/httplib.py", line 355, in _read_status
    raise BadStatusLine(line)
httplib.BadStatusLine

---

### Post by Can+~ on 2009-11-15
You should first seek for the error name in the doc:

[http://docs.python.org/library/httplib.html#httplib.BadStatusLine](http://docs.python.org/library/httplib.html#httplib.BadStatusLine)

I don't think an update could break python, updates that break compatibility are from 2.x to 3.x. Maybe the server you're connecting to is having trouble?

---

### Post by bradhaack on 2009-11-15
That could be.  I can get my ofx file thru the web browser so i lept to the conclusion that it wasn't the server.   On the python web site it just says that that error means it's returning an unknown error code.  So i don't know with that information.

Anyone else suddenly broken w/ chase?  


> **Can+~ said:**
> You should first seek for the error name in the doc:

[http://docs.python.org/library/httplib.html#httplib.BadStatusLine](http://docs.python.org/library/httplib.html#httplib.BadStatusLine)

I don't think an update could break python, updates that break compatibility are from 2.x to 3.x. Maybe the server you're connecting to is having trouble?

---

### Post by JohnColorado on 2009-11-23
Chase has apparently changed the URL of its ofx server, as  of November 15 or so.

See [http://forums.iggsoft.com/viewtopic.php?f=19&t=11019&start=105](http://forums.iggsoft.com/viewtopic.php?f=19&t=11019&start=105)

One possible option is to sign up for ibank, turn on debugging, and see what that URL is...

---

### Post by JohnColorado on 2009-12-16
[https://ofx.chase.com](https://ofx.chase.com) is the new url.

---

