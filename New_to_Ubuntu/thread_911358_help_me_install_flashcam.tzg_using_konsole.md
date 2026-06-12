---
title: "help me install flashcam.tzg using konsole"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by _tragic_ on 2008-09-05
How do i install a tgz file that is on my desktop using konsole? 

Specific app is Flashcam

---

### Post by tangibleorange on 2008-09-05
> **_tragic_ said:**
> How do i install a tgz file that is on my desktop using konsole? 

Specific app is Flashcam

these are the instructions from their website. I assume you are using version 1.1:

```
sudo apt-get install build-essential linux-headers-`uname -r`
cd Desktop
tar xf flashcam-1.1.tgz
cd flashcam-1.1
make
sudo make install
```

keep in mind that this will just install it. you may need to play around with kernel modules as described on their website.

---

