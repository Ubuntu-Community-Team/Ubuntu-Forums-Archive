---
title: "local(personal) repo for checkinstalled compiled .deb:s"
date: 2008-05-04
forum: Packaging and Compiling Programs
---

### Post by of_darkness on 2008-05-04
I want to have a local repository 2 keap and mange my checkinstalled debs

cause whit checkinstall you can oly remove a package whit apt not reinstall it.

I tried dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz and added a line in my sources list. 

But as checkinstall dosent add dependency info apt-get uppgrade gave eeror about it and could not continu..

I it possible to do it in a better way? i looked at the real packing way but it was all to mouch jobb for it to be intresting whern im only doing it for my own system.. but if there is a light wersion of it that works whit local repo then well why not..

---

### Post by mc4man on 2008-05-04
If there is a debian dir. in your source you could use ```
fakeroot debian/rules binary
``` or ```
dpkg-buildpackage -rfakeroot -b
``` 
look thru rules file in debian to ck., mod configure options and or add to command. For example for mplayer today
~/mplayer$ DEB_BUILD_OPTIONS="--prefix=/usr/local --disable-pulse --enable-gui" fakeroot debian/rules binary
Getting the build to install to /usr/local/ required some careful editing of rules file, the configure option was ineffectual

edit: you maybe need to add a few packages, fakeroot, debhelper ...

---

