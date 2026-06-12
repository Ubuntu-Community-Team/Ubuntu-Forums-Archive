---
title: "[SOLVED] Upgrading to Hardy Heron?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by BassKozz on 2008-05-05
Are there any risks involved in upgrading from 7.10 to 8.04 ?
Is it best to upgrade using the _S_ystem->_A_dministration->Update Manager?

Is there anything I should know about before pulling the trigger?

---

### Post by aheckler on 2008-05-05
I always do a clean install from a LiveCD for upgrades. IMHO, it just feels "cleaner" and there seem to be less problems that way, but that's just my experience.

As always, make sure to **back up your data first**, either route you choose.

---

### Post by Promaster91 on 2008-05-05
I don't think so. If you don't want to do it online you can download the iso, burn it to a CD and run ```
 gksu "sh /cdrom/cdromupgrade" 
```
That is how I did it. You can also check the cd for defects just to be safe. More info at:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by hyper_ch on 2008-05-05
you don't even need to burn it as you can mount the image directly itno the filesystem.

---

### Post by Sef on 2008-05-05
> Are there any risks involved in upgrading from 7.10 to 8.04 ?

Yes, there are.  Sometimes, the update does not go well, and you could be left with either problems, or a broken system.

Even if you upgrade via the update manager, have a cd of Hardy already burned, and make sure it is good.  (Use the check cd, instead of starting the live cd.)  This way in case the upgrade does not go well, you can do a clean install.

> Is it best to upgrade using the System->Administration->Update Manager?

Best way is to do a clean install, although you have to reload all your configurations.


> Is there anything I should know about before pulling the trigger?
__________________

As has been stated already, **back up** your data, no matter which way you upgrade.

---

