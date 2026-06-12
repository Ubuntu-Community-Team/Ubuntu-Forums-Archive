---
title: "Build fails at ppa with missing gnome-doc-utils"
date: 2009-01-24
forum: Packaging and Compiling Programs
---

### Post by amrlima on 2009-01-24
Hi all,

I'm trying to build a gtranslator package in ppa. I've uploaded the source to my ppa but the buil fails with:

```
configure: error: gnome-doc-utils >= 0.3.2 not found
make: *** [config.status] Error 1
dpkg-buildpackage: failure: debian/rules build gave error exit status 2

```

The package builds and installs fine in my computer with debuild. Anyone has a clue what I'm missing here?

Thanks in advance!

---

### Post by chrisccoulson on 2009-01-24
You need to specify gnome-doc-utils as a build-depends in your control file. I just had a look at it and you only have debhelper (>= 7), autotools-dev and cdbs. Without it, the build dependencies won't get installed in the build environment, which is why it fails to configure.

It works locally on your machine with debuild because you probably have the dependencies installed already. This is exactly why you should always build packages in a clean-room environment (such as with PBuilder), to catch errors like this.

---

### Post by amrlima on 2009-01-24
> **chrisccoulson said:**
> You need to specify gnome-doc-utils as a build-depends in your control file. I just had a look at it and you only have debhelper (>= 7), autotools-dev and cdbs. Without it, the build dependencies won't get installed in the build environment, which is why it fails to configure.

It works locally on your machine with debuild because you probably have the dependencies installed already. This is exactly why you should always build packages in a clean-room environment (such as with PBuilder), to catch errors like this.

Yes, you're rigth. I'll check it out and retry. I'm not using pbuilber just because I'm using a 3G modem internet connection with limited bandwidth so setting up pbuilder would eat much of my available bandwidth.

I'm still making the first steps in packaging so I'll make lots of mistakes :)

Thanks!

---

### Post by chrisccoulson on 2009-01-24
Understandable about PBuilder. But it does cache packages once they've been used in a build once.

Having a quick look at your packages configure.ac, the extra build-depends should probably be "gettext (>= 0.17.0), libdb4.3-dev (>= 4.3), gnome-doc-utils, libgconf2-dev (>= 2.18.0), libglade2-dev (>= 2.6.0), libgtksourceview2.0-dev (>= 2.4.0), libglib2.0-dev (>= 2.15.5), libgdl-1-dev (>= 0.6.0)".

The following look optional depending on what configure flags you pass and what features you want: "libgtkspell-dev (>= 2.0.2), libsoup2.4-dev (>= 2.4.0), gnome-utils, libgucharmap-dev (>= 2.23.0)"

---

### Post by amrlima on 2009-01-24
> **chrisccoulson said:**
> Understandable about PBuilder. But it does cache packages once they've been used in a build once.

Having a quick look at your packages configure.ac, the extra build-depends should probably be "gettext (>= 0.17.0), libdb4.3-dev (>= 4.3), gnome-doc-utils, libgconf2-dev (>= 2.18.0), libglade2-dev (>= 2.6.0), libgtksourceview2.0-dev (>= 2.4.0), libglib2.0-dev (>= 2.15.5), libgdl-1-dev (>= 0.6.0)".

The following look optional depending on what configure flags you pass and what features you want: "libgtkspell-dev (>= 2.0.2), libsoup2.4-dev (>= 2.4.0), gnome-utils, libgucharmap-dev (>= 2.23.0)"

I was just looking at them now, but since the names of dependencies in configure.ac are a little different from the ones in Ubuntu reps I wasn't shure about some.

2 more questions please:
- Can I create the package WITHOUT running autogen.sh?
- How to I set the option dependencies? Those are for plugins (quite useful ones :) ). I can't seem to find this on documentation so far.

Thanks a lot!

---

### Post by chrisccoulson on 2009-01-24
You shouldn't need to run the autogen.sh script, as the build environment for your source package already looks complete.

To specify configure flags with CDBS, just add a line like this in your debian/rules (replacing the features with whatever you want to enable/disable:
```
DEB_CONFIGURE_EXTRA_FLAGS := --with-*feature* --enable-*feature*
```

---

### Post by amrlima on 2009-01-24
Thanks, I'll check it out.

Anyway I'm considering configuring a pbuilder environment since its much faster to test if the package builds correctly.

---

### Post by amrlima on 2009-01-24
It builds :D!

Its still building now, I'll test if all plugins where activated as well.

---

