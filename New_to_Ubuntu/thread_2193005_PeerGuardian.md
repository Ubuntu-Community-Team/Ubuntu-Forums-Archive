---
title: "PeerGuardian"
date: 2013-12-10
forum: New to Ubuntu
---

### Post by Squeeeee on 2013-12-10
How do I uninstall PeerGuardian from Ubuntu?

---

### Post by newb85 on 2013-12-10
It's not in the Ubuntu repos, so the best way is probably using the PGL (PeerGuardian Linux) PPA.  In a terminal,
```
sudo add-apt-repository ppa:jre-phoenix/ppa
sudo apt-get update
sudo apt-get install pgl
```

Alternatively, there is an experimental PPA for untested updates, but given that you had to ask, it's probably not for you.

---

### Post by jre on 2014-01-21
To install it would be

```
sudo add-apt-repository ppa:jre-phoenix/ppa
sudo apt-get update
sudo apt-get install pgld pglcmd pglgui
```

To uninstall

```
sudo apt-get purge pgld pglcmd pglgui
```

---

### Post by newb85 on 2014-01-21
Thanks for the correction. As a non-pgl user, I didn't know what specific packages needed to be installed.

---

