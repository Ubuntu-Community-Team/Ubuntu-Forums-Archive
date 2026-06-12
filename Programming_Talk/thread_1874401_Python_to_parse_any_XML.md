---
title: "Python to parse any XML?"
date: 2011-11-03
forum: Programming Talk
---

### Post by honeybear on 2011-11-03
Hello,

I would like to read this [http://rss.lemonde.fr/c/205/f/3050/index.rss](http://rss.lemonde.fr/c/205/f/3050/index.rss)  link into textmode.

Would you know how to parse and make it readable under python? 

Thank you

---

### Post by crdlb on 2011-11-03
That sounds like a job for feedparser (python-feedparser in Ubuntu). Its original author (Mark Pilgrim) recently deleted all of his websites, so you'll need to  [use the Internet Archive to look at the documentation]("http://web.archive.org/web/20110625112238/http://feedparser.org/") until someone rehosts it.

---

### Post by LemursDontExist on 2011-11-04
> **crdlb said:**
> That sounds like a job for feedparser (python-feedparser in Ubuntu). Its original author (Mark Pilgrim) recently deleted all of his websites, so you'll need to  [use the Internet Archive to look at the documentation]("http://web.archive.org/web/20110625112238/http://feedparser.org/") until someone rehosts it.

Alternatively, the built in python xml parsing modules might be adequate depending on your exact purpose.  Check out [http://docs.python.org/library/xml.dom.html#module-xml.dom](http://docs.python.org/library/xml.dom.html#module-xml.dom) or [http://docs.python.org/library/xml.dom.minidom.html#module-xml.dom.minidom](http://docs.python.org/library/xml.dom.minidom.html#module-xml.dom.minidom).

As a third option, [Beautiful Soup]("http://www.crummy.com/software/BeautifulSoup/") provides good xml parsing functionality.

There are a lot of options.

---

### Post by gsmanners on 2011-11-04
There's also python-libxml2 which I personally like, but good luck finding any good documentation.

---

### Post by crdlb on 2011-11-04
If we're naming general XML parsing libraries, my favorite is [python-lxml]("http://lxml.de/tutorial.html"). It provides a nicer API for libxml2.

---

