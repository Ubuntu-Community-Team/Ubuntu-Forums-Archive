---
title: "Just upgraded to heron on Laptop Firefox didnt update"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by mastergunner on 2008-04-29
Guys I just upgraded and everything is working but firefox didnt upgrade. It is still the old one. I uninstalled it and went to reinstall and the same old version came up. Any ideas. Thanks.

---

### Post by pedro_orange on 2008-04-29
Find the package you want:

```
apt-cache search firefox
```

When I do it I have firefox-3.0

Perhaps you need to update your apt-get list:

```
sudo apt-get update
```

Then you just do the standard install:

```
sudo apt-get install package-name
```

---

