---
title: "What version of Ubuntu did i install"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by HappyHenry on 2008-06-30
Okay I'm stupid and forgetful, lol. I know there is a command line for getting the information on the version of Ubuntu i installed.I cant seem to find it again on the forums. The reason I ask is I am not sure if its 32 or 64 bit. Thank you.

---

### Post by sayakb on 2008-06-30
At a terminal:
```
uname -m
```x86, i386, i586, i686 : 32-bit
x86_64 : 64-bit

For checking version:
```
cat /etc/lsb-release
```

---

### Post by dominiquec on 2008-06-30
uname -a

If it's 32-bit, it should say i686.

---

### Post by unutbu on 2008-06-30
These may help you too:
```
cat /etc/lsb-release
uname -a
```

Edit: Oops. Me slow...

---

### Post by HappyHenry on 2008-06-30
Thank you All! Perfect advice, as usual!:D
uname -m
x86-_64
Bingo, now I know what I should have known:roll:

---

