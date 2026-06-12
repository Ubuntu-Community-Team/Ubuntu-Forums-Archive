---
title: "shorturl API of my site"
date: 2009-06-09
forum: Programming Talk
---

### Post by dentaku65 on 2009-06-09
Hi all,
first of all I don't know if I can post such thread here; but I guess yes.

I've created my first API of my shorturl site [Yep]("http://yep.it")

The API works in this way:
[http://yep.it/api.php?url=](http://yep.it/api.php?url=)[COLOR="Red"]<url>[/COLOR]

Way of use

**Shortening this thread as shorturl:**
[http://yep.it/api.php?url=](http://yep.it/api.php?url=)[COLOR="Red"]http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1183044[/COLOR]
will give the randomly string alphanumeric of five chars as plain text:
```
[http://yep.it/](http://yep.it/)[COLOR="Red"]hno4z[/COLOR]
```

**Track the shorturl:**
[http://yep.it/api.php?track=](http://yep.it/api.php?track=)[COLOR="Red"]hno4z[/COLOR]
will display the shorturl with clicks on rounded brackets
```
http://yep.it/hno4z (0)
```

**Check this shorturl:**
[http://yep.it/api.php?check=](http://yep.it/api.php?check=)[COLOR="Red"]hno4z[/COLOR]
will output the contents of the short url:
```
Short URL: http://yep.it/hno4z
URL: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1183044](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1183044)
Content: shorturl API of my site Programming Talk shorturl API of my site, ubuntu forums,ubuntu linux,ubuntu,linux forum,ubuntu forum,linux ubuntu,ubuntu support,ubuntu help,ubuntu linux help
Date: 2009-06-14 15:46:47 Clicks: 0
```
If someone here is creating some apps that needs shorturl converter I'll be pleased that use my API

Feedbacks are really welcome and appreciated.

---

### Post by loomsen on 2009-08-03
Indeed, I am very interested :)

Thx for your PM, I'm already using your service here n there.

What I wanted to ask, is there a simple way to access the service from the CLI? Have you written some script or so?

---

