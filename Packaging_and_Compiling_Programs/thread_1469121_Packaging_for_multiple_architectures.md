---
title: "Packaging for multiple architectures"
date: 2010-05-01
forum: Packaging and Compiling Programs
---

### Post by TheForkOfJustice on 2010-05-01
I'm trying to make a i386 version of a metapackage but no matter what I write in the 'Architecture' field the DEB is always made with my system's architecture (amd64).

What steps do I have to take to be able to make DEBs for amd64, i386, or any other architecture on an amd64 system?

On top of that, I often see packages with 'all' listed as their architecture but when I try to make an 'all' entry in my repository (using reprepro) I get an error. Why does 'all' seem to be valid when packaging but not in repositories (or at least reprepro)?

---

### Post by SevenMachines on 2010-05-02
the Architecture field in the control file is information about the package, 'all' says that the package is architecture independent, 'any' means its architecture dependent but builds on all platforms, 'i386' would mean that your package is meant to be built on only that platform. [See debian policy for more info on this]("http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Architecture")

To actually build a package for a different architecture you can pass the -a<arch> option to debuild (or dpkg-buildpackage). for example
$debuild -ai386 -b -us -uc 
would build the binaries (unsigned) for i386 on an amd64 system, assuming you had all the necessary i386 libraries installed

A good way to build packages on a range of different platforms is to use pbuilder, or pbuilder-dist (from the ubuntu-dev-tools package). Using this you can easily create a chroot build environment for each platform you want to build on

---

### Post by TheForkOfJustice on 2010-05-03
Ah, so the package must be built on the correct arch and the control file has no real bearing on the process?

How do the 'all' and 'any' options work then since they aren't archs?

Since I'm making a metapackage, will I be stuck using equivs-build (not that it was a problem to begin with).

On a further note, it is possible to uninstall packages with a metapackage?  Perhaps by including a postinst script?

---

### Post by andrewsomething on 2010-05-03
> **TheForkOfJustice said:**
> Ah, so the package must be built on the correct arch and the control file has no real bearing on the process?

How do the 'all' and 'any' options work then since they aren't archs?

Well, the package must be built on the correct arch and the control file ***does have*** a bearing on the process.

```
Architecture: all
```

This means that the package is architecture independent. So it doesn't matter what architecture it is built on, it can run on all architectures. Chances are you're meta-package is Architecture: all.

The resulting deb will be something like: foo_2.5-1_all.deb

```
Architecture: any
```

This means its architecture dependent. So it does matter what arch it is built on. The user must install a version built on the same arch that they are running. It also means that the package should build on any arch that it is attempted. So when you upload a package that is arch: any, it will be built on all availiable archs.

The resulting debs will be something like: foo_2.5-1_i386.deb, foo_2.5-1_amd64.deb, foo_2.5-1_sparc.deb, and so on...

```
Architecture: i386 amd64 powerpc
```

This means its architecture dependent, but that it will only successfully build on i386, amd64, and powerpc. So when you upload this package, it will only build on those archs, and the buildds will not bother trying to compile it on alpha, sparc, mipsel, ect..

Again, the debs will be something like: foo_2.5-1_i386.deb and foo_2.5-1_amd64.deb

Hope that makes sense....

---

### Post by Pigeon. on 2013-04-12
Apologies for bumping an old thread but since it is currently the fourth result on google for *dpkg-buildpackage "-ai386"* and the reason I was googling that is to try and find out why it doesn't work, I figured it would be helpful to add to the thread having found a way to make it work.

Do not be discouraged by reading *the package must be built on the correct arch* in the above - it is not true, at least not for the case of building i386 packages on x86_64.

This bit...

[i]To actually build a package for a different architecture you can pass the -a<arch> option to debuild (or dpkg-buildpackage). for example
 $debuild -ai386 -b -us -uc 
 would build the binaries (unsigned) for i386 on an amd64 system, assuming you had all the necessary i386 libraries installed[/i]

...is wrong (at least, it is wrong for dpkg-buildpackage; I have not tried debuild). It *appears* to work, as in it creates .debs named *blahblahblah*_i386.deb, but all it has really achieved is to get dpkg-buildpackage to lie - the files inside those .debs are still built for x86_64. 

The only indication that something may have gone wrong is the warning *dpkg-architecture: warning: specified GNU system type i486-linux-gnu does not match gcc system type x86_64-linux-gnu, try setting a correct CC environment variable* - which is right at the start of the output, and will most likely scroll off the top before you've even had a chance to notice it - and in any case the next line is *dpkg-buildpackage: host architecture i386* which will make you think it's all OK anyway... when in fact it is not.

The solution I found was to set CC as follows:

**export CC="gcc -m32 -Wl,-melf_i386"**

before invoking dpkg-buildpackage. This translates as "invoke gcc with the flag -m32 to tell it to compile in 32-bit mode, and also pass -melf_i386 to ld to tell ld to link for i386". The output from dpkg-buildpackage still includes the same warnings, but this time it *does* build i386 .debs with i386 files inside.

Note that while this does work in my specific case (building a 32-bit version of libnl on x86_64) it may not work generally; it relies on the source package's build scripts and makefiles both honouring CC, and invoking ld via gcc instead of directly.

If ld is invoked directly the solution would probably be (untested):

export CC="gcc -m32"
export LD="ld -melf_i386"

If CC/LD are not honoured this may work:

export CFLAGS="-m32 -Wl,-melf_i386"

or

export CFLAGS="-m32"
export LDFLAGS="-melf_i386"

...but it may not; for example it may break the configure script and cause it to report that the compiler does not work. In that case probably the easiest solution (for suitable values of "easiest") would be to edit the scripts/makefiles so that they do honour CC/LD.

The official Debian recommendation is to create a chroot containing a complete 32-bit environment and build all your 32-bit packages inside that. This makes sense if you are building 32-bit packages all the time, but it is massive overkill to go to all that hassle just to build the odd one now and then.

---

### Post by howefield on 2013-04-12
Old thread closed.

---

