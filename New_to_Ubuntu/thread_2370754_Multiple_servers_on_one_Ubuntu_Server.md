---
title: "Multiple servers on one Ubuntu Server?"
date: 2017-09-06
forum: New to Ubuntu
---

### Post by shaffle1 on 2017-09-06
I saw Ubuntu stuff a long time ago and i want to make my own, so my question is can you install multiple gaming servers on one ubuntu server for example cs:go and team fortress 2, + can you tell what i need to know about ubuntu, what to beware of and stuff. And my last question what is better to use ubuntu desktop or ubuntu like console thing? :D

(Sorry for my English because im from Russia lol :D) 

Thx

---

### Post by HermanAB on 2017-09-07
Yesh...

The problem with multiple complicated services from multiple vendors, is that the library and kernel requirements may clash.

There are various workarounds for that: Docker, VMware, KMS, Qemu, Virtualbox...

The best solution depends on your hardware.

---

### Post by mastablasta on 2017-09-07
yes, you can. 

but to run them at the same time you need virtual servers.

beware - linux is not windows.

desktop come swith a GUI like "normal" windows do. the GUI eats additional system resources which are very important if you are having multimple servers running a the same time using virtualization.

---

### Post by Tadaen_Sylvermane on 2017-09-07
lxd containers are your friend here.

---

