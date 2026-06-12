---
title: "time_t and saving cookies in Python"
date: 2009-03-13
forum: Programming Talk
---

### Post by twisted_steel on 2009-03-13
I have a Python program that recently stopped working on Ubuntu Hardy 32-bit.  I have a feeling that this is due to either a recent update or perhaps a difference in the representation of time_t on 64-bit.  It is possible that the one expiration date just updated recently to a later year.

I'm just trying to save a cookie with
```
self.cookiejar.save(self.cookieFile)
```This works fine on 64-bit Intrepid, but not on 32-bit Hardy.  I know I should probably test a few more iterations in between, but I don't have that luxury.


```
File "/usr/lib/python2.5/_LWPCookieJar.py", line 89, in save
    f.write(self.as_lwp_str(ignore_discard, ignore_expires))
  File "/usr/lib/python2.5/_LWPCookieJar.py", line 75, in as_lwp_str
    r.append("Set-Cookie3: %s" % lwp_cookie_str(cookie))
  File "/usr/lib/python2.5/_LWPCookieJar.py", line 35, in lwp_cookie_str
    time2isoz(float(cookie.expires))))
  File "/usr/lib/python2.5/cookielib.py", line 98, in time2isoz
    year, mon, mday, hour, min, sec = time.gmtime(t)[:6]
ValueError: timestamp out of range for platform time_t
```The date on the cookie for the first domain saved from the working computer is
```
expires="2037-12-30 16:00:00Z"
```The date on the cookie for the second domain is
```
expires="2059-03-13 01:05:25Z"
```It seems like this could be related to the Year 2038 bug, but I'm not sure.  Does anyone have any thoughts on what might be causing this?  Also, any possible suggestions on handling this error?

Thanks :)

---

### Post by twisted_steel on 2009-03-22
Apparently this is a problem with the LWPCookieJar.  Changing to MozillaCookieJar allowed the cookie to be saved without issue on both 32-bit and 64-bit platforms.

---

