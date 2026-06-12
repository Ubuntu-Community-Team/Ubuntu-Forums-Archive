---
title: "steam unable to launch (ubuntu 14.04)"
date: 2015-04-07
forum: New to Ubuntu
---

### Post by philip-wrtzner on 2015-04-07
I installed steam(steam-launcher) from USC successfully. however when trying to launch the app i get the following message

'You are missing the following 32-bit libraries, and Steam may not run:
libc.so.6'

wasn't able to solve the problem by installing and updating the i386 architectures.

solved with:

sudo apt-get install steam -y

---

### Post by mc4man on 2015-04-07
you could start by installing this, open a terminal (ctrl+alt+t) copy & paste in, press enter.
```
sudo apt-get install libc6:i386
```

---

