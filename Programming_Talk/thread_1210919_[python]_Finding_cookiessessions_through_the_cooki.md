---
title: "[python] Finding cookies/sessions through the cookielib"
date: 2009-07-12
forum: Programming Talk
---

### Post by Pyro.699 on 2009-07-12
Hey all,

When writing my python code and i have the need to save cookies i use this chunk of code:

```

global opener
cookiejar = cookielib.CookieJar()
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookiejar))

```

Then when it comes time to open a url i use:

```

opener.open("http://www.someurl.com")

```

This works great and i've never had a problem with it.

Ive come time to need to expand my code a bit and it has goten quite dynamic and i now need to figure out the cookies that are actually stored in the cookie builder.

So now i need to find out if the name of a cookie exists. For example on this forum several cookies are stored, one is [n]bbuserid[/b] which contains your user id. How would i search within the cookie jar to see if that cookie was created by this site. There will be cookies with the same name from other sites.

Thanks
~Cody Woolaver

---

### Post by unutbu on 2009-07-12
A CookieJar is an container object -- it can be iterated:

```

#!/usr/bin/env python
import cookielib, urllib2
cj = cookielib.CookieJar()
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))
r = opener.open("http://ubuntuforums.org/")

for cookie in cj:
    print('%s --> %s'%(cookie.name,cookie.value))

```

yields
```

bblastactivity --> 0
bblastvisit --> 1247413249

```

The attributes and methods available for Cookie objects can be found here:
[http://docs.python.org/library/cookielib.html#cookielib.CookieJar](http://docs.python.org/library/cookielib.html#cookielib.CookieJar)

---

### Post by Pyro.699 on 2009-07-12
Thanks, what about sessions? Is there anyway to get those?

(Information set by $_SESSION)

---

### Post by Pyro.699 on 2009-07-12
[http://ca.php.net/manual/en/features.sessions.php](http://ca.php.net/manual/en/features.sessions.php)
> 
Session support in PHP consists of a way to preserve certain data across    subsequent accesses. This enables you to build more customized applications    and increase the appeal of your web site.


[http://php.about.com/od/learnphp/qt/session_cookie.htm](http://php.about.com/od/learnphp/qt/session_cookie.htm)
> 
Sessions are not reliant on the user allowing a cookie. They work instead like a token allowing access and passing information while the user has their browser open. The problem with sessions is that when you close your browser you also lose the session. So, if you had a site requiring a login, this couldn't be saved as a session like it could as a cookie, and the user would be forced to re-login every time they visit.


I gave quotes because i know myself, i wouldn't be able to give you a clear description.

Its basically another way of saving data within the browser.

Thanks again for your help
~Cody Woolaver

---

### Post by hongquan1987 on 2009-10-23
> **Pyro.699 said:**
> Thanks, what about sessions? Is there anyway to get those?

(Information set by $_SESSION)

The ìnormation contained in $_SESSION is stored on the server by PHP. You can't get them by a client-sided script.
Maybe u should create a PHP script to retrieve $_SESSION and your Python app would request this PHP script.

---

### Post by Can+~ on 2009-10-23
> **hongquan1987 said:**
> The ìnormation contained in $_SESSION is stored on the server by PHP. You can't get them by a client-sided script.
Maybe u should create a PHP script to retrieve $_SESSION and your Python app would request this PHP script.

PHP does store session information, but that doesn't mean that is the only language that does that.

In fact, a session is just an abstraction of storing a file inside the server hard drive with a hash key and handling that key to the client.

Other languages and toolkits provide this kinds of things. [Django]("http://docs.djangoproject.com/en/dev/topics/http/sessions/") in python can store sessions, JSP "sessionBeans", etc.

---

