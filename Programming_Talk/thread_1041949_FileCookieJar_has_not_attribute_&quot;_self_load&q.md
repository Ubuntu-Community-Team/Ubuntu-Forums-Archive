---
title: "FileCookieJar has not attribute &quot;_self_load&quot; ?"
date: 2009-01-17
forum: Programming Talk
---

### Post by babanner on 2009-01-17
I ran into this problem and i cannot find a solution. 

Here is my code

```

import urllib.request, urllib.parse,http.cookiejar
url="http://localhost/test.php"
cs=http.cookiejar.FileCookieJar()
cs.load("ckie2",ignore_discard=False, ignore_expires=False)
opener=urllib.request.build_opener(urllib.request.HTTPCookieProcessor(cs))
y=opener.open(url)
print(y.read())
print(cs)

```

It throws an error: FileCookieJar has no attribute '_self_load' . 
I am using python 3.0 Thanks.

---

