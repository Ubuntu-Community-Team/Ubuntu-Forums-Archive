---
title: "Installed 32 or 64?"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by gurrunaki on 2012-05-10
Hi, I would like to know if is any command or any way to find out if my version of ubuntu 11.10 is 32 or 64 I tried in the terminal with uname -a    and cat /etc/lsb-release  and they give the info about my distro but not if is version 32 or 64

Thanks in advance!!!

---

### Post by PaulW2U on 2012-05-10
```
uname -a
```

is the command you need, which I see you have already tried.

Look for i386 or amd64 at the end of the ouput line. i386 = 32 bit, amd64 = 64 bit.

---

### Post by gurrunaki on 2012-05-10
Thanks a lot Paul they say i386 so, I have de 32 one, I didn't know this :p

---

