---
title: "Can't install Unity due to unmet dependencies"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2011-09-02
I did a dist-upgrade that apparently removed Unity (oops!).
Trying to manually install Unity get me this:


```
The following packages have unmet dependencies:
 unity : Depends: compiz but it is not going to be installed
         Depends: compiz-core-abiversion-20110703
         Depends: compiz-plugins-main-default but it is not going to be installed
         Recommends: indicator-power but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

The package compiz-core-abiversion doesn't even exist as far as I can tell.

EDIT: Forgot I had the compiz-testing PPA active. Pretty amazing how I always manage to stumble upon a solution (which eluded me for the past 2 days) mere minutes after requesting help.

---

### Post by coffeecat on 2011-09-02
> **zekopeko said:**
> 
The package compiz-core-abiversion doesn't even exist as far as I can tell.

Agreed - it's certainly not listed in Synaptic. However, I've just done a dist-upgrade which upgraded a broken Unity and has allowed me to log into my Unity desktop again. Screenshot of Unity dependencies attached which includes compiz-core-abiversion. Curious. :-k

---

### Post by ventrical on 2011-09-02
I get that too :)

---

### Post by entonjackson on 2011-09-12
I have the same problem. With the difference, that i still cannot install unity or compiz. i get error messages that tell me about dependencies and broken packages.

can anybody help me, please?

---

### Post by Framli on 2011-09-12
A new version of Compiz is coming today, but a new Unity needs to be built for it. Should be solved in a few hours.

---

### Post by effenberg0x0 on 2011-09-12
+1 unity 3d broke lol :-)
But it will be fixed soon. See the mention of the compiz ABI.
[https://launchpad.net/ubuntu/oneiric/+source/unity/4.14.2-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/unity/4.14.2-0ubuntu2)

     **Changelog**

            * Cherry-pick a fix for remapping minimized window correctly (LP: [#840285]("https://launchpad.net/bugs/840285"))   * debian/control:     - bump build-dep for latest compiz-dev ABI break 

Regards,
Effenberg

---

