---
title: "How to tell debian/rules to execute a command before ./configure?"
date: 2007-12-31
forum: Packaging and Compiling Programs
---

### Post by Adnarim on 2007-12-31
Hi,
I'm trying to package vidalia and put it into ppa. My problem is, that ppa creates packages which just contain the docs and no binary.:
[http://launchpadlibrarian.net/11104264/vidalia_0.0.16-2_i386.deb](http://launchpadlibrarian.net/11104264/vidalia_0.0.16-2_i386.deb)
[http://launchpadlibrarian.net/11104267/vidalia_0.0.16-2_amd64.deb](http://launchpadlibrarian.net/11104267/vidalia_0.0.16-2_amd64.deb)


My suspicion is that I messed up the debian/rules. When installing vidalia you have to execute:**export QMAKE=/usr/bin/qmake-qt4** before you can execute **./configure**.

So I opened the debian/rules and changed this part:
```

config.status: configure
        dh_testdir
        # Add here commands to configure the package.
ifneq "$(wildcard /usr/share/misc/config.sub)" ""
        cp -f /usr/share/misc/config.sub config.sub
endif
ifneq "$(wildcard /usr/share/misc/config.guess)" ""
        cp -f /usr/share/misc/config.guess config.guess
endif
       ./configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info CFLAGS="$(CFLAGS)" LDFLAGS="-Wl,-z,defs"

```

Into that:
```

config.status: configure
        dh_testdir
        # Add here commands to configure the package.
ifneq "$(wildcard /usr/share/misc/config.sub)" ""
        cp -f /usr/share/misc/config.sub config.sub
endif
ifneq "$(wildcard /usr/share/misc/config.guess)" ""
        cp -f /usr/share/misc/config.guess config.guess
endif
        export QMAKE=/usr/bin/qmake-qt4 && ./configure --disable-debug --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info CFLAGS="$(CFLAGS)" LDFLAGS="-Wl,-z,defs"

```

Was this wrong or correct and my error is elsewhere? How do I correctly do this?

greets

---

### Post by plugwash on 2008-01-01
that change looks fine to me.

Can you post a copy of your package source (dsc/diff.gz/orig.tar.gz set) somewhere so others can look at it and see if we can find the problems.

---

### Post by Adnarim on 2008-01-02
Hi,
thank you, here are my files:
[http://launchpadlibrarian.net/11104087/vidalia_0.0.16.orig.tar.gz](http://launchpadlibrarian.net/11104087/vidalia_0.0.16.orig.tar.gz)
[http://launchpadlibrarian.net/11104088/vidalia_0.0.16-2.diff.gz](http://launchpadlibrarian.net/11104088/vidalia_0.0.16-2.diff.gz)
[http://launchpadlibrarian.net/11104089/vidalia_0.0.16-2.dsc](http://launchpadlibrarian.net/11104089/vidalia_0.0.16-2.dsc)

It's really weird because I got no errors from paa but the packages are not correct...

---

### Post by plugwash on 2008-01-02
after building the package normally with dpkg-buildpackage I then tried running the main command from the install target manually and got 

fakeroot make prefix=/home/plugwash/vidalia-0.0.16/debian/vidalia/usr install
install -m 755 -p "vidalia" "/usr/bin/vidalia"
install: cannot create regular file `/usr/bin/vidalia': Permission denied
make: [install_target] Error 1 (ignored)
strip "/usr/bin/vidalia"
strip: '/usr/bin/vidalia': No such file
make: [install_target] Error 1 (ignored)
install -m 644 -p /home/plugwash/vidalia-0.0.16/doc/vidalia.1 /usr/share/man/man1/
install: cannot create regular file `/usr/share/man/man1/vidalia.1': Permission denied
make: [install_man] Error 1 (ignored)


In other words upstreams makefile is ignoring the request from debian/rules to install into a packaging directory rather than the system and to add insult to injury it is ignoring the permission denied errors from it's attempt to install into the system.

Reading the install target in the upstream makefile shows us that we need to change the last line of the install target in debian/rules to

        $(MAKE) INSTALL_ROOT=$(CURDIR)/debian/vidalia install

Your clean target in debian/rules also needs work to make it clean up properly after a build so another build is possible. The following lines need to be added to the clean target.

        -rm src/lang/*.qm                                                       
        -rm config.status

---

