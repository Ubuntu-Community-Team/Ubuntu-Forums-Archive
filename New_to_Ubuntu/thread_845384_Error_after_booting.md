---
title: "Error after booting"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by honkey on 2008-06-30
After I boot ubuntu there is a notify on the top of the screen:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

What a **** is this?

---

### Post by markjensen on 2008-06-30
Dunno.

Is that the exact text?   If so, it sounds like this bug:
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/130937](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/130937)
Possibly related to drive file indexing.  Do you use Evolution for email?  (it sounds like that might be contributing to the error display)

From reading the bugzilla entry, it seems like an annoyance error, and not indicating anything fatally wrong.

---

