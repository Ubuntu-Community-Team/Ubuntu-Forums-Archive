---
title: "unable to install skype on netbook"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by esse2k on 2012-11-24
Trying to install Skype on my asus netbook from the synaptic package manager, I run into some error and get this message:

E: /var/cache/apt/archives/libasound2_1.0.25-1ubuntu10.1_i386.deb: './usr/share/alsa/alsa.conf' is different from the same file on the system


Does anyone know the possible cause?
Thanks!

---

### Post by freedomAboveAll on 2012-11-24
Hi,

Perhaps following this similar bug [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/1033193](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/1033193)

you could:

> I renamed the file /usr/share/alsa/alsa.conf to /usr/share/alsa/alsa.conf.old and forced install.

could try:
```
sudo mv /usr/share/alsa/alsa.conf /usr/share/alsa/alsa.conf.old
```

and then try install..

---

### Post by Rex Bouwense on 2012-11-25
Try looking here:
[https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)

---

