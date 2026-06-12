---
title: "Permissions are not preserved when making a DKMS .deb package"
date: 2014-07-17
forum: Packaging and Compiling Programs
---

### Post by Nigraffle on 2014-07-17
Hello all,

I’m trying to package a kernel module and some userspace scripts into a DKMS .deb package, and the guide I’m using ([https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging](https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging)) works great, except it doesn’t preserve file permissions in the .deb package.

This is fine, except that I’m trying to include POST_INSTALL and POST_REMOVE scripts.  Once the package gets built, those scripts are no longer executable.

I’ve tried a couple times to get this to work, and ended up creating a really small example module to try to reduce the complexity of the build until I figure this out.

The output of the source directory:

```
adam@ubuntu:/usr/src/hello-0.1$ ll
total 40
drwxr-xr-x 2 root root 4096 Jul 17 13:21 ./
drwxr-xr-x 5 root root 4096 Jul 17 10:09 ../
-rw-r--r-- 1 root root  183 Jul 17 11:16 dkms.conf
-rw-r--r-- 1 root root  276 Jul 17 11:16 hello.c
-rwxr-xr-x 1 root root 8511 Jul 17 13:21 hello_world*
-rwxr-xr-x 1 root root   77 Jul 17 13:20 install_hello.sh*
-rw-r--r-- 1 root root  398 Jul 17 11:16 Makefile
-rwxr-xr-x 1 root root   44 Jul 17 13:20 uninstall_hello.sh*
```

A copy of my dkms.conf:

```
PACKAGE_NAME="hello"
PACKAGE_VERSION="0.1"
CLEAN="make clean"
MAKE[0]="make all KVERSION=$kernelver"
BUILT_MODULE_NAME[0]="hello"
POST_INSTALL="install_hello.sh"
POST_REMOVE="uninstall_hello.sh"
DEST_MODULE_LOCATION[0]="/updates"
AUTOINSTALL="yes"
```

The contents of the .deb file:
```
adam@ubuntu:~$ lesspipe hello-dkms_0.1_all.deb
hello-dkms_0.1_all.deb:
 new debian package, version 2.0.
 size 8910 bytes: control archive=1433 bytes.
     258 bytes,     9 lines      control
     528 bytes,     8 lines      md5sums
    1216 bytes,    49 lines   *  postinst             #!/bin/sh
     332 bytes,    28 lines   *  prerm                #!/bin/sh
 Package: hello-dkms
 Version: 0.1
 Architecture: all
 Maintainer: Dynamic Kernel Modules Support Team <pkg-dkms-maint@lists.alioth.debian.org>
 Installed-Size: 50
 Depends: dkms (>= 1.95)
 Section: misc
 Priority: optional
 Description: hello driver in DKMS format.

*** Contents:
drwxr-xr-x root/root         0 2014-07-17 13:24 ./
drwxr-xr-x root/root         0 2014-07-17 13:24 ./usr/
drwxr-xr-x root/root         0 2014-07-17 13:24 ./usr/src/
drw-r-xr-x root/root         0 2014-07-17 13:22 ./usr/src/hello-0.1/
-rw-r--r-- root/root        44 2014-07-17 13:20 ./usr/src/hello-0.1/uninstall_hello.sh
-rw-r--r-- root/root      8511 2014-07-17 13:21 ./usr/src/hello-0.1/hello_world
-rw-r--r-- root/root        77 2014-07-17 13:20 ./usr/src/hello-0.1/install_hello.sh
-rw-r--r-- root/root       398 2014-07-17 11:16 ./usr/src/hello-0.1/Makefile
-rw-r--r-- root/root       248 2014-07-17 13:22 ./usr/src/hello-0.1/dkms.conf
-rw-r--r-- root/root       276 2014-07-17 11:16 ./usr/src/hello-0.1/hello.c
drwxr-xr-x root/root         0 2014-07-17 13:24 ./usr/share/
drwxr-xr-x root/root         0 2014-07-17 13:24 ./usr/share/hello-dkms/
-rw-r--r-- root/root      1647 2014-07-17 13:24 ./usr/share/hello-dkms/hello-0.1.dkms.tar.gz
-rwxr-xr-x root/root      9090 2014-07-17 13:24 ./usr/share/hello-dkms/postinst
```

Notice that install_hello.sh, uninstall_hello.sh, and hello_world are no longer executable.

And finally, and attempted installation:
```
adam@ubuntu:~$ sudo dpkg -i hello-dkms_0.1_all.deb
(Reading database ... 70319 files and directories currently installed.)
Preparing to unpack hello-dkms_0.1_all.deb ...

-------- Uninstall Beginning --------
Module:  hello
Version: 0.1
Kernel:  3.13.0-24-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.

Running the post_remove script:
depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 0.1
completely from the DKMS tree.
------------------------------
Done.
Unpacking hello-dkms (0.1) over (0.1) ...
Setting up hello-dkms (0.1) ...

Loading tarball for hello-0.1
Loading /var/lib/dkms/hello/0.1/3.13.0-24-generic/x86_64...

DKMS: ldtarball completed.

Creating symlink /var/lib/dkms/hello/0.1/source ->
                 /usr/src/hello-0.1

DKMS: add completed.
First Installation: checking all kernels...
Building only for 3.13.0-24-generic
Building for architecture x86_64

hello:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-24-generic/updates/dkms/

: The post_install script is not executable.

depmod....

DKMS: install completed.
```

And because install_hello.sh is not executable in the .deb file, I get the “not executable” warning above.  Thus the hello_world executable is never moved to the correct directory, defined by the install/uninstall scripts.
Is there something I’m missing? Has anyone else tried to do something like this?
Thanks in advance.

If it helps at all, the output of the DKMS commands is below:

```
adam@ubuntu:/usr/src/hello-0.1$ sudo dkms add -m hello -v 0.1

Creating symlink /var/lib/dkms/hello/0.1/source ->
                 /usr/src/hello-0.1

DKMS: add completed.
adam@ubuntu:/usr/src/hello-0.1$ sudo dkms build -m hello -v 0.1

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.13.0-24-generic all KVERSION=3.13.0-24-generic....
cleaning build area....

DKMS: build completed.
adam@ubuntu:/usr/src/hello-0.1$ sudo dkms mkdeb -m hello -v 0.1
Using /etc/dkms/template-dkms-mkdeb
copying template...
modifying debian/changelog...
modifying debian/compat...
modifying debian/control...
modifying debian/copyright...
modifying debian/dirs...
modifying debian/postinst...
modifying debian/prerm...
modifying debian/README.Debian...
modifying debian/rules...
copying legacy postinstall template...
Copying source tree...
Gathering binaries...Marking modules for 3.13.0-24-generic (x86_64) for archiving...

Creating tarball structure to specifically accomodate binaries.

Tarball location: /var/lib/dkms/hello/0.1/tarball//hello-0.1.dkms.tar.gz


DKMS: mktarball completed.

Copying DKMS tarball into DKMS tree...
Building binary package...dpkg-buildpackage: warning: using a gain-root-command while being root
 dpkg-source --before-build hello-dkms-0.1
 fakeroot debian/rules clean
 debian/rules build
 fakeroot debian/rules binary
 dpkg-genchanges -b >../hello-dkms_0.1_amd64.changes
dpkg-genchanges: binary-only upload - not including any source code
 dpkg-source --after-build hello-dkms-0.1


DKMS: mkdeb completed.
Moving built files to /var/lib/dkms/hello/0.1/deb...
Cleaning up temporary files...
```

---

### Post by Nigraffle on 2014-07-23
SOLVED:

Took me a bit to figure this all out, mostly since this is the first time I've build either a kernel module or a Debian package.

DKMS will automatically use a set of template files (located in /etc/dkms/template-dkms-mkdeb/) unless they're present in the source directory during the build.
This directory contains a Makefile that is used in creating the package.  Part of it is below

```
#source tree
ifeq ("$(wildcard $(NAME)-$(VERSION))", "$(NAME)-$(VERSION)")
	install -d "$(SRC)"
	cp -a $(NAME)-$(VERSION) $(SRC)
	chmod 644 -R "$(SRC)/$(NAME)-$(VERSION)"
endif
```

The "chmod 644 -R ..." removes executable permissions from the entire source tree, including any install/uninstall scripts.

To work around this, make sure you make a copy of the template directory in your source directory named "<module_name>-dkms-mkdeb", and either remove the line, or, for extra points, just make sure you re-set the desired permissions after that line.

Hope this helps anyone who comes across a similar error.

---

