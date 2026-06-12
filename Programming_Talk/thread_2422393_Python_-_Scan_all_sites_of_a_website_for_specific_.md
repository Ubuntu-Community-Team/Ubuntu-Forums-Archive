---
title: "Python - Scan all sites of a website for specific URLs"
date: 2019-07-06
forum: Programming Talk
---

### Post by hagbardceline2 on 2019-07-06
I want to scan my forum for specific links. All links look like this: [http://www.vbulletinxyz-forum.tld/forum/showthread.php?t=17590]("http://www.vbulletinxyz-forum.org/forum/showthread.php?t=17590") except for the number at the end.
Currently I am using the following code, but it only works for one specific URL, not all threads of the forum. How would I have to change the code to let it scan all threads?

```
import urllib
mypath = "http://vbulletin-forumxyz.tld/forum/showthread.php?t=1"
mylines = urllib.urlopen(mypath).readlines()
for item in mylines:
    if "http://specific.tld" in item:
        print item[item.index("http://specific.tld"):]
```

---

### Post by hagbardceline2 on 2019-07-07
**Solution:**

```
for t in range(0,400000):
``` defines the range. Depending on how many threads the site has, you would have to adjust this number.

Here the full code for Python 3:

```
import urllib.request
import time
import codecs

def mypath(t):
    return "http://www.someforum.org/forum/showthread.php?t={}".format(t)


for t in range(0,400000):
    conn = urllib.request.urlopen(mypath(t))

    # check status code
    if conn.getcode() != 200:
        continue

    mylines = conn.read().decode('windows-1251').splitlines()

    for item in mylines:
        if "http://someurl.tld" in item:
            print(item)

   # avoid fetching to fast (you might get banned otherwise)
   # time.sleep(0.5)
```

---

