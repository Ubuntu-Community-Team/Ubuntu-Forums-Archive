---
title: "ubuntu 22.04 the screen freezes"
date: 2022-11-06
forum: New to Ubuntu
---

### Post by emilio-gnome on 2022-11-06
Hello everyone, I have ubuntu 22.04 install on laptop  Asus A55A , i5 3210m, and 8 gb ram, the screen freezes while i am watching somes videos and the only way to solve it is shutting down the system. So what can I do to resolve that issue?

---

### Post by vmpx on 2022-11-26
I use in GRUB "nomodeset quiet splash" (Ubuntu 18.04 and 20.04)

---

### Post by arieleoar on 2022-12-01
Hi!

Looks like a little more info is needed in order to know what is causing the crash.
A good way to start could be reproducing again the error (watch a video until it freezes the system), mark the time when the freeze happened and then after reboot go to /var/log/kern.log (using a text editor or directly from the files browser) and check what happened at that time in the logs.
If you got that info please paste it here, an we will hepl you check and debug the issue.

Regards!

---

