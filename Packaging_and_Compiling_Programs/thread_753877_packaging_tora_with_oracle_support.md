---
title: "packaging tora with oracle support"
date: 2008-04-13
forum: Packaging and Compiling Programs
---

### Post by alexfittyfives on 2008-04-13
Hi people,

I'm trying to create a deb package of TOra using the oracle libs supplied in oracle-xe-client from the oracle repos.

I download the source package and change the config options in debian/rules to:
```

--prefix=/usr --with-oracle=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server --without-rpath --disable-new-check --without-kde --enable-libsuffix=

```

I also set $ORACLE_HOME to /usr/lib/oracle/xe/app/oracle/product/10.2.0/server

if I then do a debian/rules binary, it dies on the dh_shlibdeps stage with:
```
dpkg-shlibdeps: failure: no dependency information found for /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib/libclntsh.so.10.1 (used by debian/tora/usr/bin/tora).
dh_shlibdeps: command returned error code 512
make: *** [binary-arch] Error 1

```

If I comment out the dh_shlibdeps step in the binary-arch target of debian/rules, it compiles and creates the package. If I install it, I've got TOra with oracle support!

Is there a way to skip the dh_shlibdeps step without resorting to such a hack?

---

### Post by alexfittyfives on 2008-04-15
I've concluded that skipping the dh_shlibdeps step is ok based on [this rather good article]("http://www.debian-administration.org/articles/529").

I've attempted write a [howto]("http://www.scrambledchannel.org/2008/04/14/oracle-and-tora-on-ubuntu-hardy-2/") that some may find useful. Let me know if you find any mistakes!

Cheers,
Al

---

### Post by badelf on 2008-12-17
> **alexfittyfives said:**
> I've concluded that skipping the dh_shlibdeps step is ok based on [this rather good article]("http://www.debian-administration.org/articles/529").

I've attempted write a [howto]("http://www.scrambledchannel.org/2008/04/14/oracle-and-tora-on-ubuntu-hardy-2/") that some may find useful. Let me know if you find any mistakes!

Cheers,
Al

I also use the full oracle client because I need to compile other C programs that don't use OCI. This is on Ubuntu Intrepid.

I'm using "debian/rules binary" to build a package in /usr/src for Tora (based on instructions from the wiki: [https://help.ubuntu.com/community/HowToBuildToraWithOracle](https://help.ubuntu.com/community/HowToBuildToraWithOracle) . And in the rules file, I set the configure line:
--prefix=/usr/local --with-oracle=/home/oracle/oracle/product/10.2.0/db_1 --without-rpath --disable-new-check --without-kde --enable-libsuffix=

Of course it fails at dh_shlibdeps. But when the compile succeeds to that point, then I just change that line in the rules file to 
"dh_shlibdeps -- --ignore-missing-info".

---

