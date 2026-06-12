---
title: "Change Main User Name?"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by mapes12 on 2013-09-11
I've done a fresh insall of 12.04. During the installation I entered a username for the primary account. How can I now change this including the main users /home name? There used to be something called Login Manager but I can't find it in this release.

Screenshot attached.

---

### Post by scbingham on 2013-09-11
I guess you could edit /etc/passwd & /etc/shadow & then rename the user's home directory.

First I'd create a new user with admin privileges, in case things go wrong. Also backup the 2 files & the user's home directory, beforehand.

Hope this helps. good luck.

---

### Post by grahammechanical on 2013-09-11
Have you tried clicking on the panel with the name in it. But as already suggested, first create a user with administration privileges then you will still be able to make administrative changes.

Regards.

---

