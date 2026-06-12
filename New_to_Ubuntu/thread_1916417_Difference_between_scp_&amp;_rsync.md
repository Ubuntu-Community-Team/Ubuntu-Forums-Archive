---
title: "Difference between scp &amp; rsync"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by karthick87 on 2012-01-28
What is the difference between scp & rsync. Can anyone explain in detail with an example pls ..

---

### Post by haqking on 2012-01-28
> **karthick87 said:**
> What is the difference between scp & rsync. Can anyone explain in detail with an example pls ..

scp is a secure copy and uses ssh, it copies files from one location to another and used for remote copying as oppose to local

rsync allows you to sync the files and there contents between one location and another both local and remotely, commonly used for backup purposes.

```
man scp
```

```
man rsync
```

---

