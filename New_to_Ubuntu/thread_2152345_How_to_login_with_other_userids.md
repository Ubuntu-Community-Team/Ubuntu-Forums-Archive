---
title: "How to login with other userids?"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by UserJB on 2013-06-07
My ubuntu system has several accounts each with a different userid  But when I reboot and I'm at the login screen, it doesn't allow me to choose which userid I can login as. It only gives me one choice: the oirginal userid I created when I installed ubuntu.  So, how can I login as the other userids?

SOLVED: The problem was the UID and GID was less than 1000, and Ubuntu by default requires than to be 1000 or higher.

---

