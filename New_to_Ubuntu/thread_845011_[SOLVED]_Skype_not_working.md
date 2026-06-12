---
title: "[SOLVED] Skype not working"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-06-30
I downloaded the latest Skype as my version stopped working for some reason last week....I cannot get it to work now, despite removing all of the original with Synaptic.

I get this error message.

/usr/bin/skype: symbol lookup error: /usr/lib/libQtNetwork.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

---

### Post by quantumstitch on 2008-07-06
did you try:
```

sudo apt-get remove --purge skype

```

Did you use the .deb package from skype.com or from the repo (medibuntu)? After purging, try installing using the repo.

---

### Post by dunbrokin on 2008-07-06
> **quantumstitch said:**
> did you try:
```

sudo apt-get remove --purge skype

```

Did you use the .deb package from skype.com or from the repo (medibuntu)? After purging, try installing using the repo.

Yep, tried that....it now appears in my Applications>Internet....but when I click on it nothing happens...

---

### Post by quantumstitch on 2008-07-06
> **dunbrokin said:**
> Yep, tried that....it now appears in my Applications>Internet....but when I click on it nothing happens...

Apparently, this is a common problem. Check out [https://help.ubuntu.com/community/Skype#Skype%20fails%20to%20start](https://help.ubuntu.com/community/Skype#Skype%20fails%20to%20start)

Best,
stitch

---

### Post by dunbrokin on 2008-07-06
> **quantumstitch said:**
> Apparently, this is a common problem. Check out [https://help.ubuntu.com/community/Skype#Skype%20fails%20to%20start](https://help.ubuntu.com/community/Skype#Skype%20fails%20to%20start)

Best,
stitch

Thanks for that pointer..however, I don't have the nessus line - so no need to hash it out as below....

#/opt/nessus/lib

---

