---
title: "Python urllib2 Exceptions &amp;  Set page timeout"
date: 2009-04-26
forum: Programming Talk
---

### Post by Pyro.699 on 2009-04-26
```

import urllib2, sys

try:
    open = urllib2.urlopen("http://mypage.com") #returns a page that is only ~37 bytes small
    sys.stdout.write(open.read())
except IOError:
    sys.stdout.write("Failed")

```
That code is the code i'm using.

Anyways, what im trying to create is a simple application that involves this program checking a specified url at a given interval and reporting it back to a web page. I have everything done and its working but i noticed some errors when my internet goes down.

I looked at the urllib2 documentation and couldnt find all the exceptions it throws but i do know that when a webpage fails to load it throws **IOError** and was wondering if there were any other exceptions that could be thrown if you were unable to connect to the webpage. Since the script refreshes the page every 5 seconds, id like to place a pageload-timeout of 4.5 seconds but am unsure how to do that.

Thanks
~Cody Woolaver

---

### Post by myrtle1908 on 2009-04-26
From memory you need to set a timeout on the socket.  For example (untested):-

[PHP]
import socket
import urllib2

socket.setdefaulttimeout(seconds)

open = urllib2.urlopen("http://mypage.com") #returns a page that is only ~37 bytes small[/PHP]

---

