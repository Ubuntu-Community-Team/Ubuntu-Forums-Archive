---
title: "Rebuilding the PHP packages"
date: 2008-07-29
forum: Packaging and Compiling Programs
---

### Post by cdean on 2008-07-29
For an application on which I'm working, I need to recompile PHP with full GD support. Apparently, so sayeth a co-dev, the Ubuntu php5-gd package lacks the full functionality of GD. Also, I need to have Fileinfo installed, so I figure I might as well compile it in with PHP.

So, I'd like to recreate the php-related deb packages.

I downloaded the sources for the Intrepid version of PHP. Its dependencies are sufficiently satisfied by the versions of stuff in Hardy, so there shouldn't be a problem there.

I've also installed all of the dependencies for all of the extensions.

I'm using **Prevu** to handle the build process.

I've edited the debian/rules file to add the configure options required, as well as edited the debian/control file to add the new dependencies.

I think the error is occurring when Prevu is building the deb files.

```
# install extensions
ext=`./debian/libapache2-mod-php5/usr/bin/php-config --extension-dir`;\
	for i in libapache2-mod-php5 libapache2-mod-php5filter php5-cgi php5-cli; do \
		mkdir -p debian/$i/${ext}; \
	done; \
	cat debian/modulelist debian/extramodulelist | while read package extname dsoname; do \
		if [ -z "$dsoname" ]; then dsoname=$package; fi; \
		mkdir -p debian/php5-$package${ext}; \
		chrpath debian/libapache2-mod-php5/${ext}/$dsoname.so; \
		chrpath -d debian/libapache2-mod-php5/${ext}/$dsoname.so; \
		install -m 644 -o root -g root \
			debian/libapache2-mod-php5/${ext}/$dsoname.so \
			debian/php5-$package${ext}/$dsoname.so; \
		rm debian/libapache2-mod-php5/${ext}/$dsoname.so; \
	done
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/curl.so: no rpath or runpath tag found.
open: No such file or directory
elf_open: Invalid argument
open: No such file or directory
elf_open: Invalid argument
install: cannot stat `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/fileinfo.so': No such file or directory
rm: cannot remove `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/fileinfo.so': No such file or directory
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/gd.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/gmp.so: no rpath or runpath tag found.
open: No such file or directory
elf_open: Invalid argument
open: No such file or directory
elf_open: Invalid argument
install: cannot stat `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/imap.so': No such file or directory
rm: cannot remove `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/imap.so': No such file or directory
open: No such file or directory
elf_open: Invalid argument
open: No such file or directory
elf_open: Invalid argument
install: cannot stat `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/interbase.so': No such file or directory
rm: cannot remove `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/interbase.so': No such file or directory
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/ldap.so: no rpath or runpath tag found.
open: No such file or directory
elf_open: Invalid argument
open: No such file or directory
elf_open: Invalid argument
install: cannot stat `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/mcrypt.so': No such file or directory
rm: cannot remove `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/mcrypt.so': No such file or directory
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/mhash.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/mysql.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/odbc.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/pgsql.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/pspell.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/recode.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/snmp.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/sqlite.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/mssql.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/tidy.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/xmlrpc.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/xsl.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/mysqli.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/pdo_mysql.so: no rpath or runpath tag found.
open: No such file or directory
elf_open: Invalid argument
open: No such file or directory
elf_open: Invalid argument
install: cannot stat `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/pdo_firebird.so': No such file or directory
rm: cannot remove `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/pdo_firebird.so': No such file or directory
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/pdo.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/pdo_odbc.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/pdo_pgsql.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/pdo_sqlite.so: no rpath or runpath tag found.
debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/pdo_dblib.so: no rpath or runpath tag found.
open: No such file or directory
elf_open: Invalid argument
open: No such file or directory
elf_open: Invalid argument
install: cannot stat `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/fileinfo.so': No such file or directory
rm: cannot remove `debian/libapache2-mod-php5//usr/lib/php5/20060613+lfs/fileinfo.so': No such file or directory
make: *** [install] Error 1
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status 2
Copying back the cached apt archive contents
 -> unmounting /var/cache/prevu/src/31138 filesystem
 -> unmounting /var/cache/prevu/hardy-debs filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/31217 and its subdirectories
========================
Prevu Error: Build failed.
Prevu encountered an error performing your build. The actual
error message may be further up in the scrollback before pbuilder
exited. Please look for a failed dependency or compile error in
the full output.
```

This is my first attempt at building a package with Prevu, so I'm not quite sure what I might be doing wrong.

---

### Post by LinuxRocks713 on 2008-07-30
Why don't you try building the package manually with dpkg-deb? It's easy, as outlined in this post: [http://www.compdigitec.com/labs/2008/07/28/building-deb-packages-on-ubuntudebian/](http://www.compdigitec.com/labs/2008/07/28/building-deb-packages-on-ubuntudebian/)

---

### Post by cdean on 2008-07-30
I'd simply do **make install** before I'd take the time to make my own package for this case. I gotta have this done today.

I've verified that the problem is in the **debian/rules** *install* section. Those extensions are not in the 20060613+lfs directory.

I'm going to try, however, using dpkg-build instead of calling debian/rules manually and see what happens. If worse comes to worse, I'll just use checkinstall.

**Edit:**dpkg-build isn't going to work because the php5 source package appears to be non-standard (debian instead of DEBIAN, control syntax is different, etc.). I'm getting all kinds of errors and don't want to muck through them right now.

---

