---
title: "How to purge dependency after apt-get build-dep"
date: 2010-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by markoer on 2010-10-13
ok,
lets say you wana compile some application from source, firstly what you need is application source, after that you need to resolve all dependency which your application require, to resolve mostly or all dependency's you need to fire up apt-get build-dep of specific program you want to compile from source

after you get all your dependency installed and you compile your application from source, you dont need any more those dependency installed upon apt-get build-dep (your system doesn't use them at all so they only waste your hd space)

so here is litle trick to remove mostly/all dependency:
 ```
aptitude markauto $(apt-cache showsrc <program-name> | grep Build-Depends: | sed -e 's/Build-Depends:\|,\|([^)]*)//g')
```example:
i want to remove all dependency installed with apt-get build-dep for application audacious
```
aptitude markauto $(apt-cache showsrc audacious | grep Build-Depends: | sed -e 's/Build-Depends:\|,\|([^)]*)//g')
```

---

