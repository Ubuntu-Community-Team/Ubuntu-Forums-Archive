---
title: "Tortured by Packaging"
date: 2010-08-04
forum: Packaging and Compiling Programs
---

### Post by babzog on 2010-08-04
Yeah, I'm a noob when it comes to packaging.  I've skimmed the debian maintainer's guide (big doc!) and googled endlessly over the last couple of days to sort out what various error messages mean and I THINK I've made some headway, but it's still not working.  I've spent a day and half on this so far - from reviewing the maintainer's guide, I had an idea that making debian  packages was complex but I never fully appreciated just how complex it actually is!

Basically, what I want to do is this.  The gsoap package is horribly out of date (2.7.9 vs the latest which is 2.7.17).  We use the latest, so I need it.  I'll compile and install if I need to (I'm this >< close to just giving up and going that route as my boss is giving me the "Why are you spending time on this?" eyeballs) but would rather have a package to manage this since gsoap is updated fairly frequently.

The build makes 2 binaries (soapcpp2 and wsdl2h) plus I'm using a patch (shamelessly stolen from fedora's package) to generate shared libraries.  I've also got another patch file with some fixes from the gsoap website.  So, two patchfiles to manage.  That was the easy part - I've got those sorted out using dpatch.

I foresee making two deb's - one for the lib and binaries and another for the development files.  I'm open to shrinking that back to just one for simplicity's sake.

What I did to kick all of this off was the following.  

- Download the gsoap-2.7.17.zip file from SF. 
- Unpack (it creates a dir gsoap-2.7, which I renamed to gsoap-2.7.17)
- Set DEBEMAIL and DEBFULLNAME
- cd gsoap-2.7.17 and run:
   dh_make -l -p "gsoap_2.7.17" --dpatch -c gpl2 --createorig
- It made the debian dir but complained thus:

```
Make sure you change the package name from gsoapBROKEN to something
else, such as gsoap1 in the debian/control file.
```

I then edited the debian/control file thus:

```
Source: gsoap
Priority: optional
Maintainer: xxx
Build-Depends: dpatch, debhelper (>= 7), autotools-dev
Standards-Version: 3.8.3
Section: libs
Homepage: http://gsoap2.sourceforge.net

Package: gsoap-dev
Section: libdevel
Architecture: any
Depends: gsoap (= ${binary:Version})
Description: gSoap development libraries, header files and documentation.
 Contains the headers and libraries for gsoap.

Package: gsoap
Section: libs
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: SOAP stub and skeleton compiler for C and C++
 The gSOAP toolkit provides a unique SOAP-to-C/C++ language
 binding for the development of SOAP Web Services and clients.
```

(Yes, I grabbed the descriptive text from the old gsoap package.)  I just renamed the 'gsoapBROKEN' references to 'gsoap' as that's what I want the package to be called.  Don't know why it figured they were broken.

Next, I removed a bunch of unused stuff: *.ex *.EX.  I might add some back later but it was just overload for now.  I renamed 'gsoap1.dirs' to 'gsoap.dirs' and ditto for 'gsoap1.install'.

The rules file though... it's empty!  Running 'fakeroot debian/rules build' gives:

```
> fakeroot debian/rules build
dh  build
   dh_testdir
   dh_auto_configure
configure: WARNING: unrecognized options: --disable-maintainer-mode
...
checking for disable openssl in library... no
configure: creating ./config.status
config.status: creating Makefile
...
config.status: creating gsoap/samples/wsse/Makefile
config.status: creating gsoap/samples/xml-rpc/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
configure: WARNING: unrecognized options: --disable-maintainer-mode
   dh_auto_build
...
   dh_auto_test
...
> 
```

Code is built.  Running the command above but using the 'binary' target gives me a build but then quits with:

```

make[1]: Leaving directory `/usr/local/src/gsoap-2.7.17'
   dh_install
dh_install: gsoap-dev missing files (usr/lib/lib*.so), aborting
make: *** [binary] Error 255

```

So I tried to make my own rules file:

```
export DH_VERBOSE=1

DEB_CONFIGURE_PREFIX = /usr
DEB_CONFIGURE_EXTRA_FLAGS = --disable-static

%:
    dh  $@

patch:
    dpatch apply-all
    autoreconf --install --force

unpatch:
    dpatch deapply-all

build: patch
    make

install: build
    dh_install --sourcedir=debian/tmp

binary: build install

clean: unpatch
    -make clean

```


I've noticed the VERBOSE flag doesn't seem to do much.  Aside that, the source is patched properly, the configure command is somehow run with the right options (I don't profess to fully understand the configure/make process even after a few years of simply using it).  Looks like a make command somehow kicks off a status check which then runs configure.... Anyway, the output:

```
> fakeroot debian/rules build
dpatch apply-all
autoreconf --install --force
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./config.guess'
libtoolize: copying file `./config.sub'
libtoolize: copying file `./install-sh'
libtoolize: copying file `./ltmain.sh'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
libtoolize: `AC_PROG_RANLIB' is rendered obsolete by `LT_INIT'
make
make[1]: Entering directory `/usr/local/src/gsoap-2.7.17'
/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash ./configure --build=i486-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/gsoap --disable-maintainer-mode --disable-dependency-tracking build_alias=i486-linux-gnu --no-create --no-recursion
configure: WARNING: unrecognized options: --disable-maintainer-mode
...
checking for disable openssl in library... no
configure: creating ./config.status
configure: WARNING: unrecognized options: --disable-maintainer-mode
 /bin/bash ./config.status
config.status: creating Makefile
...
>

```

Looks like it built okay.  Now, when I run the command with the binary target, it runs through the whole patch/configure/make process again.  This time, the install target gets run but it croaks with:

```
dh_install --sourcedir=debian/tmp
    cp -a debian/tmp/usr/include/stdsoap2.h debian/gsoap-dev//usr/include/
[SIZE=4]**dh_install: gsoap-dev missing files (usr/lib/lib*.a), aborting**[/SIZE]
make: *** [install] Error 255

```

I've not yet found any explanation for the highlighted error message or what to do about it.  The --sourcedir line I gleaned from the dh_install script itself, but as can be seen, it didn't help.  I thought it was supposed to point to the location of the libs (under debian/tmp) but it seems to still want them elsewhere, as if they were actually installed.

I'm hoping that someone can spot what I've done to make this into a dog's breakfast and can offer some advice to fix up my rules file (I'm sure that's both the cause and cure for my woes) to make this finally come together.

---

### Post by babzog on 2010-08-05
Wow.. 56 views and noone has any thoughts as to what is going on here?

Maybe a different approach then.  Simplified - no separate project-dev package as that just seems out of reach at the moment (I'm sure it's possible, right now, I'd just like to get to the point where I can build a deb at all).

So, can anyone help me to write a debian/rules file that will:

1. Patch some files, including some Makefile.am files?

2. Run: **autoreconf --install --force**

3. Run a custom configure command: **./configure --disable-static --prefix=/usr**

4. Build (and clean) the project.

5. Most important: Generate the deb file.

I've googled for "simple guides", ala Making Debian Packages for Dummies to making not-so-simple deb packages (ie: those which contain a couple of binaries, some shared libs, some headers, etc.) and have found nothing.  :(

---

### Post by SevenMachines on 2010-08-06
Generally I would have said that getting the old gsoap package and updating its packaging for the new version would have been the better way 

$ apt-get source gsoap

I'd certainly look it over to see how they've done it if I were you, you should be able to copy most of it.

but to try and answer your questions, using cdbs.

1. Generally newer packages use the quilt patching system but if you're using dpatch, patches in debian/patches either way and add

/usr/share/cdbs/1/rules/dpatch.mk

to debian/rules

2. You'll need 
$ sudo apt-get install dh-autoreconf
and 
include /usr/share/cdbs/1/rules/autoreconf.mk
in debian/rules, i think -f -i options are implicit anyway
Only do this if you really need autoreconf though, chances are you can leave it out

3. add include /usr/share/cdbs/1/class/autotools.mk and set custom configure options if you need with
DEB_CONFIGURE_EXTRA_FLAGS := --some-option

note you shouldnt need /usr prefix, cdbs does a lot of sane things in the background

4. if you have a make file then 
include /usr/share/cdbs/1/class/makefile.mk
takes care of all the building issues

5. cross your fingers!
$ debuild -b -us -uc

debian/rules:
> #!/usr/bin/make -f

DEB_CONFIGURE_EXTRA_FLAGS := --disable-static 
/usr/share/cdbs/1/rules/dpatch.mk
include /usr/share/cdbs/1/rules/autoreconf.mk
include /usr/share/cdbs/1/class/autotools.mk
include /usr/share/cdbs/1/class/makefile.mk

---

