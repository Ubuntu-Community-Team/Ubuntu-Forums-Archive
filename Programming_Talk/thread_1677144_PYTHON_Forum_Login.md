---
title: "*PYTHON* Forum Login"
date: 2011-01-28
forum: Programming Talk
---

### Post by chevloschelios on 2011-01-28
Hello. I am working on one program and I need there web login with cookies. Exactly I need to access forum and explore with python "Members Only" area. Can somebody help me ? I searched on google and the Code doesnt work:

```
import urllib, urllib2, cookielib

username = 'myuser'
password = 'mypassword'

cj = cookielib.CookieJar()
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))
login_data = urllib.urlencode({'username' : username, 'j_password' : password})
opener.open('http://www.example.com/login.php', login_data)
resp = opener.open('http://www.example.com/hiddenpage.php')
print resp
```

it redirects me again to login page. Thanks (sorry for my bad english)

---

### Post by lavinog on 2011-02-01
I don't know much about doing this type of stuff, but some sites block things that don't look like browsers.  You might want to look into modifying the user agent string.

---

### Post by Pyro.699 on 2011-02-01
It could be that your header information does not contain enough information (a method some sites use to prevent such automation). Why dont you try a more "professional" wrapper and see if that works...

Try [http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)

~Cody

---

