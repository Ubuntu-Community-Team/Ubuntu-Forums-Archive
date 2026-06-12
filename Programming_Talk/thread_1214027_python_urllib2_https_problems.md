---
title: "python urllib2 https problems"
date: 2009-07-15
forum: Programming Talk
---

### Post by acey on 2009-07-15
I seem to be having a problem on ubuntu jaunty using python urllib2 and https. The following code works on ubuntu hardy, but not on jaunty:

```

#!/usr/bin/python
import urllib2

print urllib2.urlopen("https://www.google.com").read()

```

When executing this on jaunty, I get the following:
```
Traceback (most recent call last):
  File "./test4.py", line 5, in <module>
    print urllib2.urlopen("https://www.google.com").read()
  File "/usr/lib/python2.6/urllib2.py", line 124, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 383, in open
    response = self._open(req, data)
  File "/usr/lib/python2.6/urllib2.py", line 401, in _open
    '_open', req)
  File "/usr/lib/python2.6/urllib2.py", line 361, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 1138, in https_open
    return self.do_open(httplib.HTTPSConnection, req)
  File "/usr/lib/python2.6/urllib2.py", line 1105, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error [Errno 0] Error>
```

When executing this on hardy, I get the expected result:
```
<!doctype html><html><head><meta http-equiv="content-type" content="text/html; charset=ISO-8859-1"><title>Google</title><script>window.google={kEI:"ORFeStPpGcmF-AaZ6fHhDA",kEXPI:"17259,20760,21105",kCSIE:"17259,20760,21105",kCSI:{e:"17259,20760,21105",ei:"ORFeStPpGcmF-AaZ6fHhDA"},kHL:"nl"};
window.google.sn="webhp";window.google.timers={load:{t:{start:(new Date).getTime()}}};try{window.google.pt=window.gtbExternal&&window.gtbExternal.pageT()||window.external&&window.external.pageT}catc
...

```

Does anyone have an idea of what could be wrong?


EDIT:
I've tried this on an machine that was upgraded to jaunty and it works there, but I have no idea why it doesn't work on the newly installed jaunty, maybe I am missing a package? I have no idea which one it could be though

EDIT2:
I compared packages on both machines, the one on which it's not working has more packages and has 2 pythons installed: 2.5 and 2.6, while the working one only has 2.5.

When running with 2.5 on the broken machine I get the following:
```

Traceback (most recent call last):
  File "./test4.py", line 5, in <module>
    print urllib2.urlopen("https://www.google.com").read()
  File "/usr/lib/python2.5/urllib2.py", line 124, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 381, in open
    response = self._open(req, data)
  File "/usr/lib/python2.5/urllib2.py", line 399, in _open
    '_open', req)
  File "/usr/lib/python2.5/urllib2.py", line 360, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.5/urllib2.py", line 1115, in https_open
    return self.do_open(httplib.HTTPSConnection, req)
  File "/usr/lib/python2.5/urllib2.py", line 1082, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error (8, 'EOF occurred in violation of protocol')>

```

---

### Post by pokerbirch on 2009-07-15
Not sure what the problem is, but sounds like a missing library or package. I've done a lot of web scraping and can highly recommend using pyCurl. Performance is superb, but my main reason for using it is because cookies and gzip can be set to be automatically handled...IF you need those features.

---

### Post by acey on 2009-07-15
Thanks for the suggestion, if this was a new project, I would definitely look at using pyCurl. However the above example code is the reason an existing script is not working. I would prefer to get it working without having to rewrite it :)

---

