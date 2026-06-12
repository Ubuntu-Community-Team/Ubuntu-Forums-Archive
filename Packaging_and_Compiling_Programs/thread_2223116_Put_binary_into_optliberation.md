---
title: "Put binary into /opt/liberation"
date: 2014-05-09
forum: Packaging and Compiling Programs
---

### Post by Ader_ on 2014-05-09
Hi!
I recently published my first application to the Ubuntu Software Center, and got this reply:

"Your package is nearly correct you just need to use /opt/liberation-free for your binary."

I read up on Debian-packages, and realised I probably need a rules-file. I created one and put in this line:

```
bindir =/opt/liberation-free
```

But for some reason this does not put the binary into the opt-directory. What am I missing?

Rasmus

---

### Post by slooksterpsv on 2014-05-09
Here's a copy of my rules file for my efibootorder:
```

### rules
#!/usr/bin/make -f

icon = $(CURDIR)/efibootorder-icon.png
script = $(CURDIR)/efibootorder
launcher = $(CURDIR)/efibootorder.desktop

DEST1 = $(CURDIR)/debian/efibootorder/usr/share/efibootorder
DEST2 = $(CURDIR)/debian/efibootorder/usr/share/applications

build: build-stamp

build-stamp:
	dh_testdir
	touch build-stamp

clean:
	dh_testdir
	dh_testroot
	rm -f build-stamp
	dh_clean

install: build clean $(icon) $(script) $(links) $(launcher) 
	dh_testdir
	dh_testroot
	dh_prep
	dh_installdirs

	mkdir -m 755 -p $(DEST1)
	mkdir -m 755 -p $(DEST2)

	install -m 666 $(icon) $(DEST1)
	install -m 777 $(script) $(DEST1)
	install -m 777 $(launcher) $(DEST2)

binary-arch: build install
	dh_testdir
	dh_testroot
	dh_installchangelogs
	dh_installdocs
	dh_installexamples
	dh_installman
	dh_link
	dh_compress
	dh_fixperms
	dh_installdeb
	dh_gencontrol
	dh_md5sums
	dh_builddeb

binary: binary-arch
.PHONY: build clean binary-arch install

```

Now I don't know what folders were created and what ones weren't. There's a way that you need to put the files in to tell it what binary files will be included in your package:

```

#From ${CURDIR}/debian/source/included-binaries
efibootorder
efibootorder-icon.png

```

Not sure if that helps. I followed a few different sites like this one: [http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html](http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html)
But I was more doing it for a PPA, that should help on how to create the DEB though.

---

