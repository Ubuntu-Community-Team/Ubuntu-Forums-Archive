---
title: "Can't update - how do I get rid of these or update them???"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by bryantarrington on 2014-05-08
I have 63 updates, but they will not download. It gets hung up. When I click install, it ask me to authenticate. When I do a message below (1) pops up.  There is all so something called python.

1. Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

2.  Changes for the versions:
Installed version: 1.5.3-0ubuntu8
Available version: 1.5.3-0ubuntu8.2

Version 1.5.3-0ubuntu8.2:

 * SECURITY UPDATE: cross-site scripting issue in web interface
   - debian/patches/CVE-2014-2856.patch: filter bad characters from the
     URL in scheduler/client.c.
   - CVE-2014-2856
 * This package does _not_ contain the changes from 1.5.3-0ubuntu8.1 in
   precise-proposed.

---

### Post by su:bhatta on 2014-05-08
Which version of Ubuntu are you using?
 Is it a fresh install or a upgrade?

Please provide your sources.list
Type the following command in a terminal and copy paste the result within Code tags here (denoted by # in Advanced Reply option)

```
cat /etc/apt/sources.list
```

Did you install any softwares through PPA ?
If possible give a screenshot of the dialogue that opens after you give the password for authentication or more details about what that dialogue box exactly says.

---

