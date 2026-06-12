---
title: "SSL support for Python 2.4 on Plone 2.5.5"
date: 2012-02-06
forum: Programming Talk
---

### Post by karmic-koala on 2012-02-06
Hello,

I am working to get a legacy Plone system talk to an external repository over SSL. The external repository was non secure before but can only be accessed using https now.

The legacy system is an old Plone install (v2.5.5). The operating system python (2.6.5) can easily connect over ssl but the Plone version of python can not. The following fails on Plone

import socket
socket.ssl

How do I add SSL support to Plone? Some one pointed me out to buildout.python but I can't really see how that's useful in Plone context. 

Any ideas appreciated.

---

### Post by mikemets on 2012-09-16
I have a similar issue with SSL on python 2.4. Did you make any prorgess since you last post?

---

### Post by karmic-koala on 2012-09-21
Yes, I was able to get round the problem by doing the following

(1) on my application's version of python I installed python setup tools (link here [http://pypi.python.org/pypi/setuptools](http://pypi.python.org/pypi/setuptools))

(2) then \application_directory\python2.x\python easy_install ssl  and
\application_directory\python2.x\python easy_install hashlib

(3) update application PYTHON_EGG_CACHE param to where you want things to extract

(4) restart application

---

