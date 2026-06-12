---
title: "Found a BUG"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-04-30
I encountered a bug in Kubuntu and reported it, today I got a reply on my report which probably corrects the problem. The problem is I dont understand what the reply means, Here is the reply can anyone please tell me in plain english what to do?

> ** Attachment added: "I installed all security upgrades, but when I
 wanted to update to 8.04 I got this error"
   [http://launchpadlibrarian.net/14019689/main.log](http://launchpadlibrarian.net/14019689/main.log)

-- 
I cannot upgrade to Kubuntu 8.04
[https://bugs.launchpad.net/bugs/224315](https://bugs.launchpad.net/bugs/224315)
You received this bug notification because you are a direct subscriber
of the bug.

Status in Source Package "update-manager" in Ubuntu: New

Bug description:
Binary package hint: update-manager

Traceback (most recent call last):
  File
 "/tmp/kde-faraz/adept_updater1D0zia.tmp-extract/dist-upgrade.py", line 60, in <module>
    app.run()
  File
 "/tmp/kde-faraz/adept_updater1D0zia.tmp-extract/DistUpgradeController.py", line 1550, in run
    self.fullUpgrade()
  File
 "/tmp/kde-faraz/adept_updater1D0zia.tmp-extract/DistUpgradeController.py", line 1425, in fullUpgrade
    if not self.prepare():
  File
 "/tmp/kde-faraz/adept_updater1D0zia.tmp-extract/DistUpgradeController.py", line 346, in prepare
    self.openCache()
  File
 "/tmp/kde-faraz/adept_updater1D0zia.tmp-extract/DistUpgradeController.py", line 209, in openCache
    self._view.getOpCacheProgress())
  File
 "/tmp/kde-faraz/adept_updater1D0zia.tmp-extract/DistUpgradeCache.py", line 51, in __init__
    raise CacheExceptionDpkgInterrupted, e
CacheExceptionDpkgInterrupted: E:dpkg was interrupted, you must
 manually run 'dpkg --configure -a' to correct the problem.

Delete Reply Forward Spam Move...
Previous | Next | Back to Messages 

---

### Post by Paqman on 2008-04-30
Your bug hasn't been dealt with yet.

Did you try the solution included in that error message? It was to put this into the terminal:
```

dpkg --configure -a

```

Then try running your update again.

---

### Post by warbread on 2008-04-30
Type

```
dpkg --configure -a
``` into the terminal.

---

### Post by hyper_ch on 2008-04-30
and prepend the "dpkg" with "sudo" :)

---

