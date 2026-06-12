---
title: "Software updater"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by johncroc on 2013-03-26
The software updater wants to download and install 305 mb of stuff.  Being new to Ubuntu I don't know if I should let it do this.  I'm a little bit afraid because I just spent about a month trying to get Ubuntu working at all and I don't want to screw anything up.  Particularly, when I tried to update to kernel 3.5.0-25 my keyboard and mouse stopped working and now I'm bootng the old kernel (3.5.0-17) with everything working fine.

What can you-all tell me?

John

---

### Post by computerandu on 2013-03-26
If it is software updater, go ahead with it. Nothing should break your system apart from an interrupted installation.

---

### Post by Bashing-om on 2013-03-26
johncroc; Hi !

As a matter of practice I always accept the updates, being aware of what they are. There could be problems if:
You have proprietary software (graphics driver) installed; beyond the package manager's control;
You have 3rd party PPA's installed that may also be beyond PM's control, or the PPA may have gone down.
[INDENT=4]
the risk is worth the gain

[/INDENT]

---

### Post by QIII on 2013-03-26
One word of caution:  If you are offered a partial upgrade, don't do it.  The risk of problems is high.  Wait a day and see if it's all sorted out.

---

### Post by ibjsb4 on 2013-03-26
> **QIII said:**
> One word of caution:  If you are offered a partial upgrade, don't do it.  The risk of problems is high.  Wait a day and see if it's all sorted out.

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

If you want to upgrade everything but the kernel, you can do that in terminal.

```
sudo apt-get upgrade
```

---

