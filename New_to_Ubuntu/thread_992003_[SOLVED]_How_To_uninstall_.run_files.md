---
title: "[SOLVED] How To uninstall .run files"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-11-24
Hello, i just installed the proprietary ati drivers downloaded from ati.amd.com, now i want to uninstall that drivers including ati catalyst, i installed from a .run file something like
```
sudo sh ati-driver-installer-8-11-x86.x86_64.run
```

Now, dont know how to uninstall the files installed by that drivers?
anyone knows?
thanks

---

### Post by drakeman007 on 2008-11-24
> **drakeman007 said:**
> Hello, i just installed the proprietary ati drivers downloaded from ati.amd.com, now i want to uninstall that drivers including ati catalyst, i installed from a .run file something like
```
sudo sh ati-driver-installer-8-11-x86.x86_64.run
```

Now, dont know how to uninstall the files installed by that drivers?
anyone knows?
thanks


Well, if any want to know the answer, of how to uninstall proprietary ati drivers, follow this... (I put this answer for reference, and if any of you can uninstall an ati drivers too!...

```
Automatic or Custom Driver Installations
If the ATI Proprietary Linux Driver was installed using either the Automatic or
Custom options, then do the following:
1 Launch the Terminal Application/Window and navigate to the /usr/share/ati
folder
2 With superuser permissions, enter the command "sh ./fglrx-uninstall.sh"
You have now successfully uninstalled the ATI Linux Proprietary Driver.

```

thanks...

---

