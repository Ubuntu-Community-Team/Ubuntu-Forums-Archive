---
title: "How does one install LXappearance?"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by tschec713 on 2014-02-28
Hi, I'm still sorta new to any linux distros. And so I'm having troubles running the Tar.gz file. Just the fact that I have no idea what I'm doing.

Can someone help?
Thanks,

---

### Post by Frogs Hair on 2014-02-28
Hello and Welcome

You can get the .deb pkg from the link if it is not already available in the repository. The apt install link should work. 
[URL="http://www.ubuntuupdates.org/package/core/saucy/universe/base/lxappearance-obconf"]
http://www.ubuntuupdates.org/package/core/saucy/universe/base/lxappearance-obconf[/URL]

---

### Post by vasa1 on 2014-02-28
> **Frogs Hair said:**
> Hello and Welcome

You can get the .deb pkg from the link if it is not already available in the repository. The apt install link should work. 
[URL="http://www.ubuntuupdates.org/package/core/saucy/universe/base/lxappearance-obconf"]
http://www.ubuntuupdates.org/package/core/saucy/universe/base/lxappearance-obconf[/URL]
There's no need to do anything special if you have "Universe" [enabled in your Software Sources]("https://help.ubuntu.com/community/Repositories/Ubuntu"). Just search the software center for *lxappearance* and click "install" or, after enabling Universe if you haven't already done so, run 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install lxappearance
```

The *lxappearance-obconf* mentioned above is **not** *lxappearance* but a "plugin" to allow certain aspects of the Openbox window manager to be modified. You will need to install *lxappearance* in any case.

*Actually, I don't know why you're asking this question. If you have installed Lubuntu, you have all you need.*

If you're asking because you don't see *lxappearance*, don't worry. It is there but it has a "user-friendly" name: "Customize Look and Feel".

If you don't dislike using the terminal, run
```
cat /usr/share/applications/lxappearance.desktop
```

---

### Post by tschec713 on 2014-02-28
Thanks guys :)

---

