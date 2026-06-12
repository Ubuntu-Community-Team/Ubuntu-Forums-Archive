---
title: "Problem installing deb-package (dependencies)"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by lando99 on 2012-02-18
Hi!
I'm trying to install the [climm]("http://www.climm.org/download.shtml.en") messenger on my Ubuntu (Server 11.10, 64bit).
So I downloaded the most recent package: [climm_0.7.1-9lucid_i386.deb]("http://www.climm.org/deb/dists/lucid/main/binary-i386/climm_0.7.1-9lucid_i386.deb").
Unfortunately the following error occurs:
```
root@lando:~# dpkg -i climm_0.7.1-9lucid_i386.deb
Selecting previously deselected package climm:i386.
(Reading database ... 60192 files and directories currently installed.)
Unpacking climm:i386 (from climm_0.7.1-9lucid_i386.deb) ...
dpkg: dependency problems prevent configuration of climm:i386:
 climm:i386 depends on libc6 (>= 2.7).
 climm:i386 depends on libgcrypt11 (>= 1.4.2).
 climm:i386 depends on libgnutls26 (>= 2.7.14-0).
 climm:i386 depends on libiksemel3.
 climm:i386 depends on tcl8.5 (>= 8.5.0).
dpkg: error processing climm:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 climm:i386

```

But I'm quite sure, that all these dependencies are installed:

```
root@lando:~# dpkg --get-selections  libc6 libgcrypt11  libgnutls26 libiksemel3 tcl8.5
libc6                                           install
libgcrypt11                                     install
libgnutls26                                     install
libiksemel3                                     install
tcl8.5                                          install
root@lando:~#

```
The versions should match.
How can I figure out what is missing?

Thanks
lando

---

### Post by Lisiano on 2012-02-18
It should be easier to install climm if you add it to your /etc/apt/sources.list or to /etc/apt/sources.list.d/climm.list

Either open it in your favorite text editor and append this line to it ```
deb http://www.climm.org/deb/ lucid main
```Or do this if running as a normal user ```
echo "deb http://www.climm.org/deb/ lucid main" | sudo tee -a /etc/apt/sources.list.d/climm.list
``` Or do this if running as root ```
echo "deb http://www.climm.org/deb/ lucid main" > /etc/apt/sources.list.d/climm.list
```

After that, a simple ```
sudo apt-get install climm:i386
``` should install climm and any dependencies it needs, also this will keep it updated.

---

### Post by lando99 on 2012-02-18
Thanks for the hint. I added "deb [http://www.climm.org/deb/](http://www.climm.org/deb/) lucid main" to the sources.list-file. Now I get:

```
root@lando:/etc/apt# apt-get install climm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package climm:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'climm:i386' has no installation candidate

```
Is there something wrong with the update site?

---

### Post by Lisiano on 2012-02-18
Weird, added it to my sources and it just complained of me not having i386 tcl8.5 installed, adding it to the install line made apt try to remove some stuff.
Trying to install the amd64 version from etch also fails... I think you have to manually compile it from source, refer to the climm download page and download the 0.7.1 source tgz or dowload the svn snapshot, follow the README/INSTALL/COMPILING instructions in the source, though usuaully it just sums up to ```
./configure
make
make install
```
You still might need some compilation tools and dependencies, all of those should be located in README/INSTALL/COMPILING.

---

### Post by lando99 on 2012-02-18
That's exactly what I tried in the first place. Here's the outcome:

```
...
checking for LIBGNUTLS... checking for libgnutls-config... no
checking for libgnutls - version >= 0.8.8... no
*** The libgnutls-config script installed by LIBGNUTLS could not be found
*** If LIBGNUTLS was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the LIBGNUTLS_CONFIG environment variable to the
*** full path to libgnutls-config.
checking for libgcrypt-config... /usr/bin/libgcrypt-config
checking for LIBGCRYPT - version >= 1.2.0... yes
checking LIBGCRYPT API version... okay
checking gcrypt.h usability... no
checking gcrypt.h presence... yes
configure: WARNING: gcrypt.h: present but cannot be compiled
configure: WARNING: gcrypt.h:     check for missing prerequisite headers?
configure: WARNING: gcrypt.h: see the Autoconf documentation
configure: WARNING: gcrypt.h:     section "Present But Cannot Be Compiled"
configure: WARNING: gcrypt.h: proceeding with the compiler's result
checking for gcrypt.h... no
checking openssl/ssl.h usability... no
checking openssl/ssl.h presence... no
checking for openssl/ssl.h... no
checking for DH_free in -lcrypto... no
checking for SSL_new in -lssl... no
configure: WARNING: cannot find a suitable SSL library -- encrypted connection support disabled
checking for libgcrypt-config... (cached) /usr/bin/libgcrypt-config
checking for LIBGCRYPT - version >= 1.2.0... yes
checking LIBGCRYPT API version... okay
checking for libotr CFLAGS...
checking for libotr LIBS...  -lotr
checking for libotr headers version 3.x >= 3.0.0... not present.
checking for otrl_message_receiving in -lotr... no
checking tcl8.5/tcl.h usability... no
checking tcl8.5/tcl.h presence... no
checking for tcl8.5/tcl.h... no
checking tcl8.4/tcl.h usability... no
checking tcl8.4/tcl.h presence... no
checking for tcl8.4/tcl.h... no
checking tcl8.3/tcl.h usability... no
checking tcl8.3/tcl.h presence... no
checking for tcl8.3/tcl.h... no
checking tcl.h usability... no
checking tcl.h presence... no
checking for tcl.h... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... no, consider installing GNU libiconv
checking for iconv() fallbacks to compile in... ASCII UCS2BE WIN1251 KOI8 LATIN9 LATIN1 UTF8 WCHART TRANSLIT
checking for FIFO functionality... no
checking XMPP... configure: error: in `/home/thofoer/climm-0.7.1':
configure: error: no, GnuTLS missing
See `config.log' for more details.
root@lando:~/climm-0.7.1#

```

But this package should be installed:
```
oot@lando:~/climm-0.7.1# dpkg --get-selections |grep gnutls
gnutls-bin                                      install
libcurl3-gnutls                                 install
libgnutls-dev                                   install
libgnutls26                                     install
libgnutls26-dbg                                 install
libgnutlsxx26                                   install

```

But that's not the only error I get. They are quite different:
```
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... configure: error: in `/home/thofoer/climm-0.7.1':
configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

```

Once I got a "cpp sanity check failed" or something. I cannot reproduce it (I always delete the install-dir and unpack the tgz afterwards between tries).

I'm not sure what to do. 
Is my linux broken? Or is the climm-distribution just to old?

---

### Post by Lisiano on 2012-02-18
I have a feeling that it's because 1) Climm is old and 2) Different architectures. I just remembered that Pidgin has support for ICQ (Which I'm guessing you are installing climm for) and that Pidgin has a CLI version called Finch, AND it's in the Ubuntu repositories.
Just do this and you should be done.
```
apt-get install finch
```

---

### Post by lando99 on 2012-02-19
Thank you for the hint. I installed finch and it works quite well. It appears to be a bit cumbersome on an ajaxterm with all that windows, but I will try it.

---

