---
title: "Upgrading a package &quot;by hand&quot;"
date: 2005-03-05
forum: Programming Talk
---

### Post by Stephen-I-M on 2005-03-05
I'm in search of some general FAQ's/tutorials on making a Ubuntu package.

My first wish is to learn how hard it is to upgrade an existing package.

For example, roundup ([http://higgs.djpig.de/ubuntu/www/hoary/web/roundup](http://higgs.djpig.de/ubuntu/www/hoary/web/roundup)) is at version 0.7.10-1ubuntu1, but the project ([http://roundup.sourceforge.net/](http://roundup.sourceforge.net/)) is at 0.8.

Is there an equivalent of a rpm spec file that one can extract from the current package and use to update it to the latest code? I could just use checkinstall, but the package does some nice things for you that I'd like to capture.

Stephen

---

### Post by GilGalad on 2005-03-05
This is what I do... (probably there are better ways but...)
Surely there is some guide somewhere...

Download the new version, untar it and inside the derectory type
dh_make
This will make a directory debian/ with the basic files in it.  The rules file is the makefile and usually you do not need to modify it. Configure the control file with the name and description of the package. Type 'fakeroot dpkg-buildpackage'. If it works  you can go ahed and install.

You can always do:
apt-get source <oldpackage>
dpkg-source -x <oldpackage>.dsc
and have a look at the <oldpackage>/debian directory and compare (or copy the files).

---

### Post by Stephen-I-M on 2005-03-05
[QUOTE=GilGalad]This is what I do... (probably there are better ways but...)
Surely there is some guide somewhere...
[/QUOTE]

Are there similar instructions for a python package using distutils?

Stephen

---

### Post by GilGalad on 2005-03-05
Well I guest you can download some sources (e.g. numarray, Numeric, matplotlib) and look how they have done it.  My guess is that in the file debian/rules you only need to change the configure & make lines with the equivalent for python "python setup.py install --prefix=???".

I don't have experience with those yet - but I am interested as well...

---

### Post by toojays on 2005-03-05
I had to learn how to do this recently as Ubuntu is the first time I'd used a Debian based distro.

My advice is to first install the "Debian New Maintainers Guide" (the "maint-guide" package) and read that. That gives you a good idea of how the Debian packaging process works.

Then download the source package (e.g. "apt-get source roundup") and look in the file debian/rules to see how that package is built. In the easiest case, to  make an upgraded package, you will just need to put the new source tarball in the right place, update the changelog, and run "dpkg-buildpackage -rfakeroot".

The version number is usually taken from the Debian changelog, so you will need to add a new entry. The package dpkg-dev-el has some nifty modes for editing dpkg related files.

---

