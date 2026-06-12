---
title: "Compiling from source vs downloading a package"
date: 2014-10-23
forum: New to Ubuntu
---

### Post by Karnivaurus on 2014-10-23
I am writing a C++ project in Ubuntu, and I would like to link to some third-party libraries. As such, I am trying to understand the difference between downloading and installing a package, and downloading the source and compiling locally.

Specifically, I am wanting to the use Point Cloud Library. Now, originally I downloaded this via aptitude. However, I have since learned that the library I want to use is in fact not in this package, but in a more recent version of the code which is on GitHub. If I now download the code from this repository, and compile the entire PCL library from scratch, how will this interact with dpkg?

So, the questions I would like to ask are:

1. Will the new libraries compiled from source overwrite the old libraries downloaded in the package?
2. If I now delete the original package using aptitude, will this also delete the libraries that I just compiled from source?

---

### Post by kc1di on 2014-10-23
Hi Karnivaurus and welcome to Ubuntu,

To the best of my recollection if you compile the package from source and then make it and make install it will upgrade those Libraries to the news ones.
if you delete the original package I believe will will not delete all the dependencies.  only that part that is part of the package itself. 
That is most package do not include all the libraries and other files but the are downloaded and pulled from the repository as needed by the package manager, apt. 
so that if you just remove the original package the dependencies are not completely removed. 

Maybe some else can explain that better. 
in any event I would go for it. see what happens. 
good luck.

---

### Post by Rocket2DMn on 2014-10-23
It ultimately depends on where your custom compiled binaries/libs are installed to.  You should check existing documentation.  Properly organized projects should not screw up dpkg/apt or otherwise conflict with installations handled by common package managers, but this is non a hard-and-fast rule.

If you don't need the version you installed from the repositories, you could just remove it before you do anything with the code you pull from GitHub.

Perhaps the safest thing to do is not install the build you are making from the GitHub code, just build it in place.  Instead, you can modify your own project's build to link with the required libraries in a non-standard location (in this case, PCL's build directory).  For example, either copy the compiled libs into your project's folder structure (e.g. in a lib/ directory), or include the PCL library's build path in your compiler options.

---

### Post by 3246251196 on 2014-10-23
As an addition to this question. If I am forced to download source, compile and install I believe it does not get added to the package list. What is the best way to deal with this? Create a package from the binaries you have just compiled and then run it with dpkg to install such that it gets included into the list of installed packages?

---

### Post by steeldriver on 2014-10-23
You may find the checkinstall program useful

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

