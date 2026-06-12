---
title: "Package versions and updates.. How does it work?"
date: 2007-11-04
forum: Packaging and Compiling Programs
---

### Post by jondecker76 on 2007-11-04
As I have gotten more comfortable with Ubuntu, I have been wanting to play around with newer release packages before they hit the Ubuntu repos -
However, I still want automatic updates to work, etc. So my question is:

If I install a newer package than is available in the repos (eiter via .deb file or manually compiling myself), will automatic updates still work when the Ubuntu repos catch up, or even pass up, my manually installed version?

For example, lets say that somepackage-0.1.0 existed in the ubuntu repos. But I noticed that somepackage is now up to 0.1.1, so I download the source, compile and install. Then, sometime in the future somepackage-0.1.2 hits the ubuntu repos and I still have my manually installed 0.1.1 on my local machine.. Will automatic updates still update my system to the new repo package?

Also, how important is the naming convention of packages when it comes to automatic updates? Lets say I compiled and installed someotherpackage-0.1.0 which has its environmental variable for execution as someotherpackage. Then later it goes through a name change to Gsomeotherpackage-0.1.1 then hits the Ubuntu repos..  Can ubuntu make this distinguishment and keep my version updated so long as the environmental variable is unchanged (I.e. it can still be launched in the terminal with someotherpackage)? The reason I'm asking is what if I find 2 sources for the same package, but they have slightly different naming conventions yet are the same program and version.
Do the updates work on the package name itsself, or the environmental variable name of the package?

thanks

Jon

---

### Post by LaserJock on 2007-11-07
The package manager will know nothing of software you've built from source ( ./configure && make && sudo make install and the like) and it should be installed to /usr/local/ so they don't run into each other. Basically, if you install from source the package manager can neither hurt nor help you.

If you install via .debs then the package manager will be aware of the package and would be able to update if the package name is the same. There's no way for the package manager to know that two packages with different names are the same software.

In general the best thing to do is to look for backports of your favorite software.

Hope that helps.

-LaserJock

---

### Post by dholbach on 2007-11-15
You can try [https://wiki.ubuntu.com/MOTU/Recipes/PackageUpdate](https://wiki.ubuntu.com/MOTU/Recipes/PackageUpdate) as well.

---

