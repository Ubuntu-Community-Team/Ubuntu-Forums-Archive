---
title: "Learning to post HTTPS forms w/ python"
date: 2008-12-18
forum: Programming Talk
---

### Post by jimbojones on 2008-12-18
Hello, I am trying to figure out how to post HTTPS forms through Python.  My goal is to login to a website through an HTTPS connection and keep the session active so I can preform tasks once I am logged in.  As an attempt to learn, I tried to make a simple script that I could log into myspace with since it uses HTTPS.  I tried 2 different methods but I can not seem to grasp the concept.  I have also read some online article and just cann't get wrapped around this... if anyone could give me some pointers I would appreciate it.  I run Python 2.6 and I am trying to make a small app I can use at work, I just picked myspace as an example because it was an HTTPS site

First attempt was with regular built in's httplib ,urllib

```

import httplib ,urllib
username ="myusername"
password="mypassword"
conn = httplib.HTTPSConnection( "https://secure.myspace.com:443" )
print conn
params = urllib.urlencode({'ctl00_cpMain_LoginBox_Email_Textbox': username, 'ctl00_cpMain_LoginBox_Password_Textbox': password})
print params
headers = {"Content-type": "application/x-www-form-urlencoded"}
print headers
conn.request("POST", "/index.cfm?fuseaction=login.process", params, headers )
response = conn.getresponse()
print response

```

and I receive back...

```
error: [Errno 10060] A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond
```


My second attempt i use urllib and the 3rd party httplib2

```

import urllib
import httplib2
username ="myusername"
password="mypassword"

url = 'https://secure.myspace.com/index.cfm?fuseaction=login.process'
data = {'ctl00_cpMain_LoginBox_Email_Textbox': username, 'ctl00_cpMain_LoginBox_Password_Textbox': password}
body = urllib.urlencode(data)
print body
h = httplib2.Http()
response, content = h.request(url,method="POST", body=body)
print response
print content

```

The error i get back here does not look good,

```

.....File "C:\Python26\lib\httplib2\__init__.py", line 736, in connect
    sock.settimeout(self.timeout)
  File "<string>", line 1, in settimeout
TypeError: a float is required

```


Please if anyone can tell me what I am missing(hopefully something stupid) I would be grateful...I am stumped :confused:

---

### Post by TreeFinger on 2008-12-18
why can I not find "httplib2" library on the python docs page? i can find urllib2 ... and httplib ...

---

### Post by mssever on 2008-12-19
> **TreeFinger said:**
> why can I not find "httplib2" library on the python docs page? i can find urllib2 ... and httplib ...
The OP stated that httplib2 is a third-party lib. That's why it isn't listed on the Python docs page.

---

### Post by jimbojones on 2008-12-19
> **TreeFinger said:**
> why can I not find "httplib2" library on the python docs page? i can find urllib2 ... and httplib ...

Sorry for that...httplib2 can be found here, [http://code.google.com/p/httplib2/](http://code.google.com/p/httplib2/)
I also believe they include it in the activestate version of python but not plain vanilla python.

I just thought I would add that I browsed the source code for my space to get those field names and the url....but maybe I am trying to connect to the wrong url? Also, I have WebDeveloper installed for firefox which can lay out the form data for you nice and neat, for what its worth.

I would prefer to use the standard builtins if I can but at this point anything that works would be great.  Thanks again

---

### Post by ratmandall on 2008-12-19
Maybe the mechanize module can help you.
[http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)

---

### Post by jimbojones on 2008-12-19
> **ratmandall said:**
> Maybe the mechanize module can help you.
[http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)

Thank you, I may take a look at that.

Doing some more digging I found something related to my errors in httplib2   [http://code.google.com/p/httplib2/issues/detail?id=39](http://code.google.com/p/httplib2/issues/detail?id=39)

The user supplies a .diff file as a patch, i used the patch utility to try and patch the file, ill see what happens

---

