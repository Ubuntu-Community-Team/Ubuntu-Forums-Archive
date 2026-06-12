---
title: "How to compile using make?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by lavadisco on 2008-08-16
Was attempting these instructions:

[http://ferama.netsons.org/wp/index.php/2007/11/14/guitar-rig-on-ubuntu-gutsy-howto/](http://ferama.netsons.org/wp/index.php/2007/11/14/guitar-rig-on-ubuntu-gutsy-howto/)

And right in the middle of it it says to "compile using make". How do I do that?

---

### Post by Ryadt on 2008-08-16
```
sudo make
```

---

### Post by lavadisco on 2008-08-16
Thanks!

---

### Post by Ryadt on 2008-08-16
your welcome.. can u plz mark the thread as solved plz ;)

---

### Post by nicedude on 2008-08-16
Also should be noted that when copiling anything, in the source directory there should be a README & a INSTALL text files so read them as they will tell you how to install whatever it is you are trying to install :-)

---

### Post by Separ on 2008-08-16
It should be said that you run "make" as user and "sudo make install" is running as root, don't do "sudo make".

---

