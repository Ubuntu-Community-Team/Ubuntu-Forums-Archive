---
title: "install ubuntu on a separate partion"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by vibaviattigala on 2012-10-17
i have windows xp on C: drive and i have 4 partion 100 GB each
and my D: drive is empty is there a way to install ubuntu with wondwos xp separate partion? to drive D:?.i dont want to install along windows option it will reduce the performacne right?

---

### Post by oldfred on 2012-10-17
If you are dual booting, performance of one system or the other is not changed.

You can only have 4 primary partitions with MBR partitioning. You can delete your d: partition if you are sure it is empty and convert it to an extended partition. Extended partition is a container for logical partitions and you can create all the additional partitions you need and Ubuntu will boot from logical partitions.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by Wim Sturkenboom on 2012-10-18
> **vibaviattigala said:**
> i dont want to install along windows option it will reduce the performacne right?
Wrong ;)

If you install Ubuntu inside Windows (Wubi install), you might have a performance penalty; if that performance penalty is really noticeable is another question. With Wubi, you install Ubuntu in a file on one of the drives.

If you forget about the term 'drive' and only think in partitions, you can install Ubuntu in the partition that Windows calls 'drive D:'. In that case it will be alongside Windows.

Follow Oldfred's advise and read the links that he provided.

---

