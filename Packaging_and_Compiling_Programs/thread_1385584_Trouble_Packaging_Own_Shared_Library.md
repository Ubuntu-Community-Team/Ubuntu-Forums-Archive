---
title: "Trouble Packaging Own Shared Library"
date: 2010-01-19
forum: Packaging and Compiling Programs
---

### Post by Andruk Tatum on 2010-01-19
I am developing a shared library for controlling Wacom tablet devices (much like xsetwacom), but whenever I package something and upload it to Launchpad, I get a package that installs [1], but it doesn't actually install my library file.  The same thing happens with the package for the development files for my library.

Attached are my control, rules, dirs, *.dirs, *.install, and shlibs.local files.  I use the following commands:
debuild -S -sa -k<my_gpg_key>
sudo pbuilder build ../*.dsc
dput --force ppa:csm-ticc/tablettray libwacctl_0.3.3-2_source.changes   (the csm-ticc/tablettray PPA is in my ~/.dput.cf file)
Then I wait for the Launchpad package to build, then I update my local machine and update to the released package from the Launchpad PPA.
Can anybody tell me what I'm doing wrong?

References:
[1] [https://launchpad.net/~csm-ticc/+archive/tablettray/](https://launchpad.net/~csm-ticc/+archive/tablettray/)

---

### Post by Andruk Tatum on 2010-01-19
Replying to get the remaining files uploaded.

---

### Post by SevenMachines on 2010-01-20
hi there, from a brief look at the files you've provided 

* debian/rules: you need to uncomment the dh_install line otherwise the .install files you have wont be used

* in debian/control: you have your package named libwacctl0 but your debhelper files are named libwacctl1.install and so on so wont be used. if you have a line in your control file like 'Package: mypackage', then your debhelper files should be named mypackage.install, mypackage.dirs, etc

* in the actual libwacctl1.install and  libwacctl-dev.install files you seem to have a lot of entries that dont exist. as far as i can tell from your ppa source you have a library file libwacctl.so that you probably want in your libwacctl0 package and headers that you probably want in your libwacctl-dev package. for example (debian library naming policy not withstanding :) ) you'd probably want entries more like

debian/libwacctl0.install
```
libwacctl.so usr/lib/
```and, 
debian/libwacctl-dev.install
```
*.h usr/include/wacctl/
```hope that helps a little

---

### Post by Andruk Tatum on 2010-01-25
That helped a ton, thanks!

---

