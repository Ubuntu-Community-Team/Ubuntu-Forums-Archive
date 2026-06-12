---
title: "Preserve permissions on a file?"
date: 2008-08-28
forum: Packaging and Compiling Programs
---

### Post by Ludwik on 2008-08-28
Hello,

I'd very appreciate some help, because at this point I'm pretty desperate.

I try to package my own Python script. It's the first time I'm making a package. I use [This tutorial](http://videos1.showmedo.com/ShowMeDos/extras/linuxJensMakingDeb/from_py_to_deb.pdf).

Everything works fine, except... there is one file that should have "write" permissions for all users on the system. That's crucial for the program. Unfortunately when I try to install the program from my debian package permissions on the file don't include "write" for all users.

When I run the "dpkg-buildpackage" command the file is copied from the original folder to the "debian" folder. For some reason the permissions are always dropped during this operation.

Here is the install part of the "rules" file (the file I'm talking about lives in the "data" folder):

```
install: build
	dh_testdir
	dh_testroot
	dh_clean -k 
	dh_installdirs

	# Add here commands to install the package into debian/laika-sequencer.
	#$(MAKE) DESTDIR=$(CURDIR)/debian/laika-sequencer install

	mkdir -p $(CURDIR)/debian/laika-sequencer
	cp laika-sequencer.py $(CURDIR)/debian/laika-sequencer/usr/bin/laika-sequencer.py

	mkdir -p $(CURDIR)/debian/laika-sequencer/usr/share/laika-sequencer
	cp -pr data/* $(CURDIR)/debian/laika-sequencer/usr/share/laika-sequencer
	chmod -R a+w $(CURDIR)/debian/laika-sequencer/usr/share/laika-sequencer/dzwieki
	chmod -R a+r $(CURDIR)/debian/laika-sequencer/usr/share/laika-sequencer/dzwieki
	cp laika-sequencer.desktop $(CURDIR)/debian/laika-sequencer/usr/share/applications

```

How do I preserve the permissions?

---

### Post by Ludwik on 2008-08-28
Ok, I solved the problem by adding the chmod line to the "postinst" file.

---

