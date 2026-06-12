---
title: "RapidSVN crashes on copy"
date: 2009-02-21
forum: Programming Talk
---

### Post by pfwd.tech on 2009-02-21
Hi,
Each time I try an copy a branch to the trunk rapidSvn crashes out. - Just closes down.
I loaded rapidSvn via terminal to get some out out when it crashes.
This is what I got
```
<USER>@<LOCAL>:~$ rapidsvn 
rapidsvn: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
 

```

Any ideas?  Google doesn't turn up much and I cant log into launch pad to check for know bugs.

---

