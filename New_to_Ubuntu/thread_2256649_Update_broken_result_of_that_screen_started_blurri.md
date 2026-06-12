---
title: "Update broken result of that screen started blurring (Ubuntu 14.04)"
date: 2014-12-13
forum: New to Ubuntu
---

### Post by sivakumar-sakam on 2014-12-13
Tried to install updates through Terminal in between my Laptop was got shutdown suddenly after starts my screen got blurring please see the attached videos

OS : Ubuntu 14.04


[https://www.youtube.com/watch?v=OBfOnPyqRBM](https://www.youtube.com/watch?v=OBfOnPyqRBM)

[https://www.youtube.com/watch?v=K0ea6bLWuiI](https://www.youtube.com/watch?v=K0ea6bLWuiI)

---

### Post by cariboo on 2014-12-14
Press Ctrl-F1 and login, once at the prompt type:

```
sudo apt-get update
```

then

```
apt-get -f install
```

---

### Post by sivakumar-sakam on 2014-12-16
Thank you so much .. it worked

---

