---
title: "Unable to find Ogre3D demos after doing a repository install"
date: 2009-12-04
forum: Programming Talk
---

### Post by Vyoma on 2009-12-04
Pardon me if this is the wrong section to ask this question.

I want to try out some basic Ogre3D implementations, and hence I downloaded and installed Ogre3D dev packages using Synaptic Package Manager (on Ubuntu 9.10).

Once installed, I was trying to figure out where the Ogre3D demos were installed.

Could some one please point me in the right direction?

Or should I be going for an approach of getting the Ogre3D sources and doing the build myself? Would I then be able to get the Ogre3D demo?

---

### Post by ib.lundgren on 2009-12-04
I know nothing whatsoever about 3D or Ogre but this seem to cover alot:

[http://www.ogre3d.org/wiki/index.php/Ogre_Tutorials](http://www.ogre3d.org/wiki/index.php/Ogre_Tutorials)

---

### Post by SevenMachines on 2009-12-04
ogre demos are not included in the debian packaging due to licensing issues ([see debian bug 327423]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327423")) There used to be a compiledemos.sh script to automatically download and compile them but this seems missing in the latest version, i'm not sure if this was intentional or a bug

---

### Post by Vyoma on 2009-12-06
> **ib.lundgren said:**
> I know nothing whatsoever about 3D or Ogre but this seem to cover alot:

[http://www.ogre3d.org/wiki/index.php/Ogre_Tutorials](http://www.ogre3d.org/wiki/index.php/Ogre_Tutorials)

Yes, I was going through those Tutorials too. But most of them requires a particular header file that is available only in the examples/demos. That was another reason I was looking for the demos/examples.

> **SevenMachines said:**
> ogre demos are not included in the debian packaging due to licensing issues ([see debian bug 327423]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327423")) There used to be a compiledemos.sh script to automatically download and compile them but this seems missing in the latest version, i'm not sure if this was intentional or a bug

Yes SevenMachines - the download script (/usr/share/doc/libogre-dev/examples/compileall.sh ) does seem to be missing in the version (1.6) I installed from repositories. Guess, I need to download the sources and build it myself.

Thanks for the replies!

---

### Post by SevenMachines on 2009-12-06
this is fixed in debian libogre-dev_1.6.4.dfsg1-1. its in debian testing and a sync is requested so it should arrive happilly as part of lucid
[https://bugs.launchpad.net/ubuntu/+source/ogre/+bug/490492](https://bugs.launchpad.net/ubuntu/+source/ogre/+bug/490492)

---

