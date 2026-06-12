---
title: "Firefox 3 in hardy is rotten...how to I rollback to 2.0.0.14"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by al7kz on 2008-05-03
Text widens out of sight on zoom. How can I rollback to 2.0.0.14? Thanks.

---

### Post by PmDematagoda on 2008-05-03
First remove Firefox 3 with:-
```
sudo apt-get remove --purge firefox-3.0
```
then install Firefox 2 with:-
```
sudo apt-get install firefox-2
```

That should do it.

---

### Post by al7kz on 2008-05-03
Thanks for the fast reply PmDematagoda, that worked great. I hope they fix that.

Merci beaucoup mon ami

---

### Post by SunnyRabbiera on 2008-05-03
yeh firefox 3 is still a beta, though I understand why it was put there by default.

---

