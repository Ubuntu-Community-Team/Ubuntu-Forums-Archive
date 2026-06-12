---
title: "sound card problem"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by b-do on 2008-05-25
my sound card (realtek high definition) is not working on kobuntu please help!!

---

### Post by sayakb on 2008-05-25
Install the following package:
```
sudo apt-get install linux-backports-modules
```

---

### Post by b-do on 2008-05-25
nothing changed even after i restarted

---

### Post by sayakb on 2008-05-25
```
alsamixer
```
Change the slider levels and see whether you can hear sound of not.

---

