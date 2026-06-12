---
title: "[Python] Urllib and proxy"
date: 2011-07-17
forum: Programming Talk
---

### Post by tauh on 2011-07-17
Hi!

I have recently started to learn Python 3.2 and now i'm trying to use ProxyHandler.

I want to know how i can check the status of the proxy. If it really works. 

If i write *[http://x.x](http://x.x)* in proxyhandler as the ip/adress the program still downloads google.com and prints it.

I want to print google.com (html code) only if the proxy really works!

```

import urllib.request, urllib.response, os


try:
	
	handler = urllib.request.ProxyHandler({'HTTP': 'http://x.x:80'})
	opener = urllib.request.build_opener(handler)
	urllib.request.install_opener(opener)
	
	uo = urllib.request.urlopen("Http://google.com").read()
	
	print(uo)
	
except Exception:
	print("Exception")
else:
	print("Else")
	
os.system("Pause")

```

---

