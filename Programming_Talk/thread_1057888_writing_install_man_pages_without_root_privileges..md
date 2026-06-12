---
title: "writing /install man pages without root privileges."
date: 2009-02-02
forum: Programming Talk
---

### Post by monkeyking on 2009-02-02
Hey,
I'm in the process of writing documentation to my program,

Is it possible for the end user to install the man pages on their userlevel account. In case they don't have sudo privileges.

thanks in advance.

---

### Post by wmcbrine on 2009-02-04
There is no standard location for man pages outside of the usual system hierarchy. However, like other Unix commands, this can be configured, either via file or environment variable -- see "man manpath". More directly, you can give the man command the name and path of the man page file instead of a command name: "man ./yourprog.1". (I'm not sure how standard that feature is, but it's always worked for me in Linux distros.)

---

### Post by monkeyking on 2009-02-04
Thanks very informative.

Seems quite as complicated as I had feared.

thanks again

---

