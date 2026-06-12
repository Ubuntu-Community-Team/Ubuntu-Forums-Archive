---
title: "Launchpad Packaging Dependencies"
date: 2010-08-12
forum: Packaging and Compiling Programs
---

### Post by MrQuincle on 2010-08-12
Dear all,

On the moment I am packaging a 3D robot simulator (see [https://launchpad.net/robot3d](https://launchpad.net/robot3d)). It depends on communication software called YARP which is not (yet) in the Ubuntu repositories. I have already packaged it before on my own system, and I use it locally.

At [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto) it is explained how to add such a self-created package to a local pbuilder test environment:
```
sudo apt-get install dput mini-dinstall
dput local yarp*.changes
```

But how do I add such a dependency on Launchpad, such that it can be found by the pool of (automatic) builders: [https://launchpad.net/builders/](https://launchpad.net/builders/) Again, it is not in the Ubuntu repositories!

[LIST=1]
[*]Is simple uploading a yarp*.deb file to the PPA [https://launchpad.net/~robot3d-team/+archive/ppa-robot3d](https://launchpad.net/~robot3d-team/+archive/ppa-robot3d) enough?
[*]What if I want to include a yarp*.deb file of one of the other PPAs on Launchpad? (Suppose that it will be added to [https://launchpad.net/yarp](https://launchpad.net/yarp) by its developer?)
[/LIST]

Thanks in advance!

PS: Don't bother to look into the Robot3D package yet. I didn't even figure out how to exclude the .bzr files e.g.

---

### Post by MrQuincle on 2010-08-12
> **MrQuincle said:**
> [LIST=1]
[*]Is simple uploading a yarp*.deb file to the PPA [https://launchpad.net/~robot3d-team/+archive/ppa-robot3d](https://launchpad.net/~robot3d-team/+archive/ppa-robot3d) enough?
[*]What if I want to include a yarp*.deb file of one of the other PPAs on Launchpad? (Suppose that it will be added to [https://launchpad.net/yarp](https://launchpad.net/yarp) by its developer?)[/list]


Ah, my second question is answered here: [http://ubuntuforums.org/showthread.php?t=1332003](http://ubuntuforums.org/showthread.php?t=1332003) There is an "Edit PPA Dependencies" option at the right of the [https://launchpad.net/~robot3d-team/+archive/ppa-robot3d](https://launchpad.net/~robot3d-team/+archive/ppa-robot3d) page.

---

### Post by SevenMachines on 2010-08-12
Build depends for ppas should be explained by 
[https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage#Dependencies](https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage#Dependencies)

---

### Post by MrQuincle on 2010-08-12
> **SevenMachines said:**
> Build depends for ppas should be explained by 
[https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage#Dependencies](https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage#Dependencies)

Thanks a lot! I have read that page, but I must have skipped it!

For others: 
> 
Launchpad satisfies your package's Build-Depends using:
[LIST]
[*] the most recent versions of the packages in the PPA you're uploading to
[*] all sections of the primary Ubuntu archive -- i.e. main, restricted, universe and multiverse
[*] optionally: other PPAs in Launchpad. 
[/LIST]


---

