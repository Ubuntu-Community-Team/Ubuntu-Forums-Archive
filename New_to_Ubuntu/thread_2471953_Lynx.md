---
title: "Lynx"
date: 2022-02-14
forum: New to Ubuntu
---

### Post by dantsi on 2022-02-14
Hello,

I'm sorry, I speak a little English.

My new VPS:

```
hostnamectlVirtualization: openvz
Operating System: Ubuntu 20.04.3 LTS
Kernel: Linux 5.4.0
Architecture: x86-64
```

I would like save the tezfiles.com JavaScript-based website cookies. How to?

I tried Lynx:

```
lynx -cfg=/tmp/lynxcfg-cookies -accept_all_cookies -cookie_save_file=/tmp/cookies https://tezfiles.com
```
Problem (JavaScript):

[IMG]https://i.imgur.com/cjqkVMC.png[/IMG]

What I need:

[IMG]https://i.imgur.com/EX3pwGz.png[/IMG]

---

### Post by MAFoElffen on 2022-02-15
If while in 'lynx', you press <Cntrl><K>... It will display a list of stored cookies from what 'lynx' calls their 'cookie jar'. If you want to see those cookies externally from where they are stored, look at ~/.lynx_cookies

---

