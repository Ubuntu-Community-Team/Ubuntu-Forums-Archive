---
title: "Trouble running Netbeans 8 on ubuntu 12.04,java version &quot;1.7.0_51&quot;"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by zendo108 on 2014-02-18
Hi,
I just installed Netbeans 8 in ubuntu 12.04 with  
java version "1.7.0_51"  
OpenJDK Runtime Environment (IcedTea 2.4.4) (7u51-2.4.4-0ubuntu0.12.04.2) 
OpenJDK Client VM (build 24.45-b08, mixed mode, sharing)
It run fine after installation but after that nothing.
When I run: netbeans,the terminal spits back =>The program 'netbeans' is currently not installed.  You can install it by typing:sudo apt-get install netbeans.
 Ok the first time i followed those instructions and it installed 7.0.1
Then, if i go to /usr/local/netbeans-8.0beta/bin and run: sh netbeans, I get 
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  72 (X_PutImage)
  Serial number of failed request:  325
  Current serial number in output stream:  332
but if I run: sh netbeans --nosplash, I getto start but the terminal gets locked till i quit netbeans.
Any thoughts??

Thx

---

### Post by QIII on 2014-02-18
Hello!

Try

```
/usr/local/netbeans-8.whatever/bin/netbeans
```

(or wherever you installed it to) if you installed it from Oracle's site.

---

