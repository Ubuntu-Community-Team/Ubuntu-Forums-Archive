---
title: "[SOLVED] apt-get dist-upgrade failed..."
date: 2008-09-03
forum: New to Ubuntu
---

### Post by paul_mcl on 2008-09-03
...And now I'm left with no apt-get. It said something about "dependencies" and to try 'apt-get -f install'. But it hadn't helped me. Same error. "openssh-server depends on openssh-client which is version blah-blah". What to do now?

---

### Post by ibuclaw on 2008-09-03
What repositories do you have enabled?

Have you added any third party repos?

Can you post the output of this command line task?
```
grep -v "^#" /etc/apt/sources.list
```

Regards
Iain



Regards
Iain

---

### Post by paul_mcl on 2008-09-03
SOLVED by myself!
just 'apt-get remove openssh-server', 20 mins of starnge output... and apt-getting works again.

---

