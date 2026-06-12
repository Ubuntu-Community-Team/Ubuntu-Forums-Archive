---
title: "Alittle python help"
date: 2008-11-06
forum: Programming Talk
---

### Post by blithen on 2008-11-06
Here is what I'm basically trying to code

```
os.system("lynx [www.magiccards.info/random.html](www.magiccards.info/random.html) -dump"
os.system("grep the dumped information for certain pieces of information.")
```
Think anyone could help?

---

### Post by kcode on 2008-11-06
What errors are you getting ??

Have you imported 'os' module?
Hope you have done this:
```

import os

```
And closed bracket is missing in first line.

---

### Post by raf_kig on 2008-11-06
What you probably want to use is urllib2;;

```

import urllib2

f = urllib2.urlopen('http://example.com')

for line in f:
    print line #do your matching here

```
The module BeautifulSoup might be useful for the parsing job, google for it, there are lots of howtos.


If you want to use external programs have a look at the os.popen* functions.

Regards

raf

---

