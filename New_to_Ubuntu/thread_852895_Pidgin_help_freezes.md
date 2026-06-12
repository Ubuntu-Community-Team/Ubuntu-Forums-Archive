---
title: "Pidgin help freezes"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by windows hater on 2008-07-08
I use Pidgin and sign on with Yahoo, MSN, and AIM. When I'm talking with people on MSN and Yahoo it's fine, but when someone IM's me on AIM, it kicks me off. What's wrong with it?? Thank you anyone.

---

### Post by oliviacond on 2008-07-08
download the latest version of pidgin.
[http://www.getdeb.net/release.php?id=2883](http://www.getdeb.net/release.php?id=2883)

then, remove the current version (required)
```
sudo apt-get remove pidgin pidgin-data libpurple0
```

install the .deb
install libpurple0 1st, then pigin-data, and lastly pigin

---

