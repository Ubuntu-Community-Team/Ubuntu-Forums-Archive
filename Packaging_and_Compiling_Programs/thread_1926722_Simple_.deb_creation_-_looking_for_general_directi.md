---
title: "Simple .deb creation - looking for general directions?"
date: 2012-02-16
forum: Packaging and Compiling Programs
---

### Post by Gen2ly on 2012-02-16
I have two .deb packages I'd really like to create.  They are both real simple (basically putting a couple files in the right directories) and I was hoping to find a simple guide or get a little help.

I have one package that is a java program.  I'd like to be able to put it in [FONT="Courier New"]/usr/bin/[/FONT] and then attach a [FONT="Courier New"].desktop[/FONT] (and icon) to it.  The other is a very basic program that just involves this:

```
gcc g9led.c -o g9led -lusb
```

to compile.  This I'd also like to put in [FONT="Courier New"]/usr/bin/[/FONT].

Is there a way to do this without having to learn a fair amount, or can I get by with a brief tutorial?

---

### Post by winh8r on 2012-02-16
Have a look here for a start:


[http://www.debian.org/doc/manuals/maint-guide/build.en.html]("http://www.debian.org/doc/manuals/maint-guide/build.en.html")

hope it helps.

---

### Post by Gen2ly on 2012-02-29
Ok, after a bit of research, I think I got it figured out.  Would appreciate though if someone/ones could check it out.

Ok, because the source code didn't have a Makefile I had to create one.  This is what I did, does it look ok?:

```
CC=gcc
CFLAGS=
LDFLAGS=

all: g9led

g9led: g9led.c
	$(CC) $(LDFLAGS) $(CFLAGS) g9led.c -o g9led -l usb

install: all
	install -m755 -D g9led /usr/bin/

clean:
	rm -f g9led
```

I'm pretty sure I got that right but not entirely sure.  I built a control file and that seemed pretty self-explanatory, then I built the **rules** file.  This file to me seems it would take a great time to master to get it right so any scrutiny here would be appreciated.  Basically, I added a clean section that I had seen a couple places and overrided auto install and did it manually (because of an error).  Here is the rules:

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

clean:
	dh_testdir
	dh_testroot
	rm -f build-stamp

	# Add here commands to clean up after the build process.
	$(MAKE) clean
	#-$(MAKE) distclean

	dh_clean

install:
override_dh_auto_install:

	# Copy executable to packaging directory
	mkdir -p $(CURDIR)/debian/g9led/usr/bin
	install -m755 -D g9led $(CURDIR)/debian/g9led/usr/bin



%:
	dh $@
```

I know this needs help.  It compiles and builds but would appreciate any feedback as mentioned as this is my first time doing this and would be tremendously helpful in the future.

---

### Post by Gen2ly on 2012-03-01
Ok, I learned this is *not* how to do it.  A debhelper programs should be used to create the directories,...  However, since I don't have time to learn the 70 or so debhelper tools, this will have to do, I guess.  It build and installs correctly so its good enough for now.

---

