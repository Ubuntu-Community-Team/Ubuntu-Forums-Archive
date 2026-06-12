---
title: "[SOLVED] Wine and Stability"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-06-26
I'm thinking of installing Wine.  Discussions of the program itself aside, is there any reason why NOT to install something like this?  I'm from a Windows background (unique, I know), so I have a strong paranoia about installing programs.  Is there a chance that installing Wine will destabilize or break my system in any way?  If I use the Applications --> Add/Remove option, do I ever have to worry about that sort of thing with Ubuntu?

Thanks!

---

### Post by iaculallad on 2008-06-26
If the software/application is installed properly, then, there should be nothing to worry about.

Try reading [Ubuntu.Wiki's WinE page]("https://help.ubuntu.com/community/Wine") to give you a head start.

---

### Post by wdaniels on 2008-06-27
> **Eric Qel-Droma said:**
> If I use the Applications --> Add/Remove option, do I ever have to worry about that sort of thing with Ubuntu?

Well, mistakes can and do happen, but very rarely. Applications are more cleanly separated from the underlying systems in Linux, plus there is a good amount of quality control in the packaging process, so they are much less likely to break something the way they often do in Windows. That's not to say that the applications themselves will always work properly, but they shouldn't do any harm to the system more generally.

Certainly, if you stick with the 'official' repositories you shouldn't have any problems. Wine is not going to break anything by itself and it creates an isolated environment for the Windows applications.

---

### Post by shae on 2008-06-27
The only thing to avoid really is absolutely never run wine with sudo or root permissions.

---

### Post by Xiong Chiamiov on 2008-06-27
Installing programs never caused any sort of instability for me; it was rather the terrible hacks I did to the system to make it do something or the other that did so, and that put Kubuntu at about the same stability as XP was for me.

Some applications run absolutely terribly in wine, but it won't kill your system or anything.

---

### Post by jrusso2 on 2008-06-27
The worst thing about WINE is that I have had it hard lock X.

---

### Post by crossedout on 2008-06-27
You shouldn't have any major problems, provided the apps you intend to run are in the wine app database.

Check out this link to see if the app you intend to run is on the list:
[http://appdb.winehq.org/]("http://appdb.winehq.org/")

-Xout

---

### Post by Eric Qel-Droma on 2008-06-27
What does "hard lock X" mean?

---

