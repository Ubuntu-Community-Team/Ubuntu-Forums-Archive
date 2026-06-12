---
title: "Installing/using PyQt4 on Dapper"
date: 2006-08-26
forum: Programming Talk
---

### Post by jkugler on 2006-08-26
OK.  So, after having my request for a PyQt4 backport rejected (for valid reasons; see here: [https://launchpad.net/products/dapper-backports/+bug/57519](https://launchpad.net/products/dapper-backports/+bug/57519) and here: [http://www.ubuntuforums.org/showthread.php?p=1422663](http://www.ubuntuforums.org/showthread.php?p=1422663)).  Also see those threads for why I can't just install PyQt4 straight from Riverbank's source.

I thought I'd live on the dangerous side and try pulling directly from Edgy.  An apt-get of this nature:

```

apt-get install -s python-qt4 python-qt4-gl python-qt4-sql

```

Gives me:

```

The following extra packages will be installed:
  gcc-4.1-base libc6 libc6-dev libc6-i686 libfreetype6 libfreetype6-dev libgcc1 libqt4-core libqt4-debug
  libqt4-debug-dev libqt4-dev libqt4-gui libqt4-qt3support libqt4-sql libstdc++6 linux-libc-dev
  python-elementtree python-kde3 python-numeric python-opengl python-qt3 python-qtext python-sip4
  python-support
Suggested packages:
  glibc-doc manpages-dev python-numeric-tutorial python2.3-tk python2.3-qt3-gl python-qt3-doc libqt3-mt-mysql
  libqt3-mt-odbc libqt3-mt-psql
The following packages will be REMOVED:
  linux-kernel-headers python2.4-kde3 python2.4-numeric python2.4-qt3 python2.4-qtext python2.4-sip4-qt3
The following NEW packages will be installed:
  gcc-4.1-base linux-libc-dev python-elementtree python-opengl python-qt4 python-qt4-gl python-qt4-sql
  python-sip4 python-support
The following packages will be upgraded:
  libc6 libc6-dev libc6-i686 libfreetype6 libfreetype6-dev libgcc1 libqt4-core libqt4-debug libqt4-debug-dev
  libqt4-dev libqt4-gui libqt4-qt3support libqt4-sql libstdc++6 python-kde3 python-numeric python-qt3
  python-qtext

```

Oddly enough, and perhaps thankfully, very little python-related stuff is being upgraded.

Now, some distributions say "Don't pull packages across versions, that is sooooo not supported."  But that was an RPM-based distribution that said that.  Are the dependency trees in .deb's good enough that the above list is really what I need?  Has anyone tried this (and lived)?  Has anyone severely borked their system this way?

I see the libc6, libgcc, and libqt4 upgrades.  Are those really safe?  In other words, if there were binary gotchas, would apt-get being throwing in a whole lot more upgrades?

Any comments or directions would be great. 

j

---

### Post by jdong on 2006-08-26
Do NOT (I repeat, that's NOT, as in N-O-T, as in don't even thing about it) pull binary packages from Edgy to install in Dapper. Edgy has a new compiler and C libraries that are completely incompatible with those of Dapper. You will for sure render your Ubuntu installation unbootable if you do this.


Compile the packages from source.

---

### Post by jkugler on 2006-08-26
> **jdong said:**
> Compile the packages from source.

Well, yeah, but see  [https://launchpad.net/products/dapper-backports/+bug/57519](https://launchpad.net/products/dapper-backports/+bug/57519) as to how well that (didn't) work.  :)

As to the new version of GCC, shouldn't all the new Edgy packages then have a dependency on gcc-4.1-base, or some other meta package that defines the ABI?  Sigh...when, oh when, is C++ going to have an ABI standard.

Ah well...back to the drawing board.

Thanks for the quick reply.

---

### Post by jdong on 2006-08-26
Maybe just ignore the deb packaging system altogether.. Grab source tarballs from the pyqt site and compile/install to /usr/local.

---

### Post by jkugler on 2006-08-26
> **jdong said:**
> Maybe just ignore the deb packaging system altogether.. Grab source tarballs from the pyqt site and compile/install to /usr/local.

Ah, if it were only that simple.  Well, maybe it is.  Maybe you can tell me since you probably know more about this that I do.

Compiling PyQt4 requires Sip4.4.4:

~/src/PyQt-x11-gpl-4.0.1$ python configure.py
Error: This version of PyQt requires SIP v4.4.4 or later

If I make a deb of sip 4.4.5 (via checkinstall) and try to install that, it tells me it's going to overwrite a file belonging to python2.4-sip4-qt3:

```
trying to overwrite `/usr/lib/python2.4/site-packages/sipconfig.py', which is also in package python2.4-sip4-qt3
```

Well, it also looks like it would overwrite /usr/lib/python2.4/site-packages/sip.so as well.  It wouldn't overwrite any of the sip binaries, because the sip4 package itself isn't installed.

I would name my custom compiled version of sip4 'python2.4-sip4-qt3' and call it good, but python2.4-kde3 (as well as -qt3) has a depends that includes this:

```
python2.4-sip4-qt3 (>= 4.3), python2.4-sip4-qt3 (<< 4.4)
```

So, I could call give my package version 4.3.99 and watch sparks fly.  I might just resort to doing that.  I wish the sip4 configure script had an option for a custom prefix or suffix, bit it appears it does not.

I can install the compile job in a custom location, but when the pyqt4 libraries are used, they will probably look in the default location, causing everything to bomb again. Or if I name my package python2.4-sip4-qt3 and install it, I would assume any pyqt3 programs would then bomb.  Currently eric3 and kde-guidance depend on pyqt3/pykde3.  I suppose I could go without both of those for a while. :)

It would appear I've hit a dead end.  At least if I want to do things the elagent way. :)  Maybe doing things the hackish way will still work.

j

---

### Post by jdong on 2006-08-26
:-/ Whatever you do at this point will be pretty hackish.... that's a given. That's also part of the reason I didn't want to do it a la backports, as I explained earlier. It runs the risk of breaking kde-guidance which is definitely a no-no.

---

