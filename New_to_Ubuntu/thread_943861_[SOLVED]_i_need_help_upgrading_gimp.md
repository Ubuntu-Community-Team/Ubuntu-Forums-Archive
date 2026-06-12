---
title: "[SOLVED] i need help upgrading gimp"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-10-10
i was browsing through some apps at getdeb.net and i noticed that the version of gimp they offer is newer then the version i currently use

i figured i should uninstall my old gimp before installing the new one

so i went into synaptic and i marked gimp for removal

the problem is that when i mark gimp for removal it automatically marks three other associated applications for removal

normally they would be applications that i no longer would need if i uninstall gimp, but in this case one of the apps that it will remove is called ubuntu-desktop

wont it mess up my system if i remove ubuntu-desktop?

why would uninstalling gimp remove ubuntu-desktop?

how do i remove gimp without removing ubuntu-desktop?

---

### Post by SunnyRabbiera on 2008-10-10
removing ubuntu desktop should cause very few issues and you can try to re install it later.

---

### Post by crjackson on 2008-10-10
> **tjwoosta said:**
> i was browsing through some apps at getdeb.net and i noticed that the version of gimp they offer is newer then the version i currently use

i figured i should uninstall my old gimp before installing the new one

so i went into synaptic and i marked gimp for removal

the problem is that when i mark gimp for removal it automatically marks three other associated applications for removal

normally they would be applications that i no longer would need if i uninstall gimp, but in this case one of the apps that it will remove is called ubuntu-desktop

wont it mess up my system if i remove ubuntu-desktop?

why would uninstalling gimp remove ubuntu-desktop?

how do i remove gimp without removing ubuntu-desktop?

I downloaded all the debs for the new gimp and installed over the old version without any problems. It works fine.

---

### Post by ilrudie on 2008-10-10
Agreed.  I installed over gimp 2.4 with the .debs from getdeb and I've had no problems.

Also [ubuntu-desktop]("http://packages.ubuntu.com/hardy/ubuntu-desktop") is a virtual package.  It does't actually do much for your system* but depends on every package in a standard ubuntu installation.  This is handy if you ever want to switch from some other ?buntu to normal Ubuntu because installing ubuntu-desktop will make sure you have everything you need.  

*Acording to the package description it can be useful in ensuring proper upgrades so they do not recommend removing it.

---

