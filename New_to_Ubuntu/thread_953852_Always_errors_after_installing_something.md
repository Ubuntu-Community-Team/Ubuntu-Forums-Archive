---
title: "Always errors after installing something"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by MartinDeutschland on 2008-10-20
Hi everybody,
always after using apt-get I get the following error-message:

```
ghc-pkg: dependency X11-1.3.0 doesn't exist (use --force to override)
dpkg: error processing libghc6-hgl-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libghc6-hgl-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It doesn't really disturb me, but I would like to know what it means and what I could do to avoid this message. Thanks,
Martin

---

### Post by cwsnyder on 2008-10-20
In order, this is what I understand of your problems: ```
ghc-pkg: dependency X11-1.3.0 doesn't exist (use --force to override)
``` This complaint is that the package libX11-1.3.0 which the ghc-pkg package depends on is missing.  libX11-1.3.0 is a library of routines for a particular version of the X terminal package.  You can check using apt-get, aptitude or Synaptic to see if the libX11-1.3.0 package is available from one of your approved sources.  If not, and the libX11-1.3.0 package is newer than your existing X terminal package, you can probably get it from one of the Canonical sources.

All of the rest of the errors result from the original missing libX11 library.  As the notes suggest, you can probably force the use of libghc6-hgl-dev by using the --force flag.

---

