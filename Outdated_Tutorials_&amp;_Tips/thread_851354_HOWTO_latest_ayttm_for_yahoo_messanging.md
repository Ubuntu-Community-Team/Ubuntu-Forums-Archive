---
title: "HOWTO: latest ayttm for yahoo messanging"
date: 2008-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Georges on 2008-07-06
Hi

since april 2008, yahoo refuses connections from ayttm (from ubuntu 7.10)
Solution is to install from the official website.
Compiling failed for me, as I did not have the patience to seek which dev packages I need.
So I installed using alien

first get alien:

sudo apt-get install alien

then get the latest ayttm rpm from the official site [https://sourceforge.net/projects/ayttm/](https://sourceforge.net/projects/ayttm/) and convert it to a deb:

sudo alien ayttm-0.5.0-45.i386.rpm

and install that:

sudo dpkg -i ayttm_0.5.0-46_i386.deb

starting ayttm will probably generate a message about not finding a library libjasper-1.701.so.1 which is used for yahoo webcam. I did not test the webcam so I can't tell if it really works. My experience is that it does not.

To get rid of the jasper lib warning, install it:

sudo apt-get install libjasper1

and make a link to simulate the correct version:

sudo ln -s libjasper.so.1 /usr/lib/libjasper-1.701.so.1

Voila, ayttm works again.

Georges

---

### Post by Mark76 on 2008-10-09
It keeps dropping the MSN connection for me. Any ideas how to fix that?

---

### Post by bryanalwright on 2008-10-09
That's working on my YM. Thanks!

---

### Post by Bobrm2 on 2008-10-19
I get pass, down load alien, then attempt to get the rpm, but get an unable to locate the ayttm-0.5.0-45.i386.rmp.

I am cut/paste instead of typing, to eliminate any typos.

All help appreciated.

Bob

---

### Post by Georges on 2008-10-20
> **Bobrm2 said:**
> I get pass, down load alien, then attempt to get the rpm, but get an unable to locate the ayttm-0.5.0-45.i386.rmp.

I am cut/paste instead of typing, to eliminate any typos.

All help appreciated.

Bob

sorry I can't help there, because I'm able to download it.

What I notice that the .deb file has another version than the rpm, After running alien simply look into the current folder for any file created ending with .deb, that's the one to use with dpkg.

Georges

---

### Post by Bobrm2 on 2008-10-20
Georges, 
   I finally realized that "Alien" was a program and not a repository. Everything worked out.

Thanks for your help

Bob

---

### Post by Psumi on 2010-01-23
New Ayttm (0.6.1) can't use alien:

```
~$ sudo alien ayttm-0.6.1-0.src.rpm
error: incorrect format: unknown tag
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/ayttm
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'i386' does not appear in package's architecture list (amd64)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Error 1
find: `ayttm-0.6.1': No such file or directory
```

---

### Post by Psumi on 2010-01-28
And giftwrap can't make a deb of it sadly:

```
collect2: ld returned 1 exit status
make[5]: *** [aim-oscar.la] Error 1
make[5]: Leaving directory `/home/psumi/.giftwrap/ayttm/ayttm-0.6.1/modules/aim-oscar'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/psumi/.giftwrap/ayttm/ayttm-0.6.1/modules/aim-oscar'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/psumi/.giftwrap/ayttm/ayttm-0.6.1/modules'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/psumi/.giftwrap/ayttm/ayttm-0.6.1'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/psumi/.giftwrap/ayttm/ayttm-0.6.1'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

---

