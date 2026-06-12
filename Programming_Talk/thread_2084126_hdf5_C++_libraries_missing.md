---
title: "hdf5 C++ libraries missing?"
date: 2012-11-14
forum: Programming Talk
---

### Post by Elador0 on 2012-11-14
Hi,

I'm on Ubuntu 12.10 and I've installed libhdf5-serial-dev, libhdf5-dev and libhdf5-7. This installs amongst other things:
/usr/lib/libhdf5.a
/usr/lib/libhdf5.so
/usr/lib/libhdf5_fortran.a
/usr/lib/libhdf5_fortran.so
/usr/lib/libhdf5_hl.a
/usr/lib/libhdf5_hl.so

But the C++ library is completely missing. When you build it yourself or use windows, there's also a libhdf5cpp, the C++ obj. oriented interface to the libhdf5...
The problem is of course that my application doesn't build because the CPP lib/headers (e.g. H5Cpp.h and all others) are missing.

I can't find a package in the ubuntu repo with the CPP lib.

Thank you for any help.

---

### Post by Elador0 on 2012-11-14
12.10:

[http://packages.ubuntu.com/search?searchon=contents&keywords=H5Cpp.h&mode=exactfilename&suite=quantal&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=H5Cpp.h&mode=exactfilename&suite=quantal&arch=any)

You have searched for files named H5Cpp.h in suite quantal, all sections, and all architectures.
Sorry, your search gave no results

12.04:

[http://packages.ubuntu.com/search?suite=precise&arch=any&mode=exactfilename&searchon=contents&keywords=H5Cpp.h](http://packages.ubuntu.com/search?suite=precise&arch=any&mode=exactfilename&searchon=contents&keywords=H5Cpp.h)

You have searched for files named H5Cpp.h in suite precise, all sections, and all architectures. Found 1 results.
/usr/include/H5Cpp.h	libhdf5-serial-dev


What's going on?

---

### Post by MadCow108 on 2012-11-14
yes the c++ library is missing
it has been added again in debian experimental:
[http://packages.qa.debian.org/h/hdf5/news/20121001T210247Z.html](http://packages.qa.debian.org/h/hdf5/news/20121001T210247Z.html)

this will likely make it into 13.04

---

### Post by Elador0 on 2012-11-14
Ok..... can I somehow install from this repo?

---

### Post by MadCow108 on 2012-11-14
you can probably install the debian libraries into quantal with no issues, precise is less likely to work, but it might.

possibly you will have to build it from source to get everything right.
```
apt-get install devscripts equivs ubuntu-dev-tools
pull-debian-source hdf5 experimental
cd hdf5-*
sudo mk-build-deps -ir
debuild -us -uc
#pick the library packages from ../*deb
```

---

### Post by Elador0 on 2012-11-14
Thanks very much for this short guide :-) 

This has already cost me several hours to find what's going on and why my CMake project won't compile anymore in Linux, just to find out that some ubuntu/debian package manager had the funny idea to drop the hdf5_cpp library......... what a nice idea. 

I ended up just adding the debian experimental repo, didn't work (no key found ... something), then I just downloaded the .deb's from [http://packages.debian.org/experimental/](http://packages.debian.org/experimental/). 

Seems to work, but somewhere my software still crashes. But I guess that's not hdf5's fault. Going to find out now. I think I try your way of compiling hdf5.

---

