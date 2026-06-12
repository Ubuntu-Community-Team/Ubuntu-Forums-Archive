---
title: "Testing bionic. Issue arises with Locales."
date: 2018-05-17
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2018-05-17
Getting this when trying to build my ltsp chroot. First code box is the tail of the build client process where it stops, and below is result of locale command. I've never seen C.UTF-8 so I'm assuming some sort of bug. How to work around it?

```
Error: 'C.UTF-8' is not a supported language or locale
error: LTSP client installation ended abnormally
```


```
root@ltsptest:/opt/ltsp# locale
LANG=C.UTF-8
LANGUAGE=
LC_CTYPE="C.UTF-8"
LC_NUMERIC="C.UTF-8"
LC_TIME="C.UTF-8"
LC_COLLATE="C.UTF-8"
LC_MONETARY="C.UTF-8"
LC_MESSAGES="C.UTF-8"
LC_PAPER="C.UTF-8"
LC_NAME="C.UTF-8"
LC_ADDRESS="C.UTF-8"
LC_TELEPHONE="C.UTF-8"
LC_MEASUREMENT="C.UTF-8"
LC_IDENTIFICATION="C.UTF-8"
LC_ALL=
```

```
root@ltsptest:/etc/default# cat locale 
LANG=en_US.UTF-8
```

---

### Post by dino99 on 2018-05-19
what does 'sudo dpkg-reconfigure locales' ?

---

### Post by Tadaen_Sylvermane on 2018-05-20
```
#!/bin/bash
# tadaen sylvermane | jason gibson
# configure locales for ubuntu bionic ltsp chroot creation


for var in LC_ALL= LANG= ; do
        export "$var"en_US.UTF-8
done
ltsp-build-client --chroot "$1"
```

I wrote this wrapper and got it to work. dpkg-reconfigure showed en.US-UTF8. Still question in my mind as to why. However it doesn't matter much. Once I got it to work right I found that the bionic ltsp version has the same problem as the debian stretch ltsp version so I couldn't upgrade regardless. Both seem to ignore /var/lib/tftpboot/ltsp/$chroot/lts.conf. For the time being my deployment relies on LTSP functioning properly so it's a bust.

At least unless I can find a guide to setup pxe boot clients minus ltsp. Ltsp just makes it easier.

---

### Post by rr83019 on 2018-05-25
Can you please explain what you did there?

---

