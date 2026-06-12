---
title: "gcc-4.6: not found (hardened-cc could not find target)"
date: 2013-01-30
forum: Programming Talk
---

### Post by Pobednik92 on 2013-01-30
Evening my friends. I have a question for you, because I know that you can help me. I got an error when I want to compile (or something like that) with this command:

gcc-4.2 -O -fbuiltin -fomit-frame-pointer -fPIC -shared -o ca.so ca.c -ldl


In terminal:

root@Collateral:~/Desktop/kaffeine-sc-plugin-0.4.0# gcc-4.6 -O -fbuiltin -fomit-frame-pointer -fPIC -shared -o ca.so ca.c -ldl
/usr/bin/gcc-4.6: not found (hardened-cc could not find target)
If I just type "gcc" and not "gcc-4.6", gives me another error:

root@Collateral:~/Desktop/kaffeine-sc-plugin-0.4.0# gcc -O -fbuiltin -fomit-frame-pointer -fPIC -shared -o ca.so ca.c -ldl
ca.c:107:1: error: expected ‘,’ or ‘;’ before ‘{’ token
ca.c: In function ‘cactl’:
ca.c:276:9: warning: format ‘%d’ expects a matching ‘int’ argument [-Wformat]
ca.c:289:13: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]
root@Collateral:~/Desktop/kaffeine-sc-plugin-0.4.0# 


Someone posted that he successed to compile this with gcc-4.6, so I installed hardening-wrapper with command:

apt-get install hardening-wrapper


I don't know what could be the problem. I am using fresh installed Ubuntu 12.10

So if anyone can help me, I would appreciate it :)

---

### Post by steeldriver on 2013-01-30
You already got help about fixing that error in your previous thread

[http://ubuntuforums.org/showthread.php?t=2108887](http://ubuntuforums.org/showthread.php?t=2108887)

Regardless, if your intent really is 

> **Pobednik92 said:**
> [ ... ] to watch the encrypted channels with my Skystar 2 PCI-e card  without paying to watch these channels

then we won't be able to help you, here - OTOH if you really want to know about how to install / run multiple versions of gcc on the same system then I'm sure folks will help you out if you post a suitable new thread

---

