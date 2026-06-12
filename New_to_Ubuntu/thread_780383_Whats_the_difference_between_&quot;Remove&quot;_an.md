---
title: "Whats the difference between &quot;Remove&quot; and &quot;Remove Completely&quot; in Synaptic"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Afkpuz on 2008-05-03
My title says it all.  I just wanted to know what both options do.  Thanks

---

### Post by Dazed_75 on 2008-05-03
Remove simply uninstalls the program but leaves the package files on your disk ready to reinstall if you choose.  Completely Remove does the obvious so that should you ever choose to re-install, the package(s) would have to be downloaded again.

---

### Post by Monicker on 2008-05-03
> **Dazed_75 said:**
> Remove simply uninstalls the program but leaves the package files on your disk ready to reinstall if you choose.  Completely Remove does the obvious so that should you ever choose to re-install, the package(s) would have to be downloaded again.


Actually, "removely completely" also deletes any configuration files, whereas "remove" does not.

"Remove" is the equivalent of 'apt-get remove"

"Remove Completely" is the equivalent of "apt-get --purge remove"


Reference: [https://help.ubuntu.com/community/SynapticHowto#head-2e236f992402f4adc61a9bb59f0751ce54fea1dc]("https://help.ubuntu.com/community/SynapticHowto#head-2e236f992402f4adc61a9bb59f0751ce54fea1dc")

---

