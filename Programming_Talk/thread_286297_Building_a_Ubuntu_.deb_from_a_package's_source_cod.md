---
title: "Building a Ubuntu .deb from a package's source code"
date: 2006-10-27
forum: Programming Talk
---

### Post by wolphin on 2006-10-27
Hi,

I'm trying to build a .deb from a package's source code using dpkg-buildpackage, but I get the following error: "dpkg-checkbuilddeps: error: syntax error in control file debian/control at line 12: line with unknown format (not field-colon-value)" - any ideas? My long description (line 12) has no invalid characters, as far as I am aware, so I'm not sure why it is failing. The only non-alphabetic characters the long description has are -(),. so I don't know why it's not working.

Are any of those characters illegal?

Thank you.

---

### Post by gborzi on 2006-10-27
Please post your debian/control file, so that I can check what's wrong at line 12.

---

### Post by wolphin on 2006-10-27
This is it:
> dsniff is a collection of tools for network auditing and penetration testing. dsniff, filesnarf, mailsnarf, msgsnarf, urlsnarf, and webspy passively monitor a network for interesting data (passwords, e-mail, files, etc.). arpspoof, dnsspoof, and macof facilitate the interception of network traffic normally unavailable to an attacker (e.g, due to layer-2 switching). sshmitm and webmitm implement active monkey-in-the-middle attacks against redirected SSH and HTTPS sessions by exploiting weak bindings in ad-hoc PKI.
I'm trying to make a dsniff .deb, in case it wasn't evident :p Thanks for the help.

---

### Post by gborzi on 2006-10-27
The long comment lines must start with a space, not a letter. Good sniffing !

---

### Post by wolphin on 2006-10-27
Ah! Thank you! :D

---

### Post by wolphin on 2006-10-27
Hmm... Now it's complaining about something else (although what you said worked ;)):
> max@sandbox:~/Desktop/dsniff/dsniff-2.3$ dpkg-buildpackage -b -uc -rfakeroot
dpkg-buildpackage: source package is dsniff
dpkg-buildpackage: source version is 2.3-1
dpkg-buildpackage: source changed by Max <max@thetazzone.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.3-1
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/max/Desktop/dsniff/dsniff-2.3'
make[1]: *** No rule to make target `distclean'. Stop.
make[1]: Leaving directory `/home/max/Desktop/dsniff/dsniff-2.3'
make: [clean] Error 2 (ignored)
cp -f /usr/share/misc/config.sub config.sub
cp -f /usr/share/misc/config.guess config.guess
dh_clean 
 debian/rules build
dh_testdir
# Add here commands to configure the package.
./configure --host=i486-linux-gnu --build=i486-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info CFLAGS="-Wall -g -O2" LDFLAGS="-Wl,-z,defs"
configure: warning: CFLAGS=-Wall -g -O2: invalid host type
configure: warning: LDFLAGS=-Wl,-z,defs: invalid host type
configure: error: can only configure for one host and one target at a time
make: *** [config.status] Error 1
I'm not very experienced at building .debs, so I'm not sure what the problem is.. What do those configure warnings/errors mean, and is it possible to fix them? (It also complained about there being no distclean rule, but that doesn't seem to be a critical problem).

Thanks again :)

---

### Post by gborzi on 2006-10-27
Have you tried to compile this software without making a .deb ? If so, was the compilation successful ? One thing that can be wrong are the CFLAGS and LDFLAGS at the end of the configure command. Generally they are put before the ./configure command, e.g. > CFLAGS="$(CFLAGS)" LDFLAGS="$(LDFLAGS)" ./configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info --sysconfdir=/etc --libdir=\$${prefix}/lib
where I'm assuming you have already defined CFLAGS and LDFLAGS. Or you can use a faster (and dirty) approach > CFLAGS="-Wall -g -O2" LDFLAGS="-Wl,-z,defs" ./configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info --sysconfdir=/etc --libdir=\$${prefix}/lib
Hope this helps.

EDIT: the above commands are to be used in the debian/rules file.

---

### Post by wolphin on 2006-10-27
Thanks a lot, gborzi - I will try that out (and look up what all the flags stand for) as soon as possible!

Cheers!

---

### Post by fakie_flip on 2007-02-17
Have you tried checkinstall or does that not do the same thing as dpkg-buildpackage?

---

### Post by pay on 2007-02-17
I wouldn't recommend checkinstall if you wanted to share you debian file with other computers on your network on the internet.

---

### Post by maddog39 on 2007-02-17
Why bother with the official debian utilities which are a pain, checkinstall is easier and does the same thing. Just run:
```

sudo apt-get install checkinstall

```
To install it. Then to build a debian package, cd to the packages directory and run.
```

sudo checkinstall -D --install=no

```

---

### Post by _Stevie_ on 2008-01-14
thanks, worked perfectly!

---

