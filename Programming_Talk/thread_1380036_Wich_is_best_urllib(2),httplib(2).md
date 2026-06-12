---
title: "Wich is best: urllib(2),httplib(2)  ?"
date: 2010-01-13
forum: Programming Talk
---

### Post by baskar007 on 2010-01-13
hi friends,
i have an idea to build an small web application in python, For the web interface python have these modules and so..

i want to know which module is fast and stable for download and parallel (thread) connections?

httplib,
httplib2,
urllib,
urllib2
or other that you know

friends give your opinion,

thanks in advance.

---

### Post by zippaplick on 2010-01-13
urllib2 should do just fine. I use it to make many threaded/parallel requests.

This doc covers it nicely:

[http://www.voidspace.org.uk/python/articles/urllib2.shtml](http://www.voidspace.org.uk/python/articles/urllib2.shtml)

---

### Post by baskar007 on 2010-01-15
thanks

---

### Post by MOdMac on 2010-01-20
httplib2 is the most feature rich lib.
Its particularly good if you want to interface with web sevices.  Gives you support for different kinds of authentication, compression and supports client caching.

---

### Post by baskar007 on 2010-01-20
I am using httplib, because all of other modules are seemes to be little slow in threading connections.

thanks for your reply.

---

