---
title: "install firefox 3 in gutsy???"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by holasoyneto on 2008-07-24
Hey, im still in gutsy and id like to install firefox 3 on it.
is it posible?
and if it is, can somebody tell me how ?

thank you =D

---

### Post by rockstarrem on 2008-07-24
This should work:

```

sudo apt-get install firefox-3.0

```

Let us know how you make out!

---

### Post by avtolle on 2008-07-24
[http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox) should help you. I believe, but am not sure, that FF3 Beta 5 is the only version available in the repositories for 7.10, and then from the backports. Good luck regardless of how you proceed.

---

### Post by halitech on 2008-07-24
the info on psychocats site works fine, I used it a few weeks ago and I have had no problems at all.

only thing I would suggest is go into Synaptic and lock the current version of firefox so you don't get any update notifications for FF2

---

### Post by ptn107 on 2008-07-24
In Gutsy click System -> Administration -> Software Sources.  Make sure on the Updates tab that Pre-released updates is selected (this enables gutsy-backports).  Pop open a terminal and then do:
```
sudo apt-get update && sudo apt-get install firefox-3.0
```

---

