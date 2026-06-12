---
title: "HowTo: Fix PCI: cannot allocate resource region problem"
date: 2006-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by pmilin@ptt.yu on 2006-11-02
This is my first howto, so, I am apologize for any inconvenience.
I have started two-three threads related to the problem of "allocating resource region":
[http://www.ubuntuforums.org/showthread.php?t=282683](http://www.ubuntuforums.org/showthread.php?t=282683)
[http://www.ubuntuforums.org/showthread.php?t=247801](http://www.ubuntuforums.org/showthread.php?t=247801)
[http://www.ubuntuforums.org/showthread.php?t=243453](http://www.ubuntuforums.org/showthread.php?t=243453) (without any reply!)

Also, there are many others, discussing similar problem(s):
[http://www.ubuntuforums.org/showthread.php?t=265132](http://www.ubuntuforums.org/showthread.php?t=265132)
[http://www.ubuntuforums.org/showthread.php?t=2544](http://www.ubuntuforums.org/showthread.php?t=2544)

I have HP nx8220, and my particular problem was:
```

[17179571.952000] PCI : Cannot allocate resource region 7 of bridge 0000:00:1e.0
[17179571.952000] PCI : Cannot allocate resource region 8 of bridge 0000:00:1e.0
[17179571.952000] PCI : Cannot allocate resource region 9 of bridge 0000:00:1e.0

```
that showed at the very beginning of the booting.

Yesterday, I found BIOS-upgrade for my HP nx8220, and try it (from Windows, of course). What have happened is that those ugly messages have gone. Now, booting is nice and flawless.
Try or find bios-upgrade for you particular model of laptop. Upgrade that I have used is for couple of related HP-models at the:
[http://h18007.www1.hp.com/support/files/hpcpqnk/us/download/23845.html](http://h18007.www1.hp.com/support/files/hpcpqnk/us/download/23845.html)

Sincerely,
Petar Milin

---

### Post by mrojas73 on 2006-12-02
I would be nice to be able to update using linux since some of us don't have windows installed.

---

