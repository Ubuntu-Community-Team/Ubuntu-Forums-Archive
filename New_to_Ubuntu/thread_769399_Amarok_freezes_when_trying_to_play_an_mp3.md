---
title: "Amarok freezes when trying to play an mp3"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by akiratheoni on 2008-04-26
I've installed Amarok as well as amarok-xine. I've also installed the ubuntu-restricted-extras as well as the kubuntu-restricted-extras and Amarok freezes when I try to play an mp3.

Help? 

Thanks.

---

### Post by caffienefree on 2008-04-26
What version of ubuntu are you using?

---

### Post by akiratheoni on 2008-04-26
Oh oops lol.

Fresh install of Ubuntu 8.04. Amarok is the same version in the repos.

---

### Post by akiratheoni on 2008-04-27
Bump.

Amarok worked last night but now it freezes up again =/

EDIT: It freezes for ALL music files, not just mp3.

---

### Post by akiratheoni on 2008-04-27
Double post... weird.

---

### Post by SuperSon!c on 2008-04-27
i'd say do a complete removal then reinstall.  i'm using amarok with a fresh install of 8.04 and haven't had a single issue. so try:

```
apt-get remove amarok
```

then perhaps:

```
apt-get --purge remove amarok
``` 

to clean up any residial config files.  not sure if the last one is needed though.

---

### Post by akiratheoni on 2008-04-27
Weird. Amarok will play music then when I reboot it freezes up and refuses to play mp3s. Rebooting the computer again will make the music play again. But then if I reboot it stops working...

---

### Post by SuperSon!c on 2008-04-27
like i said, try uninstalling.

---

