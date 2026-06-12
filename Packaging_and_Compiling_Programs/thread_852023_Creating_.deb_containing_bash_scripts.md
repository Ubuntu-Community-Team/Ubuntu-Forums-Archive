---
title: "Creating .deb containing bash scripts"
date: 2008-07-07
forum: Packaging and Compiling Programs
---

### Post by Roderik on 2008-07-07
I'm deploying scripts to about 10-15 machines around the office and in the datacenter and i'm currently using them from a git repository and placing them in /usr/bin. Ofcourse, none of the machines have the latest version, etc etc. 

So having some experience with creating deb's and deploying the lateste git-core packages through our ppa to those machines, i believe creating deb packages is the way to go. There even is a git-buildpackage script to help with deb's from git sources. ([http://honk.sigxcpu.org/projects/git-buildpackage/manual-html/gbp.html](http://honk.sigxcpu.org/projects/git-buildpackage/manual-html/gbp.html))

Unfortunately i can't seem to be able to create a .deb that just places several bash scripts in /usr/bin. 

I followed the guide i mentioned above, ran dh_make, and configured the control file. I also commented out "make clean" and the make command in the generated rules file. Following some guide on the forums i created a usr/bin folder in the package dir and placed the scripts there.

Launchpad was as helpful as:

> 
Rejected:
Upload rejected because it contains binary packages. Ensure you are using `debuild -S`, or an equivalent command, to generate only the source package before re-uploading. See [https://help.launchpad.net/PPAQuickStart/](https://help.launchpad.net/PPAQuickStart/) for more information.


I've googled until i was blue in the face, so i really need some help :)

Thx

---

### Post by plugwash on 2008-07-13
I haven't used ubuntu's ppa's before but my guess is you have to use some option to dpkg-buildpackage to make it generate only a source package.

---

### Post by Martje_001 on 2008-07-13
Do this;
```
mkdir ~/bash-1.0
cd bash-1.0
mkdir bash-1.0
cd bash-1.0
touch source
dh_make -f source
cd debian
gedit rules
```
Comment every line that contains '$(MAKE)' (with #).

Add this line between 'dh_md5sums' and 'dh_builddeb':
```
cd debian/bash/usr/bin; cp /path/to/bash/script .
```
Save and exit;
```
cd ..
dpkg-buildpackage -rfakeroot
```
Now your deb package is in ~/bash-1.0!

---

### Post by Major_Kong on 2008-07-15
I'm also trying to make a package for 3 bash scripts, and a perl script... 

The ubuntu guide is not very helpfull, so... could someone give me some help with this ? Do i need to make a custom install script ? Are there helpers scripts for this task ? Etc.

---

### Post by Martje_001 on 2008-07-15
Read.. the.. thread..

---

### Post by Major_Kong on 2008-07-15
> **Martje_001 said:**
> Read.. the.. thread..

I read the thread. Maybe, i'm a bit too tired... i dunno... but i did not see the info.

---

### Post by Roderik on 2008-07-15
The solution Martje_001 supplies worked fine. I changed some stuff but the essence is the same, check it out here: [https://launchpad.net/~smartlounge/+archive](https://launchpad.net/~smartlounge/+archive)

---

### Post by Major_Kong on 2008-07-22
Wouldn't the binary-indep section be a better suited place to insert the commands ?

---

### Post by Major_Kong on 2008-07-24
Well i made some changes, but i can't seem to make the package.

I get this:

> dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: pacote fonte urltoys
dpkg-buildpackage: versão da fonte 1.28
dpkg-buildpackage: fonte alterada por unknown <unknown@unknown.org>
dpkg-buildpackage: arquitectura do anfitrião amd64
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-indep-stamp configure-stamp
dh_clean 
 dpkg-source -b urltoys-1.28
dpkg-source: building urltoys in urltoys_1.28.tar.gz
dpkg-source: building urltoys in urltoys_1.28.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
# Add here commands to compile the indep part of the package.
# Nothing to do 
touch build-indep-stamp
 fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_clean -k -i 
dh_clean: I have no package to build
dh_installdirs -i
dh_installdirs: I have no package to build
cp /home/######/workspace/debs/urltoys/urltoys-1.28/bin/* /home/########/workspace/debs/urltoys/urltoys-1.28/debian/urltoys/usr/bin
cp: o alvo `/home/carlos/workspace/debs/urltoys/urltoys-1.28/debian/urltoys/usr/bin' não é uma directoria
make: *** [install-indep] Error 1
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status 2


Any ideas ?

---

### Post by Martje_001 on 2008-07-24
I assume you're also copying folders? Try:
```
cp -ap /folder /move
```

---

### Post by Major_Kong on 2008-07-24
> **Martje_001 said:**
> I assume you're also copying folders? Try:
```
cp -ap /folder /move
```

No, i just want to copy 3 bash scripts, and a perl script.

PS: Tried it anyway, same thing.

This is becoming a bit frustrating...


EDIT:
This is the whole rules file :
> 
#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1



# This has to be exported to make some magic below work.
export DH_OPTIONS

PERL ?= perl


configure: configure-stamp
configure-stamp:
	dh_testdir
	# Add here commands to configure the package.

	touch configure-stamp


#Architecture 
build: build-indep

build-indep: build-indep-stamp
build-indep-stamp: configure-stamp 

	# Add here commands to compile the indep part of the package.

	# Nothing to do 

#	touch build-indep-stamp

clean:
	dh_testdir
	dh_testroot
    
#	rm -f build-indep-stamp configure-stamp
    
    
	dh_clean 

install: install-indep install-arch
install-indep:
	dh_testdir
	dh_testroot
	dh_clean -k -i 
	dh_installdirs -i

	cp $(CURDIR)/bin/* $(CURDIR)/debian/urltoys/usr/bin
	cp $(CURDIR)/*.pm $(CURDIR)/debian/urltoys/usr/lib/perl5
    
	dh_install -i

# Must not depend on anything. This is to be called by
# binary-arch/binary-indep
# in another 'make' thread.
binary-common:
	dh_testdir
	dh_testroot
	dh_installchangelogs 
	dh_installdocs
	dh_installexamples
#	dh_installmenu
#	dh_installdebconf	
#	dh_installlogrotate	
#	dh_installemacsen
#	dh_installpam
#	dh_installmime
#	dh_installinit
#	dh_installcron
#	dh_installinfo
	dh_installman
	dh_link
	dh_strip
	dh_compress 
	dh_fixperms
#	dh_perl
#	dh_python
	dh_makeshlibs
	dh_installdeb
	dh_shlibdeps
	dh_gencontrol
	dh_md5sums
	dh_builddeb
# Build architecture independant packages using the common target.
binary-indep: build-indep install-indep
	$(MAKE) -f debian/rules DH_OPTIONS=-i binary-common

binary: binary-indep
.PHONY: build clean binary-indep binary install install-indep configure

---

### Post by Martje_001 on 2008-07-24
This should do:
> #!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1



# This has to be exported to make some magic below work.
export DH_OPTIONS

PERL ?= perl


configure: configure-stamp
configure-stamp:
dh_testdir
# Add here commands to configure the package.

touch configure-stamp


#Architecture
build: build-indep

build-indep: build-indep-stamp
build-indep-stamp: configure-stamp

# Add here commands to compile the indep part of the package.

# Nothing to do

# touch build-indep-stamp

clean:
dh_testdir
dh_testroot

# rm -f build-indep-stamp configure-stamp


dh_clean

install: install-indep install-arch
install-indep:
dh_testdir
dh_testroot
dh_clean -k -i
dh_installdirs -i

dh_install -i

# Must not depend on anything. This is to be called by
# binary-arch/binary-indep
# in another 'make' thread.
binary-common:
dh_testdir
dh_testroot
dh_installchangelogs
dh_installdocs
dh_installexamples
# dh_installmenu
# dh_installdebconf
# dh_installlogrotate
# dh_installemacsen
# dh_installpam
# dh_installmime
# dh_installinit
# dh_installcron
# dh_installinfo
dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
# dh_perl
# dh_python
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol

[B]cp $(CURDIR)/bin/* $(CURDIR)/debian/urltoys/usr/bin
cp $(CURDIR)/*.pm $(CURDIR)/debian/urltoys/usr/lib/perl5
[/B]
dh_md5sums
dh_builddeb
# Build architecture independant packages using the common target.
binary-indep: build-indep install-indep
$(MAKE) -f debian/rules DH_OPTIONS=-i binary-common

binary: binary-indep
.PHONY: build clean binary-indep binary install install-indep configure 

---

### Post by Major_Kong on 2008-07-24
Thank you for being patient... but i have yet another problem...

Now i get this:
> 
dpkg-genchanges: failure: cannot read files list file

:(

---

### Post by Martje_001 on 2008-07-25
Can you give the complete output between code-tags?

---

### Post by Major_Kong on 2008-07-25
> **Martje_001 said:**
> Can you give the complete output between code-tags?

```
dh_install -i
dh_install: I have no package to build
 signfile urltoys_1.28.dsc
gpg: skipped "unknown <unknown@unknown.org>": chave secreta não disponível
gpg: [stdin]: clearsign failed: chave secreta não disponível

 dpkg-genchanges  >../urltoys_1.28_amd64.changes
dpkg-genchanges: failure: cannot read files list file: Ficheiro ou directoria inexistente
dpkg-buildpackage: failure: dpkg-genchanges gave error exit status 2

```

---

### Post by Martje_001 on 2008-07-26
I can't really see what the problem is. Can you upload the whole *debian* directory (in .tar.bz2)? Then I'll look at it here.

---

### Post by Major_Kong on 2008-07-26
Done.

Thanks again for the time. :)

---

### Post by rlandrum on 2008-07-26
> **Martje_001 said:**
> Do this;
```
mkdir ~/bash-1.0
cd bash-1.0
mkdir ~/bash-1.0
cd bash-1.0
touch source
dh_make -f source
cd debian
gedit rules
```
Comment every line that contains '$(MAKE)' (with #).


I'm totally green, but why are you creating bash-1.0 twice in ~? ... the second cd will fail.

Is the intention to be in ~/bash-1.0/bash-1.0/ when you run dh_make?

---

### Post by Martje_001 on 2008-07-26
> **rlandrum said:**
> Is the intention to be in ~/bash-1.0/bash-1.0/ when you run dh_make?
Yes it is, my fault. Fixing it now in my previous post.

@ Major_Kong: look at the attachment.

* 1: Tabs missing on line 20
* 2: Fixed line 20 and rerunning
* 3: Tabs missing on line 30

See?

---

### Post by Major_Kong on 2008-07-26
Sorry sent the wrong debian directory... ](*,)](*,)

---

### Post by Martje_001 on 2008-07-27
Ok, I really don't know what's wrong with this. Please regenerate everything with```
dh_make
``` and don't remove all the 'extra' files.

Sorry I couldn't help you.

---

### Post by LinuxRocks713 on 2008-07-28
> **Major_Kong said:**
> I'm also trying to make a package for 3 bash scripts, and a perl script... 

The ubuntu guide is not very helpfull, so... could someone give me some help with this ? Do i need to make a custom install script ? Are there helpers scripts for this task ? Etc.

Why don't you try building it with dpkg-deb? It's very easy. Here's a step-by-step guide:
[http://www.compdigitec.com/labs/2008/07/28/building-deb-packages-on-ubuntudebian/](http://www.compdigitec.com/labs/2008/07/28/building-deb-packages-on-ubuntudebian/)

---

### Post by Major_Kong on 2008-07-29
Got it to work! (just don't ask me what was the problem)

So, one last question. What do i need to change to make the package universal? It's a bit silly to have a architechture dependent package for a few scripts...

---

### Post by Martje_001 on 2008-07-29
In your control file add (or change) the line:
```
Architecture: all
```

---

### Post by Major_Kong on 2008-07-29
Thanks for all the help. :)

---

### Post by Martje_001 on 2008-07-29
You're welcome :)

---

### Post by Major_Kong on 2008-08-01
This time it's the last question. 

How do i set file associations from the command line ? (just to make everything work 'out of the box')


Offtopic:
Is there a package for LWP::TkIO - Tk I/O routines for the LWP library ?

---

### Post by Martje_001 on 2008-08-01
> **Major_Kong said:**
> How do i set file associations from the command line ? (just to make everything work 'out of the box')
Read [this](http://freedesktop.org/wiki/Specifications/AddingMIMETutor?action=show&redirect=Standards%2FAddingMIMETutor).


> **Major_Kong said:**
> Is there a package for LWP::TkIO - Tk I/O routines for the LWP library ?
I've got absolutely no idea what you´re talking about, sorry.

---

### Post by Major_Kong on 2008-08-03
Is there a way to do this just by using a command ? I only need (can) to add the extension, as the contents is only text.

---

### Post by Martje_001 on 2008-08-03
Not that I'm aware of. But you could always do:

```
#!/bin/bash
echo '<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="image/png">
         <comment xml:lang="en">PNG image</comment>
         <comment xml:lang="af">png beeld</comment>
         ...
         <magic priority="50">
                <match type="string" value="\x89PNG" offset="0"/>
         </magic>
         <glob pattern="*.png"/>
  </mime-type>
</mime-info>' > /usr/local/share/mime/packages/whatever.xml
update-mime-database [-hvV] MIME-DIR

```

---

### Post by RATM_Owns on 2008-08-04
If anyone still needs to, I just made a script that can make a deb package for you.
Requires the package epm. (sudo apt-get install epm)

Just download the script, chmod +x it and run it.

I dunno. I'm pretty sure it will work. Only if shell scripts remember read commands. If they don't you can just open it in gedit or something and understand it.

The directory must only have the files you want to make a deb package out of in it.

EDIT: Place in /usr/bin

---

### Post by brennydoogles on 2009-08-27
I wrote a script recently that is pretty helpful for this as well, and gives you a little more control and guidance than RATM's. It is CLI based, but it creates a full directory structure for a debian package, as well as stubs for all of the required files. It also allows you to use an icon for your program, and adds it to your gnome or KDE menu. It is still a work in progress, but here it is!


ps- I would make a directory full of all of the executable files before running the script, and make sure they are all executable with ```
chmod +x
``` before running projectmaker.

---

