---
title: "Login/open a webpage with Python"
date: 2014-03-16
forum: Programming Talk
---

### Post by Elastic_Potential on 2014-03-16
In order to get information from my job's website (as the first step to a larger utility), I wanted to simply modify an existing code which I use to log-in and display html data.  Here's the script after my modification:
```

#! /usr/bin/env python

import re
import urllib,urllib2,cookielib

data1={
'userID':'[my id]', 'userPin':'[my password]'
}

data1=urllib.urlencode(data1)
cookiejar1=cookielib.CookieJar()
opener=urllib2.build_opener(urllib2.HTTPCookieProcessor(cookiejar1))
# Log-in page
opener.open('website.com',data1)
# Same URL, but it will open the "dashboard" once logged-in
resp=opener.open('website.com/subpage')
print(resp.read())

```

However, the html data suggests that it's still just on the login screen.  This works fine for retrieving data from Facebook mobile, but not for this.  Any suggestions?

---

### Post by Elastic_Potential on 2014-03-16
I'm now trying mechanize.  I received a "*'module' object has no attribute 'Browser'*" error, but this occurred because one of my test scripts was named "mechanize.py;" renaming it solved this issue.

With an updated script, it will take me to the page I want using this modification:
```

#!/usr/bin/env python

import mechanize
import cookielib

browser = mechanize.Browser()
browser.open('website.com')
browser.select_form(nr = 0)
browser.form['userID'] = 'my username'
browser.form['userPin'] = 'my password'
browser.submit()

browser.open('website.com/subpage')
# Populates a list of available forms, for my reference
for f in browser.forms():
        print f
# Edits the endDate form
browser.form['endDate'] = '06/10/2014'
browser.submit()
print browser.response().read()

```
but it won't let me edit the endDate form

---

### Post by Elastic_Potential on 2014-03-16
Okay, so with the help of one of my really good friends, we got a script to fill in boards.  The problem, I now realize, is that I need to get some information from JavaScript -__- Using a JavaScript blocker, I can't press the "Search" button.  Will be working on that, I guess.

---

### Post by Elastic_Potential on 2014-03-16
duplicate post (no idea how this happened)

---

