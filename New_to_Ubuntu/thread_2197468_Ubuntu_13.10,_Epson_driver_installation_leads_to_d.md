---
title: "Ubuntu 13.10, Epson driver installation leads to dpkg problem"
date: 2014-01-03
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2014-01-03
See the attached errors for details.

I was installing the printer drivers from the EPSON page with GDebi-GTK for my EPSON Stylus NX230, when the install stopped because of a dependency problem.

```
apt-get -f install
dpkg --configure -a
```

All yield to the same error.

Any help appreciated.

Logs:

[ATTACH]249179[/ATTACH]
[ATTACH]249180[/ATTACH]

-- Jonathan

---

### Post by Jonathan Precise on 2014-01-06
Fixed! I don't know how, but the next time the computer started, the dependency issue was fixed!

---

