---
title: "Import libraries (Python)"
date: 2011-01-07
forum: Programming Talk
---

### Post by ki4jgt on 2011-01-07
How would one import libraries such as ncurses or python wifi?

---

### Post by Miyavix3 on 2011-01-07
[http://effbot.org/zone/import-confusion.htm]("http://effbot.org/zone/import-confusion.htm")

Read the above. 
If you don't have the libraries installed, then you will have to download them from the repositories or manually install them from their official website.

---

### Post by ki4jgt on 2011-01-07
I've downloaded the python-wifi library. When I run
```
python setup.py install
```

I get this:

```
---------------------------------------------------------------------------
This script requires setuptools version 0.6b3 to run (even to display
help).  I will attempt to download it for you (from
http://chees*****.python.org/packages/2.6/s/setuptools/), but
you may need to enable firewall access for this script first.
I will start the download in 15 seconds.

(Note: if this machine does not have network access, please obtain the file

   http://chees*****.python.org/packages/2.6/s/setuptools/setuptools-0.6b3-py2.6.egg

and place it in this directory before rerunning this script.)
---------------------------------------------------------------------------
Downloading http://chees*****.python.org/packages/2.6/s/setuptools/setuptools-0.6b3-py2.6.egg
Traceback (most recent call last):
  File "setup.py", line 4, in <module>
    use_setuptools()
  File "/home/jesse/Desktop/python-wifi-0.5.0/ez_setup.py", line 70, in use_setuptools
    egg = download_setuptools(version, download_base, to_dir, download_delay)
  File "/home/jesse/Desktop/python-wifi-0.5.0/ez_setup.py", line 124, in download_setuptools
    src = urllib2.urlopen(url)
  File "/usr/lib/python2.6/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 397, in open
    response = meth(req, response)
  File "/usr/lib/python2.6/urllib2.py", line 510, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.6/urllib2.py", line 429, in error
    result = self._call_chain(*args)
  File "/usr/lib/python2.6/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 605, in http_error_302
    return self.parent.open(new, timeout=req.timeout)
  File "/usr/lib/python2.6/urllib2.py", line 397, in open
    response = meth(req, response)
  File "/usr/lib/python2.6/urllib2.py", line 510, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.6/urllib2.py", line 435, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.6/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 518, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 404: Not Found
jesse@Remember:~/Desktop/python-wifi-0.5.0$ python setup.py install

```

The .egg file is not available, so I don't know how to get it. :-(

***EDIT: the **** is cheese shop (one word)

---

### Post by MadCow108 on 2011-01-07
have you tried 6c version?
[http://pypi.python.org/pypi/setuptools](http://pypi.python.org/pypi/setuptools)

Its probably backwards compatible with 6b

---

### Post by ki4jgt on 2011-01-07
I somehow got it to work, don't ask how, but I don't know what all it does. I think they said that wifi-radar used it, and a few other programs on their sites (Forgive me LOL, this is my first python program. I'm coming from a background in BASIC)

***EDIT: oh and what would I need to use to run an http server over wifi? Is this module already included in Python?

---

### Post by wmcbrine on 2011-01-08
HTTP doesn't know the difference between WiFi and any other form of Internet. And yes, it's in the standard library:

import BaseHTTPServer

---

