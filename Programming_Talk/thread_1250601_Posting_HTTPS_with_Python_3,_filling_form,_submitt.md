---
title: "Posting HTTPS with Python 3, filling form, submitting, clicking link"
date: 2009-08-26
forum: Programming Talk
---

### Post by exutable on 2009-08-26
Hello,

I am trying to create a python script that can log into [https://telmore.dk]("https://telmore.dk") for me and send a web-sms.

The website is secure, hence https but all I need to do is a fill the username and password forms, press the submit button and then click links.  I am able to retrieve the source with a script that I wrote but I can't figure out how to actually fill the form with Python.

I have done something similar with perl where I simply specified the IDs of the input boxes I wanted to fill.  Would perl be a better language for this, although I'm not very familiar? Will python suffice?  Is there a better way to send sms messages in python? How would this be accomplished with Python?

---

### Post by unutbu on 2009-08-26
If you install python-pycurl (400 KB), perhaps the following would work.
(Change USER and PASS as appropriate).

Also, the python-pycurl package is probably setup for Python2.x, not Python3. So sorry if this is not what you are looking for.

[PHP]#!/usr/bin/env python
from curl import Curl
import pycurl
import sys

class TCurl(Curl):
    def login(self):
        'Establish a login session.'
        self.post('j_security_check',
                  (('username','USER'), 
                   ('password','PASS'),
                   )
                  )

acurl=TCurl(base_url='https://telmore.dk/')
try:
    acurl.login()
except pycurl.error,err:
    exc_tuple=sys.exc_info()
    sys.stderr.write(pformat(exc_tuple))
    exit(1)

acurl.get()
content=acurl.body()
print(content)
[/PHP]

For more info on pycurl:
See
/usr/lib/python*/site-packages/curl/__init__.py
[http://code.activestate.com/recipes/267255/](http://code.activestate.com/recipes/267255/)
[http://pycurl.sourceforge.net/](http://pycurl.sourceforge.net/)
[http://curl.haxx.se/libcurl/c/](http://curl.haxx.se/libcurl/c/)

---

### Post by exutable on 2009-08-27
Hmmm,

definitely on the right track, for some reason it keeps pulling an error page instead of a log in though....

---

### Post by unutbu on 2009-08-27
I don't know if there is an easier way, but you could use wireshark (also in the repos) to capture the HTTP traffic on port 80 as you login. Then sift through the captured packets to see what your browser sends to login. Once you know exactly what you are supposed to be sending, the Python code can be written (maybe?) easily.

---

### Post by Clopin on 2009-08-27
Lately I've been writing some Gaia bots using Python 2.4, and just edited a bit of it, so you could use it.

What it does is, that it simulates a HTTP request to Telmore login, and, hopefully, logs in, using this code. I'm pretty sure you can do the same for filling other forms as well.
You can find all the various request identifiers (j_password for an example) using TamperData.

I can't test it out, so you oughta mess around with it.
```
import urllib
import urllib2
import sys
import cookielib
import hashlib

cookieJar = cookielib.LWPCookieJar()
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookieJar))
#opener.addheaders = [('User-agent', "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)")]

opener.addheaders = [('User-agent', "Mozilla/5.0")]

username = "USERNAME"
password = "PASSWORD"

#print hashlib.md5(hashlib.md5(password).hexdigest()).hexdigest()
url = "https://web.telmore.dk/j_security_check"

form = { "j_username" : username,
         "j_password" : password }
		 
encodedForm = urllib.urlencode(form)
request = urllib2.Request(url, encodedForm)
page = opener.open(request)
contents = page.read()

#Example: Check contents for a string in the login page.
#If "blabla" in contents then do write "Login successful"
```

---

### Post by exutable on 2009-08-27
AHA!

That was it, got the source and everything.  What lib would I use for clicking links?

Thanks,

Dane

---

### Post by exutable on 2009-08-27
doh I could just redirect too

---

