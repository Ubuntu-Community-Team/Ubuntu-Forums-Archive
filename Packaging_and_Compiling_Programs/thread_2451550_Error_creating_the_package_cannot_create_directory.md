---
title: "Error creating the package: cannot create directory ‘/opt/simplest_studio’"
date: 2020-10-06
forum: Packaging and Compiling Programs
---

### Post by helg1980 on 2020-10-06
Hi!
I trying to create a .deb package. 
Created the control and rules files, did everything, as it was said in the instructions 
and after a ten thousandth attempt errors still pop up. 
The $(MAKE) command is executed successfully and is created a binary file, 
but then something strange happens. For example, an attempt in the process of the '$(MAKE) install' command  
try to create the '/opt/simplest_studio’ directory. I don't understand  anything, where does this come from. 
I.e. instead of putting the binary in a  folder the usr/bin that I specify, it tries for some reason install it in the opt folder. 
Then it is not clear how I can set in the rules file installing the icon  and shortcut to launch the application, 
I tried to find examples with  installing a shortcut and icon, I can't find... Tell me what to do with all this heap of problems?

 
Here is the terminal output with the error:


```
helg@helg-VirtualBox:~/Create DEB/simplest-studio-1.1$ dpkg-buildpackage -us -uc -rfakeroot
.
.
/usr/bin/make install DESTDIR=/home/helg/Create DEB/simplest-studio-1.1/debian/simplest-studio/usr/bin 
make[1]: Entering directory '/home/helg/Create DEB/simplest-studio-1.1'
mkdir: cannot create directory ‘/opt/simplest_studio’: Permission denied
make[1]: *** [Makefile:1075: install_target] Error 1
make[1]: Leaving directory '/home/helg/Create DEB/simplest-studio-1.1'
make: *** [debian/rules:23: install] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary subprocess returned exit status 2


```

This is my 'rules' file:


```

#!/usr/bin/make -f

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE = 1

build:
    $(MAKE)
    #docbook-to-man debian/packagename.sgml > packagename.1

clean:
    dh_testdir
    dh_testroot
    rm -f build-stamp configure-stamp
    $(MAKE) clean
    dh_clean

install: build
    dh_testdir
    dh_testroot
    dh_prep
    dh_installdirs
    # Add here commands to install the package into debian/package
    $(MAKE) install DESTDIR=$(CURDIR)/debian/simplest-studio/usr/bin 

# Build architecture -independent files here.
# binary-indep: build install

# Build architecture -dependent files here.
binary-arch: build install
    dh_testdir
    dh_testroot
    dh_installchangelogs
    dh_installdocs
    dh_installexamples
    dh_install
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

binary: binary-indep binary-arch
.PHONY: build clean binary-indep binary-arch binary install configure

```

---

### Post by TheFu on 2020-10-06
I haven't any clue and have never attempted to make a debian packes, but don't allow spaces in filenames or directory names. That's asking for failure.

I've never seen a makefile with the interpreter in the first line. Does that even work? I really don't know.
I assume you know that {tabs} have to be used, not spaces, in Makefiles (gmake). Yes?

Whenever I've used make install, it would just copy files where they needed to be, not recursively call itself.  Or am I reading that wrong?

I wouldn't guess anything more without seeing the included files.

---

### Post by helg1980 on 2020-10-06
I rewrote the Makefile, but now it writes the same thing, but this time it can't create the 'usr/bin' folder.

---

### Post by TheFu on 2020-10-06
> **helg1980 said:**
> I rewrote the Makefile, but now it writes the same thing, but this time it can't create the 'usr/bin' folder.

Is this recursive in a Makefile?
```
install: build
        $(MAKE) install DESTDIR=$(CURDIR)/debian/simplest-studio/usr/bin 

```
Or am I missing something simple.

Perhaps you want 
```
install: build
        /usr/bin/install --directory $(CURDIR)/debian/simplest-studio/usr/bin 

```
I honestly don't know. I've never used the 'install' command before and only looked at the manpage about 10 seconds.

---

### Post by helg1980 on 2020-10-06
I was able to create a working package with these parameters:


install: build
    dh_testdir
    dh_testroot
    dh_prep
    dh_installdirs
    mkdir -p $(CURDIR)/debian/simplest-studio/usr/bin
    install -m 0755 simplest_studio $(CURDIR)/debian/simplest-studio/usr/bin
    mkdir -p $(CURDIR)/debian/simplest-studio/usr/share/applications
    mkdir -p $(CURDIR)/debian/simplest-studio/usr/share/icons/hicolor/64x64/apps
    install -m 0644 simplest-studio.desktop $(CURDIR)/debian/simplest-studio/usr/share/applications
    install -m 0644 simplest-studio.png $(CURDIR)/debian/simplest-studio/usr/share/icons/hicolor/64x64/apps

It works well for me, I hope it doesn't destroy the system?

---

### Post by TheFu on 2020-10-06
Not fully specifying the install and mkdir command paths is asking to be hacked.  Never trust the PATH.  Never.

---

### Post by helg1980 on 2020-10-06
It's just that my other options don't work. How else can I do this?

---

### Post by helg1980 on 2020-10-07
> **TheFu said:**
> Not fully specifying the install and mkdir command paths is asking to be hacked.  Never trust the PATH.  Never.

If you know, tell me.

---

