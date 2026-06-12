---
title: "[SOLVED] Get Ubuntu's Standard Network Manager Back!"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-07-25
I recently installed wicd to replace the standard network manager in Ubuntu to see if it was any better (it wasn't) but i would like to remove it and use the standard network manager again...how do i re-enable the old network manager?:confused:

Thanks in advance!

---

### Post by issih on 2008-07-25
```

sudo apt-get install network-manager-gnome
```

That ought to reinstall the needed package

Hope that helps.

---

### Post by phidia on 2008-07-25
If you used apt-get/synaptic to install Wicd then the package manager removed NM.
To install it again-and remove wicd install network-manager && network-manager-gnome.
Either look for those packages with synaptic or in terminal: "sudo apt-get install" both those. Hope that helps.

---

### Post by kamitsukai on 2008-07-25
Thanks!

---

