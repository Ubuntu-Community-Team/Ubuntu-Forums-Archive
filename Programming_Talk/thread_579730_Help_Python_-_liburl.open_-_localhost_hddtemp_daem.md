---
title: "Help: Python - liburl.open - localhost hddtemp daemon"
date: 2007-10-18
forum: Programming Talk
---

### Post by arsenic23 on 2007-10-18
Ok, I have hddtemp running as a daemon on its default port of 7634.  I can see it by opening localhost:7634 in my browsers, but I can't seem to get to it using python.

After looking around the net I discovered urllib and read a bit about it.  So I tried something like :
```
v=urllib.urlopen("http://localhost:7634").read()
```
But I get *(104, 'Connection reset by peer')* every time.

I looked around some more, sampling other people's work, and I've seen numorous other examples where people use urllib in the exact same way.  Can someone please tell me why this isn't working, or just point me in the correct direction?

---

### Post by pmasiar on 2007-10-18
you can do it 3 steps in shell
[php]
import urllib
f = urllib.openurl("http://localhost:7634")
v = f.read()
[/php]
Does it fail when creating f or v? Did you tried newer urllib2?

---

### Post by arsenic23 on 2007-10-18
Yeah, I tried urllib2 as well - I just can't figure out what's causing this:

```
>>> f=urllib2.urlopen("http://localhost:7634")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/urllib2.py", line 121, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 374, in open
    response = self._open(req, data)
  File "/usr/lib/python2.5/urllib2.py", line 392, in _open
    '_open', req)
  File "/usr/lib/python2.5/urllib2.py", line 353, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.5/urllib2.py", line 1100, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.5/urllib2.py", line 1075, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error (104, 'Connection reset by peer')>
```

It just strikes me as odd that I can open [http://localhost:7634](http://localhost:7634) in pretty much everything else.

---

### Post by arsenic23 on 2007-11-07
Alright, so I sat down and started playing with this again this morning and I have figured out the cause.

If I try to download *[http://localhost:7634/index.html](http://localhost:7634/index.html)* using wget, then I can see that it's downloading the txt/html, which has no header apparently, and then reporting *'Read error at byte 66 (Connection reset by peer)'*.

So it seems the only thing I have to do to make this work is ignore the error with a try statement.
```
try:	val=urllib2.urlopen("http://localhost:7634/index.html").read()
except: None

print val
```
Works most of the time.  Unfortuneately, sometimes "print val' errors: *"NameError: name 'val' is not defined"*.  There is no pattern to it that I can see, it just doesn't work about 5% of the time.  Obviously I can just set val to some value before this and monitor for it later to ignore the times this happens.  But I'm more interested in why it happens.

Anyone have any thoughts?

---

### Post by cmsimike on 2010-03-18
I know this is a bit late, but this is how I did it (needed to do the same thing) in Python:

```
#!/usr/bin/python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("localhost",7634))
buf = s.recv(4096)
s.close()
print buf

```

I am a bit new to Python so this may not be the most elegant way of doing it.

---

