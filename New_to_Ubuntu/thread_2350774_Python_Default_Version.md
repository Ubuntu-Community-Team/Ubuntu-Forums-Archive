---
title: "Python Default Version"
date: 2017-01-27
forum: New to Ubuntu
---

### Post by eddiefiggie on 2017-01-27
Very new to this, and just poking around to gather a better understanding of things...  I noted here that Python 3 is now the default and Python 2 was no longer installed as part of the native 16.04 build:

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Python_3](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Python_3)

That said, when I type Python on the command line...  it's barking out that I have version 2.7.12.

Can someone enlighten me?


EDIT::

I see, my original link was for Server...  This link answers my question:  [https://wiki.ubuntu.com/Python/3](https://wiki.ubuntu.com/Python/3)

---

### Post by ajgreeny on 2017-01-27
16.04 has both versions of python installed

---

### Post by ian-weisser on 2017-01-27
The 'python' command should refer to Py2, per [PEP 394]("https://www.python.org/dev/peps/pep-0394/"), until the upstream policy changes.

---

