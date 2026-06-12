---
title: "Failed backups"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by Shoalster on 2013-05-02
No backup since upgrade to 13.04.  I get:  "Giving up on request after 5 attempts, last status 400 Bad Request"

---

### Post by rburkartjo on 2013-05-02
what program are you using to backup?

---

### Post by Shoalster on 2013-05-02
Disregard.  I just uninstalled it.   Thank you.

---

### Post by pmunly on 2013-05-10
I'm having the same problem, using the standard Ubuntu backup program (deja-dup) with Ubuntu One as the backup server.  Here's the error I'm getting: 

Giving up on request after 5 attempts, last status 400 Bad Request

Started happening after upgrade to 13.04.  Any ideas?

Thanks!

---

### Post by kalikiana on 2013-05-23
This a bug in Duplicity. Be sure to enable "proposed updates" in the software sources settings and the next update should include a fix.

See [https://bugs.launchpad.net/ubuntu/+source/duplicity/+bug/1161599](https://bugs.launchpad.net/ubuntu/+source/duplicity/+bug/1161599)

---

