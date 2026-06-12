---
title: "Problem packing a python program"
date: 2010-05-26
forum: Packaging and Compiling Programs
---

### Post by zimio on 2010-05-26
Hi there! So, am trying make this deb package for a modified version of comix and I've been following [this guide]("https://wiki.ubuntu.com/PackagingGuide/Python"). The problem comes when I reach the "Building instructions - debian/rules" section. It tells me that terminator (the python program they use as a example) has a setup.py "which reduces our job here to almost nothing". Unfortunalety, comix doesn't have that script, instead, it has a install.py which copies everything to its proper place.

How do I go from here with the CDBS being unable to use a setup.py like the one in the guide am clueless.


Thanks in advance for any help.

---

### Post by SevenMachines on 2010-05-28
hi there. The only things i know you can override for cdbs python-distutils are the following (before the includes i think(?) )
DEB_PYTHON_SETUP_CMD
DEB_PYTHON_CLEAN_ARGS 
DEB_PYTHON_BUILD_ARGS 
DEB_PYTHON_INSTALL_ARGS_ALL

I'm dont think changing the setup command to install.py would improve the situation in this case though as it doesnt look like it works in an 'expected enough way' for cdbs though.

Best advice I could give would be to look at the current package and see what they've done, it really depends if your trying to do. if you want to

* Modify a package
    $ apt-get source comix and then use the patch system to add your changes

* Do/Learn the packaging for yourself
    Still probably a good idea to look at the way its done now for ideas. If you want to do this you'll probably need to use debhelper rather than cdbs (which is how its done in the current packaging)

hope thats some help

---

