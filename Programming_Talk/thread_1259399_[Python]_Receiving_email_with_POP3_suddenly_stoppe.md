---
title: "[Python] Receiving email with POP3 suddenly stopped working"
date: 2009-09-06
forum: Programming Talk
---

### Post by fiddler616 on 2009-09-06
Hello,

I've been messing around with Python and email, and a few days ago created the following, which gets the most recent email to a given address:

[PHP]def getMessage():  
    M = poplib.POP3_SSL('pop.gmail.com', 995)
    M.user("<address>")
    M.pass_("<password")
    message = ""
    for i in M.retr(1)[1]:
        message += i
    M.dele(1)#Added later
    M.quit()
    return message[/PHP]

It worked fine, but now when I run it, it raises a bunch of errors:
```
Traceback (most recent call last):
  File "wikiomatic.py", line 99, in <module>
    message = getMessage()
  File "wikiomatic.py", line 26, in getMessage
    for i in M.retr(1)[1]:
  File "/usr/lib/python2.6/poplib.py", line 224, in retr
    return self._longcmd('RETR %s' % which)
  File "/usr/lib/python2.6/poplib.py", line 159, in _longcmd
    return self._getlongresp()
  File "/usr/lib/python2.6/poplib.py", line 135, in _getlongresp
    resp = self._getresp()
  File "/usr/lib/python2.6/poplib.py", line 128, in _getresp
    raise error_proto(resp)
poplib.error_proto: -ERR Message number out of range.

```
What happened?

Thanks

---

### Post by fiddler616 on 2009-09-06
The problem was elsewhere in the code, it works now.

---

