---
title: "Differences between upgrade and dist-upgrade"
date: 2015-03-03
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-03-03
I read the manual entries for apt-get upgrade and apt-get dist-upgrade as well as did a brief google search but I'm still not entirely understanding what each does and when one is preferred over the other.

Am I wrong in saying that:

1. apt-get upgrade will update all packages to the newest available version if this means that no additional packages are removed or installed? So if *any newer version of a package needed an extra dependency* or *it no longer needed a dependency that was required by the previous version* (and therefore, the dependency will now be redundant), the package will not be installed? I'm not too sure about the latter--what happens to the dependency that is now redundant if the package gets upgraded in this situation?

2. apt-get dist-upgrade will update all packages to the newest available version no matter what. It will also install and remove dependencies as needed (install dependencies to satisfy packages, obviously, but also remove dependencies that became orphaned if a package that was updated no longer needed the dependency. 

Also, any caution/tips in using either.

Thanks.

---

### Post by grahammechanical on 2015-03-03
This is what I go by

apt-get upgrade

> [COLOR=#333333][FONT=Ubuntu]This command upgrades all installed packages. This is the equivalent of "Mark all upgrades" in Synaptic.[/FONT][/COLOR]

apt-get dist-upgrade

> [COLOR=#333333][FONT=Ubuntu]The same as the above, except add the "smart upgrade" checkbox. It tells APT to use "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary.[/FONT][/COLOR]

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

In my experience, apt-get upgrade will bring in some package upgrades but there will sometime be others that are held back for some reason. But apt-get dist-upgrade will also bring in the held back packages. And there is a risk that smart conflict resolution system is not so smart. Something gets removed that breaks our setup.

If we want to install packages from a PPA we may need to run apt-get dist-upgrade to bring in those packages. But otherwise if I was running a released version of Ubuntu and I wanted it to remain stable I would not run apt-get dist-upgrade.

I run the development version of Ubuntu and I rarely run apt-get dist-upgrade and if I do I keep my fingers crossed. The other day I noticed that others running Vivid Vervet had been upgraded to Linux kernel 3.19 but that had not come through on my system. So, I ran apt-get dist-upgrade to get the kernel. It would have been installed eventually. I decided not to wait. 

The apt-get dist-upgrade command will bring in everything that is in the Proposed repository if we have it enabled. The purpose of the proposed repository is described in this way:

> 
[LIST]
[*=left]"Pre-released Updates (raring-proposed)". The testing area for updates. This repository is recommended only to those interested in helping to test updates and provide feedback.
[/LIST]


[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

It is for code that has not yet been placed in the standard repositories but the code is made available to be installed and tested.

Regards.

---

### Post by Impavidus on 2015-03-03
If a new version of a package needs a new dependency, apt-get dist-upgrade will upgrade and install the dependency, apt-get upgrade won't. Kernel upgrades usually come as a new package, which is a new dependency of the new version of the kernel metapackage. If you want to install kernel upgrades by command line, you need apt-get dist-upgrade. This is to make it possible to keep an old kernel and keep the system bootable if there is a bug in the new kernel or installation failed.

If a new version of a package conflicts with an already installed package, apt-get dist-upgrade may remove the conflicting package and upgrade the other, apt-get upgrade won't. But I've never seen apt-get dist-upgrade remove packages, so I assume it's rare. But I don't run the development version or use many PPAs.

When a new version of a package no longer depends on some dependency, both apt-get upgrade and apt-get dist-upgrade will upgrade the package and leave the dependency in place (possibly upgrading that too; there is no need to remove the ex-dependency), but it may become autoremovable.

---

### Post by garycheng12 on 2015-03-03
> **Impavidus said:**
> If a new version of a package needs a new dependency, apt-get dist-upgrade will upgrade and install the dependency, apt-get upgrade won't. Kernel upgrades usually come as a new package, which is a new dependency of the new version of the kernel metapackage. If you want to install kernel upgrades by command line, you need apt-get dist-upgrade. This is to make it possible to keep an old kernel and keep the system bootable if there is a bug in the new kernel or installation failed.

If a new version of a package conflicts with an already installed package, apt-get dist-upgrade may remove the conflicting package and upgrade the other, apt-get upgrade won't. But I've never seen apt-get dist-upgrade remove packages, so I assume it's rare. But I don't run the development version or use many PPAs.

When a new version of a package no longer depends on some dependency, both apt-get upgrade and apt-get dist-upgrade will upgrade the package and leave the dependency in place (possibly upgrading that too; there is no need to remove the ex-dependency), but it may become autoremovable.

Just what I needed--thanks.

---

