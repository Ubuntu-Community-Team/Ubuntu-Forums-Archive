---
title: "CPU Frequency"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by D|F on 2008-05-21
I have problem when i open desktop after login its written
CPU Frequency Scaling Unsupport
you will not be able to modify the frequency of your machine.
Your machine may be misconfigured or not have hardware support for CPU frequency scaling.
And i when i open System>Preferences>Appearance its hanging.

theres someone can helep me ?...

---

### Post by NightwishFan on 2008-05-21
What is the model of your processor. We can set it up manually if it supports it. In terminal:
```
cat /proc/cpuinfo | grep "model name"
```

---

