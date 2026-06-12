---
title: "desktop background-advanced help"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-10-30
i started having this problem when i was testing ubuntu 13.10. after i login all i get is a grey screen;however, after i open my home folder the desktop background loads. even if i change my background the same error repeats. any ideas? tks

---

### Post by rburkartjo on 2013-11-01
just a bump this is the weekend usually more users on. again tks there has to be an easy fix

---

### Post by Toz on 2013-11-01
Are you running xfdesktop as the desktop manager?
```
ps -ef | grep xfwm | grep -v grep
```
...if not, what is managing the desktop (nautilus, etc)?

Are you using thunar as your file manager? If not, which one (nautilus, pcmanfm, etc)?

Have you tried clearing your sessions cache (Settings Manager -> Session and Startup -> Session tab -> "Clear saved sessions")?

Are there any error messages in your ~/.xsession-errors log file?

---

