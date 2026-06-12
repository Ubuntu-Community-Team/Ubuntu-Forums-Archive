---
title: "&quot;Invisible packages&quot;"
date: 2005-12-06
forum: Packaging and Compiling Programs
---

### Post by charnooh on 2005-12-06
Hi,
it might be not nice to make my first post like "help me, i'm useless" but after  4 days of installing a simple GNU Gadu 2, i'm out of idea what to do.

The problem is:

- When i run ./configure it does not see a package [in example gtk+-2.0]  but when I check the /usr/lib/ there is "libgtk-x11-2.0.so.0"
- When i download a .deb package and install it ["dpkg -i package-2.0.deb"] then ity installs well, but still it is not seen by ./configure [like in former example]

The only way is to compile EVERY single package [including the present ones] and install it. It can be done, but i've got an error form ./configure that " Package requirements (x11) were not met." and i'm already drowning in dependencies [just to build gtk+, which is present].

I have no idea how to deal with this problem. 
btw, I have Breezy 5.10, downloaded just a week ago.

---

### Post by kairu0 on 2005-12-06
When you compile things and they check for say "GTK 2.0" or "X11," they usually are not looking for the compiled gtk 2.0 and x11 core but the header files.

For example, if you're trying to compile a gtk program and it complains about not finding gtk, then you should install the libgtk-xxxx-dev package. If you are compiling a program that depends on xosd (the x on screen display library) and it fails saying that xosd is not installed, then you should install xosd-dev.

So, when your compilation stopped at "you need gtk+-2.0," it was looking for the gtk library development files (not the actual, compiled gtk library (libgtk-x11-2.0.so.0).

---

### Post by charnooh on 2005-12-06
OK, thank you very much, but i don't know what to do with this:

libxext depends on proto-xext
proto-xext sepends on xi
and xi depends on xext
so it is "marry-go-round" i have no idea what to do with this
here's the log:

> root@sos:/home/sos/deps/depp# dpkg -i libxext-dev_6.4.3-3_i386.deb
Selecting previously deselected package libxext-dev.
(Reading database ... 60242 files and directories currently installed.)
Unpacking libxext-dev (from libxext-dev_6.4.3-3_i386.deb) ...
dpkg: dependency problems prevent configuration of libxext-dev:
 libxext-dev depends on x11proto-xext-dev; however:
  Package x11proto-xext-dev is not configured yet.
dpkg: error processing libxext-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxext-dev
root@sos:/home/sos/deps/depp# dpkg -i x11proto-xext-dev_6.9.99.0-1_all.deb
(Reading database ... 60264 files and directories currently installed.)
Preparing to replace x11proto-xext-dev 6.9.99.0-1 (using x11proto-xext-dev_6.9.99.0-1_all.deb) ...
Unpacking replacement x11proto-xext-dev ...
dpkg: dependency problems prevent configuration of x11proto-xext-dev:
 x11proto-xext-dev depends on libxi-dev; however:
  Package libxi-dev is not configured yet.
dpkg: error processing x11proto-xext-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 x11proto-xext-dev
root@sos:/home/sos/deps/depp# dpkg -i libxi-dev_1.3.0-2_i386.deb
(Reading database ... 60264 files and directories currently installed.)
Preparing to replace libxi-dev 1:1.3.0-2 (using libxi-dev_1.3.0-2_i386.deb) ...
Unpacking replacement libxi-dev ...
dpkg: dependency problems prevent configuration of libxi-dev:
 libxi-dev depends on libxext-dev; however:
  Package libxext-dev is not configured yet.
dpkg: error processing libxi-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxi-dev
root@sos:/home/sos/deps/depp#


---

### Post by kairu0 on 2005-12-07
Try a "sudo apt-get -f install"

That should install all of the missing dependencies for the packages that you just tried to install.

---

