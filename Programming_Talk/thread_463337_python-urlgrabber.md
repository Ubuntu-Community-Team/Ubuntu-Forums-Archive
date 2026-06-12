---
title: "python-urlgrabber"
date: 2007-06-03
forum: Programming Talk
---

### Post by bjourne on 2007-06-03
I tried to install the python-urlgrabber package, but it seems to install itself in the wrong directories:

```

$ dpkg -S python-urlgrabber
python-urlgrabber: /usr/share/python-support/python-urlgrabber
python-urlgrabber: /usr/share/python-support/python-urlgrabber/urlgrabber
python-urlgrabber: /usr/lib/python-support/python-urlgrabber/python2.5
python-urlgrabber: /usr/share/python-support/python-urlgrabber/urlgrabber/grabber.py
python-urlgrabber: /usr/share/doc/python-urlgrabber/changelog.gz
python-urlgrabber: /usr/share/python-support/python-urlgrabber/urlgrabber/keepalive.py
python-urlgrabber: /usr/share/python-support/python-urlgrabber/urlgrabber/__init__.py
python-urlgrabber: /usr/share/python-support/python-urlgrabber/urlgrabber/progress.py
python-urlgrabber: /usr/share/doc/python-urlgrabber/TODO
python-urlgrabber: /usr/lib/python-support/python-urlgrabber/python2.5/urlgrabber-2.9.9-py2.5.egg-info
python-urlgrabber: /usr/share/doc/python-urlgrabber/changelog.Debian.gz
python-urlgrabber: /usr/share/doc/python-urlgrabber
python-urlgrabber: /usr/share/python-support/python-urlgrabber/urlgrabber/byterange.py
python-urlgrabber: /usr/share/doc/python-urlgrabber/copyright
python-urlgrabber: /usr/share/python-support/python-urlgrabber/urlgrabber/mirror.py
python-urlgrabber: /usr/lib/python-support/python-urlgrabber
$ python -c "import urlgrabber"
Traceback (most recent call last):
  File "<string>", line 1, in ?
ImportError: No module named urlgrabber

```

What does the /usr/share/python-support directories do? Python packages used to install themselves in /usr/lib/python2.4/site-packages.

---

