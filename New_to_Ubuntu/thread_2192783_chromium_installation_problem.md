---
title: "chromium installation problem"
date: 2013-12-09
forum: New to Ubuntu
---

### Post by george11 on 2013-12-09
Chromium stopped working, so I uninstalled then reinstalled it from the software centre in Ubuntu 12.04 LTS, where it is shown as 'installed'.  The lcon in the launcher says 'waiting to install'.  What else do I need to do, please?

---

### Post by newb85 on 2013-12-09
I would try the following in a terminal.
```
sudo apt-get update
sudo apt-get -f install
```

---

### Post by george11 on 2013-12-09
Thanks for reply.  Tried the suggestion, but still no joy.

george11

---

### Post by walterorlin on 2013-12-10
Did the terminal ouput anything?

---

### Post by codenine75a on 2013-12-10
sudo apt-get remove chromium
sudo apt-get install chromium
or maybe build it too
sudo apt-get build-dep chromium
sudo apt-get source chromium --compile

that is if all the sources are available.

---

### Post by newb85 on 2013-12-10
I think the package is chromium-browser. 

What is the output of

```
 sudo dpkg --status chromium-browser 
```

---

