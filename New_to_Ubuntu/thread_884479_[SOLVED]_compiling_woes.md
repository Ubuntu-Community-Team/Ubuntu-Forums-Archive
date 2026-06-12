---
title: "[SOLVED] compiling woes????"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-09
ive tried to compile some packadgeswith kompile,and i always get this;
configure: error: C compiler cannot create executables See `config.log' for more details. 
Error during sources configuration. Installation aborted!
is there a fix for this??
rick

---

### Post by eightmillion on 2008-08-09
What's config.log say?

---

### Post by RiceMonster on 2008-08-09
Have you installed build-essentials? You can't compile without it.

```
sudo apt-get install build-essentials
```

---

### Post by Crafty Kisses on 2008-08-09
Great read and documentation right here < [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

---

