---
title: "Unable to install my unity in ubuntu 13.10"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by coffeepenguin on 2013-11-04
I have been trying to install my unity, however  whennever I run sudo apt-get update  the packages get a 404. 

```
W: Failed to fetch http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/saucy/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found
```

so that when I try to install it I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package myunity
han_solo@MilleniumFalcon:~$ 
```

---

### Post by monkeybrain20122 on 2013-11-04
How did you add the ppa?

---

### Post by Frogs Hair on 2013-11-04
For 13.10 you would need to install the Unity Tweak Tool which is in the software center and there is a development PPA as well.

[http://www.omgubuntu.co.uk/2013/03/unity-tweak-tool-is-now-available-in-raring](http://www.omgubuntu.co.uk/2013/03/unity-tweak-tool-is-now-available-in-raring)

---

### Post by deadflowr on 2013-11-04
+1 for unity-tweak-tool.
Myunity hasn't been updated to any release beyond 12.04.

Not sure it still works but another one is [unsettings]("http://www.florian-diesch.de/software/unsettings/")

---

### Post by coffeepenguin on 2013-11-04
Thank you so much! I can't believe I was downloading the wrong program.

---

### Post by deadflowr on 2013-11-04
> **coffeepenguin said:**
> Thank you so much! I can't believe I was downloading the wrong program.

No problem.
It's the nature of the beast.
Programs come and go and users tend to recommend that which they know works for them.
However, as development proceeds, things get mixed up and older tools can fall to the wayside.

I think it took me at least a month into quantal's release to realize that myunity was broken, and that I should stop recommending it for newer versions of Ubuntu beyond 12.04.

---

### Post by Frogs Hair on 2013-11-04
Remove that old PPA from Software & Updates > Other Software or it will cause errors.

---

