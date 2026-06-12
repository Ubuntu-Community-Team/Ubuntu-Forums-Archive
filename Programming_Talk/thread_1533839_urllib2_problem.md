---
title: "urllib2 problem"
date: 2010-07-18
forum: Programming Talk
---

### Post by chevloschelios on 2010-07-18
Hello,

I have trouble. I want to download source code of one website. If I use urllib2, python raise error that page blocked connection. The page is [http://pokec.sk](http://pokec.sk) . Is possible to download source ? Thanks.

---

### Post by Zugzwang on 2010-07-18
Test if downloading the site using wget works. For this, in the terminal, try something like:
```

cd /tmp
wget <yoursite>

```

Do you get an error? If yes, the owner of that site doesn't want to get it processed using anything else than a browser, which you should respect. If not, please copy&paste the precise error message of your Python program here.

---

### Post by chevloschelios on 2010-07-18
I try wget and it works fine. I will post the error tommorow coz i have the program on second PC and i dont have much time now. Thanks you.

---

### Post by soltanis on 2010-07-19
If wget works, then its probably something wrong with your call to urllib2 rather than the website discriminating based on your user agent (which by the way, feel free to ignore, the Internet is a public place).

---

### Post by chevloschelios on 2010-07-19
Ok, here is error :
```

/usr/bin/python -u  "/home/remixus/Plocha/a.py"
Traceback (most recent call last):
  File "/home/remixus/Plocha/a.py", line 4, in <module>
    s=urllib2.urlopen('http://www.azet.sk')
  File "/usr/lib/python2.6/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 391, in open
    response = self._open(req, data)
  File "/usr/lib/python2.6/urllib2.py", line 409, in _open
    '_open', req)
  File "/usr/lib/python2.6/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 1161, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.6/urllib2.py", line 1136, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error [Errno 104] Connection reset by peer>
```and the program
```

import urllib2
s=urllib2.urlopen('http://www.pokec.sk')
print s

```

---

### Post by StephenF on 2010-07-19
I can indeed confirm it is the user agent that is not liked by the server but this works.
```

r = urllib2.Request("http://www.pokec.sk", headers={"User-Agent": "Python-urlli~"})
urllib2.urlopen(r).read()

```
Replace the ~ with a b and it fails again.

---

### Post by chevloschelios on 2010-07-19
Thank you so much !!

---

### Post by chevloschelios on 2010-07-19
I want you ask something again :) If you type [http://pokec.sk](http://pokec.sk) to browser there is login. How can I log in using python ? Thanks for reply.

---

### Post by StephenF on 2010-07-19
I just looked through the simpler login page and found the form tag has the action:
```

https://prihlasenie.azet.sk/overenie?uri=http%3A%2F%2Fpokec.azet.sk&isWap=0

```
This is where to send your http(s) << s for secure request also type="post" so it's a post request and the names on the text and password inputs are "form[username]" and "form[password]"

This page is interesting as it will tell you how to encode the url. I assume you just tack the encoded form data onto the rest of the url and send it although there is probably an urllib way of doing this. Then prepare to receive a session cookie, I guess.
[http://en.wikipedia.org/wiki/POST_%28HTTP%29](http://en.wikipedia.org/wiki/POST_%28HTTP%29)

Edit:
Here is my best guess as I don't have an account on this site and I can't read this anyway in order to set one up.
```

import urllib
import urllib2
import os

username = "me"
password = "unknown"
filename = "sitedump.html"

r = urllib2.Request("https://prihlasenie.azet.sk/overenie?uri=http%3A%2F%2Fpokec.azet.sk&isWap=0",
urllib.urlencode({"form[username]":username, "form[password]":password}), {"User-Agent": "Python-urlli~"})
with open(filename, "w") as f:
   f.write(urllib2.urlopen(r).read())
os.system("firefox file://" + os.path.join(os.getcwd(), filename))

```
This gives me the login page with the supplied username correctly filled in which is very encouraging and according to what I have gleaned from the docs any session cookies are handled by the fourth parameter of urllib2.Request, "origin_req_host" and has a default value that isn't None so hopefully that means there is automatic behaviour.

---

### Post by chevloschelios on 2010-07-19
Thanks again ! I just want to ask...how i can search google using python ? for example i type to google something and google show me the best webpages ... and the program can show me this address. Sorry for my bad english, i hope you understand

---

### Post by StephenF on 2010-07-19
You can glean that information from the URL bar. It's not hard to decode. Anyway that last solution needs some work. I tried using the technique on some sites I have membership of without any luck.

---

### Post by Some Penguin on 2010-07-19
> **chevloschelios said:**
> Thanks again ! I just want to ask...how i can search google using python ? for example i type to google something and google show me the best webpages ... and the program can show me this address. Sorry for my bad english, i hope you understand


[http://www.google.com/accounts/TOS?hl=en&loc=US](http://www.google.com/accounts/TOS?hl=en&loc=US)

5.3	You agree not to access (or attempt to access) any of the Services by any means other than through the interface that is provided by Google, unless you have been specifically allowed to do so in a separate agreement with Google. You specifically agree not to access (or attempt to access) any of the Services through any automated means (including use of scripts or web crawlers) and shall ensure that you comply with the instructions set out in any robots.txt file present on the Services.

---

### Post by soltanis on 2010-07-20
[Google provides a search API.]("http://code.google.com/apis/ajaxsearch/")

[http://dcortesi.com/2008/05/28/google-ajax-search-api-example-python-code/](http://dcortesi.com/2008/05/28/google-ajax-search-api-example-python-code/)

---

### Post by Some Penguin on 2010-07-20
...which is strictly for use on web pages to be displayed to end users. It's still a TOS violation to do otherwise, and violating this in volume is likely to have your search requests fail because you aren't passing the CAPTCHAs that will start appearing.


[http://code.google.com/apis/ajaxsearch/terms.html](http://code.google.com/apis/ajaxsearch/terms.html)
"You agree that You are responsible for your own conduct and content while using the Service and for any consequences thereof. You agree to use the Service only for purposes that are legal, proper and in accordance with these Terms of Use and any applicable policies or guidelines. By way of example, and not as a limitation, You agree that when using the Service, You will not, and will not permit users or other third parties to:
...
use any robot, spider, site search/retrieval application, or other device to retrieve or index any portion of Google Search Results or to collect information about users for any unauthorized purpose
...
copy, store, archive, republish, or create a database of Google Search Results, in whole or in part, directly or indirectly, except that You may display Google Search Results that have been "clipped" through an end user-requested action, provided that You comply with the attribution requirements described in Section 2.3 below;
"

---

### Post by StephenF on 2010-07-20
I am not a lawyer... but...

I recall it has already been proven in court that robots.txt has no legal force behind it and the site owners would have to prove they had a substantial claim to bandwidth theft. That or fraud such as providing a search service stripped of Google ads and their own inserted.

Funny how they hate web crawlers but have so many of their own.

---

