---
title: "Uninstall lightdm"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by cat2005 on 2012-11-30
How do I unitstall lightdm?  I have KDE and want it to be the sole dm.
 
Ubuntu 64bit 12.04.  KDE 4.8.something.
 
Would uninstalling lightdm cause problems?

---

### Post by deadflowr on 2012-11-30
You shouldn't need to uninstall it. Just use this command:

```
sudo dpkg-reconfigure kdm
```

Which will help set kdm as the display manager.

---

### Post by cat2005 on 2012-11-30
> **deadflowr said:**
> You shouldn't need to uninstall it. Just use this command:

```
sudo dpkg-reconfigure kdm
```Which will help set kdm as the display manager.


deadflowr,

I already have KDE running.  Is that what you mean?  Or do you mean something different?

The reason I want to uninstal lightdm is that I think it could be interfering with a backup remastering program I use (remastersys).  The remastersys program is probably being thrown off by having 2 dm.

---

### Post by deadflowr on 2012-11-30
If you're running kdm(kde display manager), then lightdm(light display manager) is not running, as you can only have one display manager running at one time.

I can see no reason why uninstalling lightdm would cause problems.

But as it is, if the other display manger(kdm) is running, it(lightdm) would be a dead program and shouldn't be affecting the system.

---

### Post by cat2005 on 2012-12-01
> **deadflowr said:**
> If you're running kdm(kde display manager), then lightdm(light display manager) is not running, as you can only have one display manager running at one time.

I can see no reason why uninstalling lightdm would cause problems.

But as it is, if the other display manger(kdm) is running, it(lightdm) would be a dead program and shouldn't be affecting the system.


deadflowr,

For the sake of being thorough, do you know how I would uninstall lightdm?  I assume I could always reinstall it later, correct?

---

