---
title: "warlock 2 frontend"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by bruvidef on 2012-07-26
fairly new to linux and could use some help. i am trying to install the file warlock-0.4. when i run ./configure i receive the following. 

                                  checking for gtk+-2.0 >= 2.4 gthread-2.0 libglade-2.0 gconf-2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package gthread-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gthread-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gthread-2.0' found Package libglade-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libglade-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libglade-2.0' found Package gconf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gconf-2.0' found 
 configure: error: Library requirements (gtk+-2.0 >= 2.4 gthread-2.0 libglade-2.0 gconf-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

---

### Post by levlaz on 2012-08-01
I think you need to install the dev package in order to use this. 

```
 sudo apt-get install libgtk2.0-dev 
```

---

### Post by stproctor on 2012-08-11
Warlock 0.4 is quite old. Warlock 2 is a re-write to support the new protocol used in DR2/GS4. It has received much more testing and is still being supported. I say this as the author of Warlock 0.4 and part of Warlock 2. If you need more support you can find a few of us on IRC in #warlock on irc.freenode.net.

Regards,
Sean

---

