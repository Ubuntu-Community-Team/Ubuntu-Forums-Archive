---
title: "removing update-manager &amp; update-notifier"
date: 2021-02-12
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2021-02-12
Hello all,

I want to remove 'update-manager' and 'update-notifier' as I always update manually from the terminal and I'm sick of the graphical stuff popping up every time I boot the PC.

but when I 'apt-get remove' them it wants to remove more packages than just those two...```
The following packages will be REMOVED
  ubuntu-desktop ubuntu-desktop-minimal ubuntu-release-upgrader-gtk update-manager update-notifier


```
Why is this? I thought if these were orphaned dependencies then they would be removed by running apt-get autoremove?

Any advice would be appreciated!

---

### Post by TheFu on 2021-02-12
ubuntu-desktop ubuntu-desktop-minimal are meta-packages.  Removing any single dependency they include automatically removes those meta-packages ... but don't worry, it won't remove your GUI.

You may want to know that **do-release-upgrade** won't work after you remove those things, so when you want to move to a different release and us that process (rather than the manual method), you'll probably want to reinstall update-manager.  I don't think the other packages are needed.

---

### Post by jcdenton1995 on 2021-02-13
> **TheFu said:**
> ubuntu-desktop ubuntu-desktop-minimal are meta-packages.  Removing any single dependency they include automatically removes those meta-packages ... but don't worry, it won't remove your GUI.

You may want to know that **do-release-upgrade** won't work after you remove those things, so when you want to move to a different release and us that process (rather than the manual method), you'll probably want to reinstall update-manager.  I don't think the other packages are needed.

Thanks! That's good to know.

Just out of interest, I found this on the ubuntu documentation wiki...> A metapackage, such as **ubuntu-minimal** or **ubuntu-desktop**,  can have a long list of dependencies.  So, when a metapackage is  automatically removed by the removal or purging of any one, or more, of  its underlying dependencies, all of the other packages that were in the  metapackage's depends list are still installed on the system.  If at a  later time, there is an upgrade to the metapackage, the upgrade cannot  occur, because the metapackage to be upgraded is no longer installed on  the system.So if one of a meta-packages dependencies are removed, the meta-package is also removed, because if the entire list of it's dependencies are not installed, technically that meta-package is not installed because by definition the meta-package *is* it's dependencies.

But what happens if you remove a meta-package directly? does that actually remove all it's dependencies?

Or have I got that bit wrong?

---

### Post by deadflowr on 2021-02-13
Try turning it off
```
gsettings set com.ubuntu.update-notifier no-show-notifications true
```

---

### Post by Dennis N on 2021-02-13
> But what happens if you remove a meta-package directly? does that actually remove all it's dependencies? Or have I got that bit wrong? 
No it doesn't remove any dependencies. If metapackage A depends on package B, removing B will remove A. But, since nothing depends on A, you can remove metapackage A alone.

---

### Post by TheFu on 2021-02-13
Try it.  See what happens. ;)  There's a reason that apt asks (Y/n).  Use that to do nothing, after seeing what apt proposes.

---

### Post by Impavidus on 2021-02-13
A metapackage is a package that has no contents, but only some metadata like a version and a list of dependencies. When you remove a package (and this can be a metapackage or a normal package or even a virtual package, in a sense), every package that depends on it will be removed too. ubuntu-desktop is a metapackage designed to conveniently pull in a large collection of software that's considered default software on Ubuntu desktop systems. If you don't want all of it, you can't have ubuntu-desktop, but not having ubuntu-desktop doesn't rule out having the packages it depends on.

When you remove a metapackage, nothing really happens (other than triggering the removal of any packages depending on that metapackage; they are not necessarily at the root of the dependency tree). The quote you found in the wiki is not very clear, but there's one important point to make regarding upgrades and metapackages. Kernel upgrades are distributed in a different way than upgrades to other packages. With most packages, a new version of the package is put in the repositories and automatically installed, overwriting the old version. In case of kernel upgrades, the new version is in a separate package and doesn't overwrite the old version. This is because sometimes the new version doesn't work on some hardware. The new kernel version is installed by providing an upgrade for a metapackage, which depends on the new kernel package. As the metapackage is upgraded, it automatically pulls in the new dependency, installing the actual upgrade. So whilst most metapackages are nothing more than a convenient way of installing a large collection of software at once, the kernel metapackages are required to get automatic upgrades.

---

### Post by jcdenton1995 on 2021-02-13
Well all that clears it up, I'm marking the thread as solved. Thanks to everyone who replied! there's some good information here.

---

