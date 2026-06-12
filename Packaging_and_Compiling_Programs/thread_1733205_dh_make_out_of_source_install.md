---
title: "dh_make out of source install"
date: 2011-04-19
forum: Packaging and Compiling Programs
---

### Post by marrabld on 2011-04-19
Hi I need help building a .deb file so I can upload it to my ppa.

I can get the .deb file built using dh_make but it .deb file is pretty much empty.  I am pretty sure that this is because the 'make install' step is not working correctly.  And I believe that its because my rules file is not set up correctly.

I have to do an out of source folder build because of the way the ./config file creates the make files.  Its a big project and would take me much longer to figure out how to change this. 

if I don't use dh_make the following commands compile and install the package

```

rm -rf build
mkdir -p build

./autogen.sh

cd build
../configure --prefix=/usr/local/jude_test --with-qtlibdir=/usr/lib --with-qtdir=/usr/share/qt4

make 
sudo make install

```

When I try with dh_make I think the problem is it leaves the build folder and then executes its dh_auto_install scripts.  As the project builds but I get the (nearly) empty .deb file.  I have played around with a few different rules files, but it takes a long time to build and fail each time.  

Any help would be much appreaciated.  Here is what I have done

example_build
```

#!/bin/sh

# create configure script
# ./autogen.sh

# make a directory to build in
rm -rf build
mkdir -p build

./autogen.sh
# change to that directory
cd build

# configure to install in the sub-directory "install" and tell where to find Qt version 4
# to build command line version only without qt use option --disable-qt
../configure --prefix=/usr/local/jude_test --with-qtlibdir=/usr/lib --with-qtdir=/usr/share/qt4

# build
make 

# to install under /usr/local you probably need root priviliges
# sudo make install

```

my rules file
```

#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

%:
	dh $@ 

override_dh_auto_configure:
	./example_build


override_dh_install:

#	dh_install ./planarrad.desktop /usr/share/applications
	cd build
#	make install
	dh_auto_install

```

---

### Post by MadCow108 on 2011-04-19
the default dh_make setting uses DESTDIR to set the install folder.
It will be set to debian/tmp
[http://www.gnu.org/prep/standards/html_node/DESTDIR.html](http://www.gnu.org/prep/standards/html_node/DESTDIR.html)

from this folder you then have to set the files to be installed by dh_install*
debhelper compat 7 automatically falls back to search debian/tmp, see the manpages.

if the build takes a long time do it in steps
execute fakeroot debian/rules binary to build the package and then just execute the dh_install* scripts manually until debian/package-name is filled correctly.
export DH_VERBOSE=1 helps debugging

---

### Post by marrabld on 2011-04-19
Thanks for taking the time to reply.

I am not %100 sure what you mean.  I am not very experienced with large compiles, my make files are usually pretty simple.  Furthermore, I did not make this project, a colleague did.

"from this folder you then have to set the files to be installed by dh_install*"

Are you suggesting I will have to build a new dh_make install script and tell it where I want things installed ?  I would like to avoid that.  

There are lots of libraries and lots of compiled binaries in the project.  Its quite a complicated install procedure-- copying a lot of files out of a lot of folders to the correct destinations.  

There is already an install script that works if I just get dh_make to go to the build directory and do a 'make install' for me.

I have read that 
```
%:
	dh $@ 
```

Should pretty much do a ./configure make make install

which it does, but if I try that without going in to the build directory the make files that autogen generates don't like it.

"if the build takes a long time do it in steps"

yes this is good advice, thanks.

I am sure I am missing some concept, I would appreciate any more help I can get

---

### Post by MadCow108 on 2011-04-19
> **marrabld said:**
> 
"from this folder you then have to set the files to be installed by dh_install*"

Are you suggesting I will have to build a new dh_make install script and tell it where I want things installed ?  I would like to avoid that.  


in that case set DESTDIR to debian/package-name (this may actually be the default of dh_make, I'm not sure)

if your install script does not understand DESTDIR or any variation of it you need to patch it.
if it does then do this:
```
override_dh_auto_install:
  ./my_install_script --root=$(CURDIR)/debian/package-name
  dh_auto_install
```

where --root sets the root installation path so in the end you have something like this
debian/package-name/usr/lib/libbla.so

---

### Post by marrabld on 2011-04-24
Thanks for your help so far.

I have managed to get it built and uploaded.  I think the error was that install script was trying to install to /usr/local/  and after a bit of digging around found that is reserved for users to install to only and dh_make wont like it.  Once I changed it to /usr/bin  it worked fine.

I have one last question, the application does not include a *.desktop file.  I have written one but can't figure out how to get it copied over to /usr/share/applications I keep getting a build fail and a message saying that dh_make does not have sufficient privileges.  

any ideas on how I can get dh_make to copy it over.  There is a menu.ex file but I have read that Ubuntu does not follow the Debian menu system.

Thanks

---

### Post by MadCow108 on 2011-04-24
put it into the install fill for dh_install
e.g.
path/yourfile.desktop usr/share/application
note the missing leading / in the destination!

if it is not included in the original source place it in the debian/ folder

if you get permission denied errors use fakeroot:
fakeroot debian/rules binary

---

### Post by marrabld on 2011-04-25
Thanks MadCow108

That worked a treat.  My error was I had /usr/share/applications and not usr/share/applications

as soon as I dropped the /  it worked.  And I have uploaded it to my ppa and it successfully built there too.

thanks again 

\m/ :-O \m/

---

