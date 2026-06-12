---
title: "Can someone help me solve dependency problems??"
date: 2007-08-13
forum: Programming Talk
---

### Post by jondecker76 on 2007-08-13
I've been wanting autorun.inf files on windows programs discs to work on Ubuntu and found that a spec is written and a patch is done for this. Please see 

[wiki.ubuntu.com/autorun]("wiki.ubuntu.com/autorun")

I have followed the instructions pasted below:
```

#

sudo apt-get install build-essential
sudo apt-get build-dep gnome-volume-manager
mkdir gnome-volume-manager
cd gnome-volume-manager
apt-get source gnome-volume-manager
wget http://launchpadlibrarian.net/8292130/gnome-volume-manager-autorun-inf-02.patch
patch -p1 < gnome-volume-manager-autorun-inf-02.patch
cd gnome-volume-manager-2.17.0
./configure --prefix=/usr
make
sudo make install

#



```

However, it does not work, as there are dependencies that will not satisfy (seemingly because of a conflict in expected naming convention?). Please see my output below

```

gary@gary-laptop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gary@gary-laptop:~$ sudo apt-get build-dep gnome-volume-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for gnome-volume-manager could not be satisfied.
gary@gary-laptop:~$ mkdir gnome-volume-manager
gary@gary-laptop:~$ cd gnome-volume-manager
gary@gary-laptop:~/gnome-volume-manager$ apt-get source gnome-volume-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 496kB of source archives.
Get:1 http://us.archive.ubuntu.com feisty/main gnome-volume-manager 2.17.0-0ubuntu2 (dsc) [894B]
Get:2 http://us.archive.ubuntu.com feisty/main gnome-volume-manager 2.17.0-0ubuntu2 (tar) [475kB]
Get:3 http://us.archive.ubuntu.com feisty/main gnome-volume-manager 2.17.0-0ubuntu2 (diff) [20.5kB]
Fetched 496kB in 4s (123kB/s)              
gpg: Signature made Sun 04 Mar 2007 08:22:13 PM EST using DSA key ID 0F932C9C
gpg: Can't check signature: public key not found
dpkg-source: extracting gnome-volume-manager in gnome-volume-manager-2.17.0
dpkg-source: unpacking gnome-volume-manager_2.17.0.orig.tar.gz
dpkg-source: applying ./gnome-volume-manager_2.17.0-0ubuntu2.diff.gz
gary@gary-laptop:~/gnome-volume-manager$ wget http://launchpadlibrarian.net/8292130/gnome-volume-manager-autorun-inf-02.patch
--18:58:08--  http://launchpadlibrarian.net/8292130/gnome-volume-manager-autorun-inf-02.patch
           => `gnome-volume-manager-autorun-inf-02.patch'
Resolving launchpadlibrarian.net... 82.211.81.235
Connecting to launchpadlibrarian.net|82.211.81.235|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32,597 (32K) [text/plain]

100%[====================================>] 32,597        67.44K/s             

18:58:09 (67.19 KB/s) - `gnome-volume-manager-autorun-inf-02.patch' saved [32597/32597]

gary@gary-laptop:~/gnome-volume-manager$ patch -p1 < gnome-volume-manager-autorun-inf-02.patch
patching file gnome-volume-manager-2.17.0/src/autorun_inf_parser.c
patching file gnome-volume-manager-2.17.0/src/autorun_inf_parser.h
patching file gnome-volume-manager-2.17.0/src/Makefile.am
patching file gnome-volume-manager-2.17.0/src/manager.c
gary@gary-laptop:~/gnome-volume-manager$ cd gnome-volume-manager-2.17.0
gary@gary-laptop:~/gnome-volume-manager/gnome-volume-manager-2.17.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for nautilus... /usr/bin/nautilus
checking for intltool >= 0.35.0... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking whether to enable debugging... yes
checking whether to enable run-time multiuser checks... yes
./configure: line 6329: directory: command not found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GVM... configure: error: Package requirements (libgnomeui-2.0 dbus-glib-1 >= 0.31 hal >= 0.5.4 gtk+-2.0 >= 2.6.0) were not met:

No package 'libgnomeui-2.0' found
No package 'dbus-glib-1' found
No package 'hal' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GVM_CFLAGS
and GVM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

gary@gary-laptop:~/gnome-volume-manager/gnome-volume-manager-2.17.0$ make
make: *** No targets specified and no makefile found.  Stop.
gary@gary-laptop:~/gnome-volume-manager/gnome-volume-manager-2.17.0$ 



```

Does anyone have any ideas why I'm having these dependency issues?

thanks

---

### Post by Mirrorball on 2007-08-13
Install these packages, I think it will work.

libgnomeui-dev
libdbus-glib-1-dev
libhal-dev
libgtk2.0-dev

---

