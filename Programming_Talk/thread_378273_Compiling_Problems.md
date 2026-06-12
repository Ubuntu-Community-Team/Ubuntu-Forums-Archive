---
title: "Compiling Problems"
date: 2007-03-07
forum: Programming Talk
---

### Post by Jsgrabo on 2007-03-07
I just installed Ubuntu on my laptop and im trying to compile a few programs. When I attempt to use the "make" command all I get is this:

```

bash: make: command not found
```

Ive compiled many programs on linux before and I have never had this problem. Any suggestions?

Thanks

---

### Post by Mr. C. on 2007-03-07
Install appropriate development tools.  Use Synaptec if you wish - look under the development category.

MrC

---

### Post by 23meg on 2007-03-07
Install the package *build-essential*, which contains *make*, among the other things you need to compile.

```
sudo apt-get install build-essential
```

---

