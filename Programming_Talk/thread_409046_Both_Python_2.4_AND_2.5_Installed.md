---
title: "Both Python 2.4 AND 2.5 Installed"
date: 2007-04-14
forum: Programming Talk
---

### Post by cisforcojo on 2007-04-14
Hey guys,

I've got BOTH python 2.4 and 2.5 installed. Is this a problem?

The problem I ran into was I ran using idle-2.5 and it told me that the pygame module didn't exist. That's because pygame was installed with python 2.4. I went to get rid of 2.4 but TONS of applications were affected (so instead I removed 2.5 which was only affected by idle-2.5 and democracyplayer <--- i don't use) Anyway, do you guys use 2.5? If so, how did you update your system so all your apps are dependent on it and not 2.4?

Thanks!

---

### Post by souki on 2007-04-14
this should not be a problem, all 2.4 modules are installed in /usr/lib/python2.4
all deb packages are version specific : python2.4-xml, python2.3-xml

if you want to use python-2.5 and this version is not the default on your distrib, the best thing to do is probably installing it from source under /usr/local

I think, feisty has 2.5, not sure

---

### Post by cisforcojo on 2007-04-14
It didn't give me any problems with applications. It was just a hassle that pygame installed to 2.4. 
Also, I hate the inefficiency of having 2 copies. Just me. Was wondering what ev1 else does.

For now I got rid of 2.5 and am using 2.4. We'll see what Feisty does. (REALLY hoping they fix the touchpad problem)

---

### Post by souki on 2007-04-14
what I was trying to say is that your problem is a packaged-distribution-problem because python2.5-pygame is not yet packaged

you don't have this kind of problem with sources

if you want to keep your system deb-package-only, then you have to stay with 2.4, or find a repository, or build your own deb package

you can allways install python modules from src (it's often a single command)

---

### Post by cisforcojo on 2007-04-14
Got it. I'll be sorted next week when feisty comes out anyway!

---

