---
title: "After Partial Upgrade, Ubuntu won't Boot"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Umenzi on 2008-11-16
I tried to upgrade to Intrepid earlier, but during installation, I was asked whether to replace the old menu.lst with a new copy. I pressed open a new shell, and the dialog box crashed. Then the installation wouldn't continue, and update manager no longer listed the 8.10 upgrade. Then I restarted, and ubuntu only gets past the loading bar, after which it spits out some command line jargon, trying to read some files which may or may not exist, and then leaves me there. I'm helpless.

GRUB is still working, so I could boot into recovery mode if I wanted to, but I really don't know what I would do. I'm hesitant to do that because it resets the menu.lst file, which I have modified to let me enter XP.

---

### Post by zvacet on 2008-11-16
I will try in recovery mode 

```
apt-get update && apt-get dist-upgrade
```

But that is just my opinion.Maybe somebody else will correct me and give you better solution.

---

