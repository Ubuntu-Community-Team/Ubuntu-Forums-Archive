---
title: "Anki Network Error"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by expatcm2 on 2013-09-06
I am trying to get Anki to access the server and synchronise the account.   I get the following error 

 > Unable to connect to the server.

Please check your network connection or try again in a few minutes.

Error was:

 Traceback (most recent call last):   File "/usr/share/anki/ankiqt/ui/getshared.py", line 67, in fetchData     URL + "search?t=%d&c=1" % self.type)   File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen     return _opener.open(url, data, timeout)   File "/usr/lib/python2.7/urllib2.py", line 406, in open     response = meth(req, response)   File "/usr/lib/python2.7/urllib2.py", line 519, in http_response     'http', request, response, code, msg, hdrs)   File "/usr/lib/python2.7/urllib2.py", line 438, in error     result = self._call_chain(*args)   File "/usr/lib/python2.7/urllib2.py", line 378, in _call_chain     result = func(*args)   File "/usr/lib/python2.7/urllib2.py", line 625, in http_error_302     return self.parent.open(new, timeout=req.timeout)   File "/usr/lib/python2.7/urllib2.py", line 406, in open     response = meth(req, response)   File "/usr/lib/python2.7/urllib2.py", line 519, in http_response     'http', request, response, code, msg, hdrs)   File "/usr/lib/python2.7/urllib2.py", line 444, in error     return self._call_chain(*args)   File "/usr/lib/python2.7/urllib2.py", line 378, in _call_chain     result = func(*args)   File "/usr/lib/python2.7/urllib2.py", line 527, in http_error_default     raise HTTPError(req.get_full_url(), code, msg, hdrs, fp) HTTPError: HTTP Error 404: Not Found


My network connection with the rest of the Internet is fine.  My Anki account status is working.  Any idea how to fix this?

---

### Post by expatcm2 on 2013-09-06
Ok ... solved that.  Bit disappointing really.  The version of Anki in the Software Center is so far out of date that it can no longer be used.

The solution is to download a .deb from this link
[http://ankisrs.net/](http://ankisrs.net/)
and have a happy life.

---

### Post by otax38 on 2013-10-14
Thanks a lot expatcm2

I couldn't understand that either.
Regards
otax.

---

### Post by Eric_Light on 2014-03-31
Thanks, expatcm2.  Still the case in April 2014.  You saved me a lot of time.  :)

---

