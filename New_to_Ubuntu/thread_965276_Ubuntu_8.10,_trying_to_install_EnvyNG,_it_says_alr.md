---
title: "Ubuntu 8.10, trying to install EnvyNG, it says already installed but I can't find it!"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by GameGuru on 2008-10-31
It isn't in the Accessories>System Tools like it always was in Ubuntu 8.04 when I installed.  I try to uninstall it and it says it can't find it, I do a search for it in synaptic and it isn't found but if I do sudo apt-get install envyng-gtk it says the newest version is already installed.  What do I do?

---

### Post by BKonkle on 2008-10-31
I tried EnvyNG on Intrepid at first, also, but then ended up not needing it.  I don't think the GTK package is working with Intrepid.  It didn't matter, though - the nvidia-glx-177 package included in the repos by default now works flawlessly for my Nvidia graphics card.  The package installs the Nvidia Settings manager to Preferences, so you can set up dual monitors and other features if needed.

---

### Post by GameGuru on 2008-10-31
Sorry, the PC I am doing this on has a Radeon x1650 Pro.

---

### Post by drs305 on 2008-10-31
If you have an apt-get discrepancy where apt-get/dpkg thinks it's installed but synaptic doesn't show it, you can edit the following file. This shouldn't be done routinely but in this case may provide a resolution:
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak
gksudo gedit /var/lib/dpkg/status
```

Find the section listing envyng-gtk and remove the section starting with "Package: envyng-gtk".  Save the file and then run 'apt-get update'

If this doesn't correct the problem, restore the original:
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg.old
sudo mv /var/lib/dpkg/status.bak /var/lib/dpkg/status
```

---

