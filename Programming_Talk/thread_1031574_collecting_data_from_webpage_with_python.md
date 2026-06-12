---
title: "collecting data from webpage with python"
date: 2009-01-05
forum: Programming Talk
---

### Post by sujoy on 2009-01-05
I am trying to write a console program that can fetch my internet usage details from this site [http://10.240.43.216](http://10.240.43.216)

I managed to set the User Agent and cookies, but I cannot wrap my head around submitting the login data, to the server.

```

import urllib2, cookielib
import ClientForm

USER_AGENT = "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.5) Gecko/2008122113 GranParadiso/3.0.5"
SITE = "http://10.240.43.216/"
USERNAME = "myusername"
PASSWORD = "mypassword"

request = urllib2.Request (SITE)
request.add_header ('User-Agent', USER_AGENT)

cj = cookielib.CookieJar ()
opener = urllib2.build_opener (urllib2.HTTPCookieProcessor (cj))

response = opener.open (request)

forms = ClientForm.ParseResponse (response, backwards_compat = False)
response.close ()

form = forms[0] # the login form
print form

form['username'] = USERNAME
form['password'] = PASSWORD

```

after this if i do the following

```

request2 = form.click()

try:
     response2 = opener.open(request2)
except urllib2.HTTPError, response2:
     pass

response2.read()

```

i get this output,

```
 '<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">\n<HTML><HEAD>\n<TITLE>400 Bad Request</TITLE>\n</HEAD><BODY>\n<H1>Bad Request</H1>\nYour browser sent a request that this server could not understand.<P>\nInvalid URI in request POST /../secu/myportallogin.jsp HTTP/1.1<P>\n</BODY></HTML>\n'
```

[this]("http://dpaste.com/105699/") is the webpage that contains the login form.

Any help is appreciated.

---

