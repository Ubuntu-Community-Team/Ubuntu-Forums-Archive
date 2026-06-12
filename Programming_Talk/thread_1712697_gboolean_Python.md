---
title: "gboolean Python"
date: 2011-03-23
forum: Programming Talk
---

### Post by ki4jgt on 2011-03-23
So, I'm doing what I can to make educated guesses in programming. Since Devhelp has hardly anything on webkit, and what it does have is based on C, I've been trying to use a combination of the web, Devhelp and __doc__ strings.

So now I'm trying to set enable-private-browsing to TRUE in webkit.websettings (The doc string includes: enable-private-browsing with the understatement of: -> gboolean: Enable Private Browsing
    Enables private browsing mode


Can someone give me an example of how to set this? So I can understand gbooleans for the future.

I've tried webkit.WebSettings.enable-private-browsing("TRUE")
webkit.WebSettings.enable-private-browsing() = "TRUE"

So how does one express a gboolean in Python?

If you don't feel comfortable doing this then can you use another example? so I may get the idea?

---

### Post by d3v1150m471c on 2011-03-23
I'm currently getting some hands-on learning with python so i'm no expert. is gboolean different from boolean somehow? I can tell you that python's boolean uses : "True" or "False", opposed to "TRUE" or "FALSE". IE:

```

import os

var = True
foo = "/home"

if var is True:
 print "var is true!"

if os.path.exists(foo) is True:
 print "Home directory exists!"


```

---

### Post by surfer on 2011-03-23
moreover python treats any non-empty tuple, list or string or any non-zero number as True and the opposite as false.

```
#!/usr/bin/python

# -*- coding: utf-8 -*-

lst = []
if lst:
    print 'True'
else:
    print 'False'

lst = [2]
if lst:
    print 'True'
else:
    print 'False'

strg=''
if strg:
    print 'True'
else:
    print 'False'

i=0
if i:
    print 'True'
else:
    print 'False'
```

and so on...

---

