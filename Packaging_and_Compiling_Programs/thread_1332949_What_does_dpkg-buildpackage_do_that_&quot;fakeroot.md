---
title: "What does dpkg-buildpackage do that &quot;fakeroot debian/rules binary&quot; doesn't?"
date: 2009-11-20
forum: Packaging and Compiling Programs
---

### Post by glennric on 2009-11-20
I am trying to build a package from some sources that I have.  In the past either using "fakeroot debian/rules binary" or dpkg-buildpackage give debs that seem to have the same functionality.  I usually use "fakeroot debian/rules binary" to test if the rules file and such work, and then I use pbuilder for a proper build.  Of course pbuilder used dpkg-buildpackage.  The package I am working on building (it happens to be d2x-xl) only contains one binary executable file that is installed to /usr/bin.  Both methods build the package, but with dpkg-buildpackage the resulting executable file is about .2 megs smaller.  This would be good news if it weren't for the fact that some of the functionality of the program is lost.

So what I want to know is what is it that dpkg-buildpackage does to the executable binary in this package that "fakeroot debian/rules binary" does not do, and is there a way to override this so that dpkg-buildpackage doesn't do it?

---

### Post by SevenMachines on 2009-11-22
the man page gives a good description of the stages run by dpkg-buildpackage, better than mine but in essence for a binary only build
1. set environmental variables for the build
2. check dependencies
3. run fakeroot debian/rules clean
4. run debian/rules build then fakeroot debian/rules binary
5. sign .dsc file, run dpkg-genchanges, sign .changes file

perhaps theres some variables being set for the build by dpkg that you don't expect?

---

### Post by glennric on 2009-12-02
Yeah, I had read the man page, and I suspected it had something to do with the environment variables that are set.  It turns out that it was.  By default dpkg-buildpackage sets the compiler optimization flag "-O2".  Normally this would be good; however, it breaks things with the d2x-xl code.  Largely because the d2x-xl code is pretty poorly written, without proper consideration for data types.

---

