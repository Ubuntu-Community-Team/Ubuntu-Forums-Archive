---
title: "Unreal install problems"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by bwbritt86 on 2014-01-06
So I'm trying to install UnrealIRCd-3.2.10.2 and right after answering the last question: "Would you like to pass any custom parameters to configure?" I get this.

```
.configur --with--showlistmodes --with-listen=5 --with-dpath=/IRC/Unreal3.2.10.
2 --with-spath=IRC/Unreal3.10.2/src/ircd --with-nick-history=2000 --with-send
q=3000000 --with-bufferpool=18 --with-permissions=0600 --with-fd-setsize=1024 --
enable-dynamic-linking
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure error: in '/IRC/Unreal3.2.10.2':
configure: error: no acceptable C compiler found in $PATH
```

Now I know that GCC comes with lubuntu-13.10 and already did a search to make sure it was there.
```
sudo find / --name gcc
usr/lib/gcc
/usr/share/bash-completion/completions/gcc
```
 Does anyone know if this is a real problem or just a stupid newbie mistake?  Help would be much appreciated.

Unreal is in directory path: /IRC/Unreal3.2.10.2

---

### Post by monkeybrain20122 on 2014-01-06
Just to make sure you have it why not try to install it again, doesn't hurt if it is already installed.
```
sudo apt-get install gcc
```

---

### Post by bwbritt86 on 2014-01-06
Yep, that did the trick. GCC needed 11 new files and needed to update 26 old ones. Thank you...

---

### Post by mörgæs on 2014-01-06
Good, please mark the thread 'solved'.

---

