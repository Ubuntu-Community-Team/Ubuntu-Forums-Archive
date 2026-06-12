---
title: "Compiling and packaging a new version of a library"
date: 2006-08-03
forum: Packaging and Compiling Programs
---

### Post by thomas.hood on 2006-08-03
Hello packaging gurus,

Firstly just to say I've ploughed through the following, so I'm not being lazy :-)
[https://help.ubuntu.com/ubuntu/packagingguide/C/index.html]("https://help.ubuntu.com/ubuntu/packagingguide/C/index.html")
[http://www.tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/]("http://www.tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/")
[http://www.debian.org/doc/maint-guide/]("http://www.debian.org/doc/maint-guide/")

I'm somewhat wiser, but pretty confused. What I want to do is relatively simple but I'm unsure of how to proceed. I need to build some .debs of a selection of libraries (libjack, jackd, libraw1394, libiec61883, libavc1394) that are already in the dapper binary repositories, but from the latest SVN versions.

The libraries work fine by apt-get install'ing the binary repository versions and then compiling the SVN sources and installing over the top like so:

$ autoreconf -f -i -s
$ ./configure --prefix=/usr
$ make
$ sudo make install

I do this so that apt knows these programs are installed for other apps that depend on them.

Obviously making debs would be a far more sensible approach, not least because there seems to be some odd naming convention stuff going on. (i.e. all the libjack stuff gets called libjack0.100.0-0.so etc, whereas installing from source just calls the files libjack.so etc.)

The sensible approach would appear to be to copy the method that the package maintainers used when building these libraries and just use the SVN source and update the version numbers in the control file. BUT... I can't figure out how to do this as there don't seem to be any source packages for the aforementioned libraries, and I'm unlikely to come up with a correct (matching) set of build rules etc. on my own...

If someone has gone to the trouble of creating binary debs, why don't the put the source packages up? As I understand it, you have to create the source packages first anyhow... ](*,)

Am I missing something really obvious here? 

Thanks,

Tom

P.S. Specifically I need [Freebob]("http://freebob.sourceforge.net/index.php/Main_Page") which is a Firewire soundcard driver library which utilises the Jack audio connection kit.

P.P.S. I know quite a few people are interested in having a set of ubuntu debs (which I'm happy to host) for this, so you'd be helping the multitude :-)

---

### Post by quilted on 2006-08-05
> **thomas.hood said:**
> 
P.P.S. I know quite a few people are interested in having a set of ubuntu debs (which I'm happy to host) for this, so you'd be helping the multitude :-)

I am one of them!

---

### Post by mlind on 2006-08-07
I can help you create .deb package from jack svn, but you should get pretty up-to-date source package from debian unstable and just build that.

If I need to package a svn build of certain application, I check for existing  source package from Ubuntu and Debian. If it's available, I usually take the newest one (if it's from Debian like usual, Ubuntu specific patches might be important, so Ubuntu package's should be reviewed with care).

Then I check out the cvs/svn module and use uupdate (or simply patch) to apply existing packaging information. It's important to check source's ChangeLog too, so you know if some parts of the packaging information needs to be updated (new dependencies, removed files, etc..).

Then I try to build package in a chroot jail until it builds succesfully (and installs without problems). For svn/cvs builds, I usually add rule that invokes autogen.sh/autoreconf automatically, so that entire package can be built using just debian/rules build target.

---

### Post by bcw on 2007-10-01
> **thomas.hood said:**
> 
I need to build some .debs of a selection of libraries (libjack, jackd, libraw1394, libiec61883, libavc1394) that are already in the dapper binary repositories, but from the latest SVN versions.

checkinstall will build a .deb from a 'make install' type package.  It's in the Universe repositories on feisty.

Cheers,
Bret

---

