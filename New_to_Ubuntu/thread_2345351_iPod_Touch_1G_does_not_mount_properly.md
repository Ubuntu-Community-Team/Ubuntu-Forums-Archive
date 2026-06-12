---
title: "iPod Touch 1G does not mount properly"
date: 2016-12-03
forum: New to Ubuntu
---

### Post by alryaz2 on 2016-12-03
Hello!

I'm seriously getting frustrated by this issue, where GVFS would not mount my **iPod Touch 1G (8GB, on 3.1.3, jailbroken, afc2add installed)** over the AFC protocol.
On the other side, the *ifuse* package that I have installed, allowed me to browse the filesystem using a manual mount.
I've seen this issue in the following distributions: *Linux Mint 18*, *Ubuntu Gnome 16.04* and *Lubuntu 16.04*. I have tried numerous tutorials, yet most of them concern either an older distribution of Ubuntu, or a version of iOS significantly higher than mine (3.1.3).

I am not sure whether I should file a bug report considering the fact that I haven't found any similar problems on the internet. I might as well missed something during the configuration process.
Could somebody help me with this issue? I am currently running *Ubuntu Gnome 16.04* with *Gnome 3.18 Shell*. My primary goal is to get it working either with *Rhythmbox* or *Lollypop*.

---

### Post by alryaz2 on 2016-12-03
Just stumbled upon a bug report citing some breaking changes in the version **1.28** of *gvfs* package family. A downgrade to **1.27.4** solved the issue.

---

### Post by oldrocker99 on 2016-12-03
Welcome to the forums!

Since you have solved this problem, please use the Thread tools to mark this thread as [SOLVED]. Thanks.

---

