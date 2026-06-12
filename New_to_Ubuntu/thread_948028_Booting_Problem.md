---
title: "Booting Problem"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by djb6 on 2008-10-14
I had trouble with ubuntu so I just went ahead and tried to uninstall it.  I had it installed just like it was a program through windows and for some reason, I couldn't uninstall it properly.  I ended up having to just delete the folder it was in.  The problem I have now is when I boot up my computer, I have the option to still boot Ubuntu and I would like to remove it.  So...how do I do that?

---

### Post by phidia on 2008-10-14
I'm guessing you had a wubi install. You can read the wubi FAQ [here]("http://ubuntuforums.org/showthread.php?t=396526"). I believe a link there can help you.

---

### Post by caljohnsmith on 2008-10-14
All you need to do is take out the following line in your C:\boot.ini file:
```
C:\wubildr.mbr="Ubuntu"
```
To edit your boot.ini file, you might want to use [this guide]("http://users.bigpond.net.au/hermanzone/p9.html"). Let me know how it goes. :)

---

