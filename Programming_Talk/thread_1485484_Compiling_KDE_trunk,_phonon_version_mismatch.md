---
title: "Compiling KDE trunk, phonon version mismatch?"
date: 2010-05-16
forum: Programming Talk
---

### Post by Tyrhei on 2010-05-16
Hello,

while trying to compile kdelibs from KDE's trunk on kubuntu 10.04, cmake gives me the following error:

```

CMake Error at cmake/modules/FindPackageHandleStandardArgs.cmake:129 (MESSAGE):
  Could NOT find Phonon: Found version "4.3.1", but required is at least
  "4.3.80" (found /usr/include/qt4)
Call Stack (most recent call first):
  cmake/modules/FindPhonon.cmake:35 (find_package_handle_standard_args)
  cmake/modules/FindKDE4Internal.cmake:670 (find_package)
  CMakeLists.txt:38 (find_package)
```

When I check which version of phonon is installed, I seem to see a mismatch in the phonon libraries installed and the dev includes:
[LIST]
[*]Libraries installed are version 4.4.0 (/usr/lib/libphonon.so.4.4.0)
[*]Headers installed are version 4.3.1 (as indicated in /usr/include/qt4/phonon/phononnamespace.h)
[/LIST]

The libraries come from package libphonon4 version 4:4.6.2-0ubuntu5 and the headers from package libphonon-dev version 4:4.6.2-0ubuntu5.

Is this normal or could this be a mistake in the version of the headers packaged in libphonon-dev?

If this is normal, how can I get the right version installed? Is there an easy way to find a package with the headers for phonon 4.4.0?

Thanks

---

### Post by hazica on 2010-07-04
I've run into the same problem today while trying to compile KDE. The solution for me was rather simple: I've [_added the Kubuntu beta PPA( ppa:kubuntu-ppa/beta ) to my repository sources_]("https://help.ubuntu.com/community/Repositories/Kubuntu"), did a full upgrade, sorted out the dependency issues and I was on my way.

I stumbled upon the solution whilst googleing for version 0.1.4 of libattica dev, which, I discovered, was in the beta PPA.

---

