---
title: "Thunderbird has disappeared"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by afrancis-ozonline on 2013-10-24
Since upgrading from 13.04 to 13.10 everything has been working fine until this morning. When I went to check my emails I found that the Thunderbird Icon has just disappeared. Any ideas as to what I should do?

---

### Post by Frogs Hair on 2013-10-24
On a fresh install opening Tbird from dash was required the first time . Upgrades seem to cause problems with panel indicators some times. Try the following and logout -in. ```
sudo apt-get install --reinstall indicator-messages 
```

---

### Post by afrancis-ozonline on 2013-10-26
Looks as though I didn't need to panic. Thunderbird appeared the next time I opened Ubuntu.

---

### Post by vanadium on 2013-10-26
Ubuntu 13.10 has a problem with the indicator icons. It is mostly visible with the datetime indicator sometimes not appearing, but it affects other icons too. The problem is known and it probably won't take long anymore before this annoyance is fixed.

---

