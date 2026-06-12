---
title: "Terminal"
date: 2014-11-18
forum: New to Ubuntu
---

### Post by flaymond on 2014-11-18
sudo: unable to resolve host Inter76% - This statement always appear when I tried to run sudo commands....help! Its happen when Im changed the hostname!

---

### Post by steeldriver on 2014-11-18
You will need to fix your hostname in order for sudo to work. Did you use the hostname command, or edit the /etc/hostname file directly?

In the absence of a working sudo command, you may be able to reverse you changes using pkexec, otherwise you will need to boot into recovery mode and do it from a root shell.

Note that the /etc/hostname file and the /etc/hosts file need to be consistent - you can't change the hostname in one without updating the other

---

### Post by flaymond on 2014-11-19
I don't understand sir, can you show me step by step or post a link to guide me? If you willingly to do so..


* Im changed it using Network app....you know....DNS hostname....

---

