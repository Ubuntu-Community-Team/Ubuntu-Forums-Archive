---
title: "dpkg-genchanges: failure: cannot read files list file: No such file or directory"
date: 2008-04-20
forum: Packaging and Compiling Programs
---

### Post by gregoryg on 2008-04-20
I'm working on a custom usplash theme for a West Virginia University Ubuntu variant. I grabbed the source for the usplash-theme-ubuntu package and used it as the source for my new package.

I can build the source package, but the binary package fails. Here is the output of dpkg-buildpackage -rfakeroot

> 
dpkg-buildpackage: source package is usplash-theme-loud
dpkg-buildpackage: source version is 5.0.0
dpkg-buildpackage: source changed by Gregory Gay (Signature) <gregoryg@csee.wvu.edu>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 5.0.0
 fakeroot debian/rules clean
dh_testdir
rm -f build-stamp
/usr/bin/make clean
make[1]: Entering directory `/home/greg/svns/lgutsy/lgutsy/usplash-theme-loud'
rm -f *.png.c *.bdf.c *.c.o *.so
make[1]: Leaving directory `/home/greg/svns/lgutsy/lgutsy/usplash-theme-loud'
dh_clean
 dpkg-source -b usplash-theme-loud
dpkg-source: warning: source directory './usplash-theme-loud' is not <sourcepackage>-<upstreamversion> 'usplash-theme-loud-5.0.0'
dpkg-source: building usplash-theme-loud in usplash-theme-loud_5.0.0.tar.gz
dpkg-source: building usplash-theme-loud in usplash-theme-loud_5.0.0.dsc
 debian/rules build
dh_testdir
/usr/bin/make
make[1]: Entering directory `/home/greg/svns/lgutsy/lgutsy/usplash-theme-loud'
make[1]: Circular throbber_back.png <- throbber_back.png.c dependency dropped.
pngtousplash throbber_back.png > throbber_back.png.c
gcc  -g -Wall -fPIC -o throbber_back.png.c.o -c throbber_back.png.c
make[1]: Circular throbber_back_16.png <- throbber_back_16.png.c dependency dropped.
pngtousplash throbber_back_16.png > throbber_back_16.png.c
gcc  -g -Wall -fPIC -o throbber_back_16.png.c.o -c throbber_back_16.png.c
make[1]: Circular throbber_fore.png <- throbber_fore.png.c dependency dropped.
pngtousplash throbber_fore.png > throbber_fore.png.c
gcc  -g -Wall -fPIC -o throbber_fore.png.c.o -c throbber_fore.png.c
make[1]: Circular throbber_fore_16.png <- throbber_fore_16.png.c dependency dropped.
pngtousplash throbber_fore_16.png > throbber_fore_16.png.c
gcc  -g -Wall -fPIC -o throbber_fore_16.png.c.o -c throbber_fore_16.png.c
make[1]: Circular usplash_1024_768.png <- usplash_1024_768.png.c dependency dropped.
pngtousplash usplash_1024_768.png > usplash_1024_768.png.c
gcc  -g -Wall -fPIC -o usplash_1024_768.png.c.o -c usplash_1024_768.png.c
make[1]: Circular usplash_1365_768_scaled.png <- usplash_1365_768_scaled.png.c dependency dropped.
pngtousplash usplash_1365_768_scaled.png > usplash_1365_768_scaled.png.c
gcc  -g -Wall -fPIC -o usplash_1365_768_scaled.png.c.o -c usplash_1365_768_scaled.png.c
make[1]: Circular usplash_800_600.png <- usplash_800_600.png.c dependency dropped.
pngtousplash usplash_800_600.png > usplash_800_600.png.c
gcc  -g -Wall -fPIC -o usplash_800_600.png.c.o -c usplash_800_600.png.c
make[1]: Circular usplash_640_400.png <- usplash_640_400.png.c dependency dropped.
pngtousplash usplash_640_400.png > usplash_640_400.png.c
gcc  -g -Wall -fPIC -o usplash_640_400.png.c.o -c usplash_640_400.png.c
make[1]: Circular usplash_640_480.png <- usplash_640_480.png.c dependency dropped.
pngtousplash usplash_640_480.png > usplash_640_480.png.c
gcc  -g -Wall -fPIC -o usplash_640_480.png.c.o -c usplash_640_480.png.c
gcc  -g -Wall -fPIC -o usplash-theme-loud.c.o -c usplash-theme-loud.c
gcc  -g -Wall -fPIC -shared -o usplash-theme-loud.so throbber_back.png.c.o throbber_back_16.png.c.o throbber_fore.png.c.o throbber_fore_16.png.c.o usplash_1024_768.png.c.o usplash_1365_768_scaled.png.c.o usplash_800_600.png.c.o usplash_640_400.png.c.o usplash_640_480.png.c.o usplash-theme-loud.c.o
rm usplash_1024_768.png.c usplash_1365_768_scaled.png.c throbber_fore_16.png.c throbber_back.png.c usplash_640_480.png.c usplash_640_400.png.c throbber_back_16.png.c throbber_fore.png.c usplash_800_600.png.c
make[1]: Leaving directory `/home/greg/svns/lgutsy/lgutsy/usplash-theme-loud'
touch build-stamp
 fakeroot debian/rules binary
dh_testdir
dh_testdir: I have no package to build
dh_testroot
dh_clean -k
dh_clean: I have no package to build
dh_installdirs
dh_installdirs: I have no package to build
/usr/bin/make install DESTDIR=/home/greg/svns/lgutsy/lgutsy/usplash-theme-loud/debian/usplash-theme-loud
make[1]: Entering directory `/home/greg/svns/lgutsy/lgutsy/usplash-theme-loud'
/usr/bin/install -c -d /home/greg/svns/lgutsy/lgutsy/usplash-theme-loud/debian/usplash-theme-loud/usr/lib/usplash
/usr/bin/install -c -m 755 usplash-theme-loud.so /home/greg/svns/lgutsy/lgutsy/usplash-theme-loud/debian/usplash-theme-loud/usr/lib/usplash/usplash-theme-loud.so
make[1]: Leaving directory `/home/greg/svns/lgutsy/lgutsy/usplash-theme-loud'
dh_testdir
dh_testdir: I have no package to build
dh_testroot
dh_installchangelogs
dh_installchangelogs: I have no package to build
dh_installdocs
dh_installdocs: I have no package to build
dh_installman
dh_installman: I have no package to build
dh_link
dh_link: I have no package to build
dh_strip
dh_strip: I have no package to build
dh_compress
dh_compress: I have no package to build
dh_fixperms
dh_fixperms: I have no package to build
dh_installdeb
dh_installdeb: I have no package to build
dh_shlibdeps
dh_shlibdeps: I have no package to build
dh_gencontrol
dh_gencontrol: I have no package to build
dh_md5sums
dh_md5sums: I have no package to build
dh_builddeb
dh_builddeb: I have no package to build
 signfile usplash-theme-loud_5.0.0.dsc

You need a passphrase to unlock the secret key for
user: "Gregory Gay (Signature) <gregoryg@csee.wvu.edu>"
1024-bit DSA key, ID 28A67EE2, created 2007-09-20

                  
 dpkg-genchanges
dpkg-genchanges: failure: cannot read files list file: No such file or directory



Here is my rules file:

> 
#!/usr/bin/make -f

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

export DH_OPTIONS

CFLAGS = -g -Wall

# Disable optimisations if noopt found in $DEB_BUILD_OPTIONS
ifneq (,$(findstring noopt,$(DEB_BUILD_OPTIONS)))
        CFLAGS += -O0
else
        CFLAGS += -Os
endif

# Build the package
build: build-stamp
build-stamp:
        dh_testdir
        $(MAKE)
        touch $@

# Install files
install: build
        dh_testdir
        dh_testroot
        dh_clean -k
        dh_installdirs
        $(MAKE) install DESTDIR=$(CURDIR)/debian/usplash-theme-loud

binary: binary-indep binary-arch

# Build architecture-independent files here.
binary-indep:
# We have nothing to do by default.

# Build architecture-dependent files here.
binary-arch: DH_OPTIONS=-a
binary-arch: build install
        dh_testdir
        dh_testroot
        dh_installchangelogs
        dh_installdocs
        dh_installman
        dh_link
        dh_strip
        dh_compress
        dh_fixperms
        dh_installdeb
        dh_shlibdeps
        dh_gencontrol
        dh_md5sums
        dh_builddeb


# Clean up the mess we made
clean:
        dh_testdir
        rm -f build-stamp
        -$(MAKE) clean
        dh_clean

.PHONY: build install binary-indep binary-arch binary clean


Can anybody help out? Thanks!

---

### Post by DexterLB on 2009-11-02
Same error here.
rules: [http://pastebin.com/m772a1040](http://pastebin.com/m772a1040)
control: [http://pastebin.com/mbebecd0](http://pastebin.com/mbebecd0)
changelog: [http://pastebin.com/m42a68215](http://pastebin.com/m42a68215)

anybody help?

---

