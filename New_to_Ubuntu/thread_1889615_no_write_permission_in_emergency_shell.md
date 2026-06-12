---
title: "no write permission in emergency shell"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by JazzPotato on 2011-12-01
I have to use the emergency shell to fix an edit i made to xorg.conf, which stopped my pc from booting. However, whether i'm logged in as root or sudo'ing with my user, i cant write to anything. When trying to nano xorg.conf I get "no write permission", and when i use chown i get "changing ownership of xorg.conf: read-only file system." and the ownership isn't changed.
 Could somebody please tell me how to get write permission?

Thanks in advance

---

### Post by btindie on 2011-12-01
It sounds like your / root file system is mounted read only for some reason. You'll need to re-mount rw to be able to make changes. To do so use:

mount -o remount,rw /

---

