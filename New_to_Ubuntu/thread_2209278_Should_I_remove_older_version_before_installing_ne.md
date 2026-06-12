---
title: "Should I remove older version before installing new versions of a software ?"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by Ardeshir on 2014-03-04
HI Everyone !
I have CodeBlocks 12.11 on my Ubuntu but I want to install teh newest version 13.12 which I downloaded from CodeBlocks official site .
Should I just install them or I should delete (remove) the older version before installing the new one .

+NOTE :
There are some plugins of CodeBlocks I have on my system which only works with the 13.12 version and I don't want to lose them !
Thanks !@

---

### Post by monkeybrain20122 on 2014-03-04
You should just install 13.12 from a ppa (kind of unofficial repositories which integrate into the system and will be upgraded through normal channel)

[https://launchpad.net/~pasgui/+archive/ppa/](https://launchpad.net/~pasgui/+archive/ppa/)

Here are the commands

```
sudo add-apt-repository ppa:pasgui/ppa
sudo apt-get update
sudo apt-get install codeblocks
```

You don't need to uninstall the old version, the installation of 13.12 this way would be just like a normal upgrade through the package manager.

---

