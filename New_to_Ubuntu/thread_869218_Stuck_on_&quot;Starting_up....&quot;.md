---
title: "Stuck on &quot;Starting up....&quot;"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by VoXoM on 2008-07-24
Alright... I installed an update. Then the next thing you know it tells me to reboot and it gets stuck on Starting up... before it loads ubuntu... Wth? This so pissed me off.... I had to press esc and load an older version or whatever to make it work...

I'm not really new to Ubuntu, but I don't know much. and it is starting to piss me off more and more.

Any help please? Thanks.

---

### Post by coffeecat on 2008-07-24
> **VoXoM said:**
> Alright... I installed an update.

What update? It might help to know.

---

### Post by avtolle on 2008-07-24
I'm guessing you have the proposed repository enabled, and the update installed is the -20 kernel. There are several threads on the Forum today concerning this. Search around, there is a link in at least one of them to a bug report you might wish to join and follow. It appears this updated kernel works for some, but for the majority of those posting, it doesn't (no surprise there).

Unless you want to be involved in testing proposed updates, don't enable the proposed repository. The purpose of the proposed repository is, in fact, to allow users to download packages and test them. The packages themselves may or may not be stable, and can, as here, break your system. So, if you would like for this to not happen in the future, disable the proposed repository in your software sources. Wait for the "new stuff" to be tested, and install when the same make it into the "regular" repositories.

---

### Post by VoXoM on 2008-07-24
> **avtolle said:**
> I'm guessing you have the proposed repository enabled, and the update installed is the -20 kernel. There are several threads on the Forum today concerning this. Search around, there is a link in at least one of them to a bug report you might wish to join and follow. It appears this updated kernel works for some, but for the majority of those posting, it doesn't (no surprise there).

Unless you want to be involved in testing proposed updates, don't enable the proposed repository. The purpose of the proposed repository is, in fact, to allow users to download packages and test them. The packages themselves may or may not be stable, and can, as here, break your system. So, if you would like for this to not happen in the future, disable the proposed repository in your software sources. Wait for the "new stuff" to be tested, and install when the same make it into the "regular" repositories.


You are right. I had the proposed stuff checked. Now that I unchecked it, how do I fix this? Would you mind please linking me to the thread with the bug fix please?

Thanks a lot.

---

### Post by avtolle on 2008-07-24
There is no bug fix, just a report. I'll get you a link in a bit. Meanwhile, the "fix" for the moment is to boot into an older kernel (the one ending in -19).

EDIT: Link to bug report: [https://bugs.launchpad.net/ubuntu/+bug/251344](https://bugs.launchpad.net/ubuntu/+bug/251344)

---

### Post by VoXoM on 2008-07-24
> **avtolle said:**
> There is no bug fix, just a report. I'll get you a link in a bit. Meanwhile, the "fix" for the moment is to boot into an older kernel (the one ending in -19).

EDIT: Link to bug report: [https://bugs.launchpad.net/ubuntu/+bug/251344](https://bugs.launchpad.net/ubuntu/+bug/251344)

Yea thats exactly what I did. K well thanks for the info. I'm assuming that soon there will be an update to fix this while I'm on the -19 kernel.

---

