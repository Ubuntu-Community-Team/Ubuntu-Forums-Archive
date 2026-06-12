---
title: "How to look at source code"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by brushman on 2011-09-09
Just for fun I want to look around the source code of the linux kernel and the ubuntu software.

What's the easiest way to do this without chance of messing up my computer? I know there's different "packages" I need to download but I don't know how to download these or what the names are of packages I can download.

Thanks

---

### Post by haqking on 2011-09-09
> **brushman said:**
> Just for fun I want to look around the source code of the linux kernel and the ubuntu software.

What's the easiest way to do this without chance of messing up my computer? I know there's different "packages" I need to download but I don't know how to download these or what the names are of packages I can download.

Thanks

Source for 10.04 is [here]("http://old-releases.ubuntu.com/releases/releases/10.04/release/source/")

you can change the version number in the URL for a few other versions, not every version is there.

as for source of packages then:


sudo apt-get build-dep package

then do 

sudo apt-get source package

package is name of package

---

### Post by sisco311 on 2011-09-09
EDIT: d'oh haqking beat me to it! :)

Just a note: you don't need to download the source code as root (don't use sudo in the front of the command).

/EDIT
Hi, 


You can download the source code of any package with the following command:
```
apt-get source **package-name**
```

You may have to enable the *source* repository first. For instructions, see: [uhelp]community/Repositories/Ubuntu[/uhelp]

---

