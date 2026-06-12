---
title: "no YouTube audio"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-07-05
I can't get any audio on YouTube

Any suggestions how I can solve this?

---

### Post by Captain panda on 2008-07-05
Making sure that any media players you have are all closed sometimes helps when you tube doesn't work for me.

---

### Post by neurostu on 2008-07-05
Try installing libflashsupport:
```

sudo apt-get install libflashsupport

```

---

### Post by wolfen69 on 2008-07-05
try this:
```
wget http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb

```
then
```
sudo dpkg -i libflashsupport_1.0~2219-1_i386.deb

```
restart firefox

---

### Post by Rustbeard on 2008-07-05
thanks I was just about to post asking for help on this

---

