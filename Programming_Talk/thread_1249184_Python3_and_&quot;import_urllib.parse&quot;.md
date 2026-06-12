---
title: "Python3 and &quot;import urllib.parse&quot;"
date: 2009-08-25
forum: Programming Talk
---

### Post by Bertik on 2009-08-25
Hello,

could somebody help please?
I am total newbie with Python programing and I was trying to run a script I found on the net. Here it is
```
#!/usr/bin/python3

import urllib.parse
import httplib2

http = httplib2.Http()

url = 'http://www.example.com/login'   
body = {'USERNAME': 'foo', 'PASSWORD': 'bar'}
headers = {'Content-type': 'application/x-www-form-urlencoded'}
response, content = http.request(url, 'POST', headers=headers, body=urllib.parse.urlencode(body))

headers = {'Cookie': response['set-cookie']}

url = 'http://www.example.com/home'   
response, content = http.request(url, 'GET', headers=headers)
```

When I run it I am geting error
ImportError: No module named parse

I was trying to search for Python module named Parse in Synaptics, but there is like zillion results.
How can I install the right parse module please? Or where do I get it?

---

### Post by Can+~ on 2009-08-25
> Note

The urllib module has been split into parts and renamed in Python 3.0 to urllib.request, urllib.parse, and urllib.error. The 2to3 tool will automatically adapt imports when converting your sources to 3.0. Also note that the urllib.urlopen() function has been removed in Python 3.0 in favor of urllib2.urlopen().

[http://docs.python.org/library/urllib.html#module-urllib](http://docs.python.org/library/urllib.html#module-urllib)

Run it with python3... or look for python2.6 (or less) examples.

---

### Post by Bertik on 2009-08-25
Thank you for pointing me to right direction.

I am using Geany to edit the code in, and it was executing the code in Python 2.x
I have modified config file for Geany to execute with Python3 and all is OK now.

Thanks again

---

