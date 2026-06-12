---
title: "ristretto default option on deleting pictures"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by Apurvam on 2013-03-04
I want to change it to "ok". By default ristretto selects "cancel".
How can I do this?

---

### Post by maggotbrain on 2013-03-04
It doesn't look like there is an easy way to do that without going into the source code.

Using xfconf-query, ristretto looks like it only has two easily modifiable properties: window position and last file directory

```
xfconf-query -c ristretto -l -v:
/file/current-uri               file:///home/maggotbrain/pictures
/window/navigationbar/position  left
```

---

### Post by Apurvam on 2013-03-04
Really?

---

