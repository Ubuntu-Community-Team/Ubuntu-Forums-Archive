---
title: "Gaim Issue"
date: 2004-11-27
forum: Packaging and Compiling Programs
---

### Post by ZeroX on 2004-11-27
I managed to successfully compile gaim 1.0.3... but when I try to launch MSN i get the old "Blah blah, SSL Support is needed. Please install a supported SSL library"

Anyone know what lib i need?

---

### Post by jdong on 2004-11-27
remind me why you're installing GAIM from source?

---

### Post by ZeroX on 2004-11-27
Because the latest when I apt-get is 1.0.0 and when I try to install guifications plugin it cannot find gaim.pc (a bug I was told in #ubuntu on freenode irc). Compiling gaim from source would not only give me the latest version but the plugin I need would compile and work.

---

### Post by jdong on 2004-11-27
[http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.3-1.dsc](http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.0.3-1.dsc)

Looking at Hoary's GAIM 1.0.3:
```

Build-Depends: bzip2, cdbs, debhelper (>= 4.1.0), libgtk2.0-dev, autotools-dev, libgnutls11-dev (>= 1.0.16-5), libperl-dev (>= 5.8.1), tcl8.4-dev, tk8.4-dev, libao-dev, libaudiofile-dev, libgtkspell-dev, libltdl3-dev, libstartup-notification0-dev, xutils, libzephyr-dev, automake1.8
Build-Conflicts: tcl8.3-dev, tk8.3-dev

```

Make sure you have all the Build-Depends libraries installed.

---

### Post by jdong on 2004-11-27
beaming over to programming forum.

---

### Post by Roptaty on 2004-12-01
[QUOTE=ZeroX]Because the latest when I apt-get is 1.0.0 and when I try to install guifications plugin it cannot find gaim.pc (a bug I was told in #ubuntu on freenode irc). Compiling gaim from source would not only give me the latest version but the plugin I need would compile and work.[/QUOTE]

I had the same problem, but I "solved" it by using these steps: 
[list=1]
[*]apt-get source gaim
[*]sudo apt-get build-dep gaim
[*]cd into gaim-1.0.3/debian 
[*]edit rules and comment out these lines: rm -rf debian/gaim/usr/include and rm -rf debian/gaim/usr/lib/pkgconfig
[*]cd .. 
[*] dpkg-buildpackage -rfakeroot (sudo apt-get install fakeroot if you dont have it installed) 
[*] dpkg -i ../gaim*.deb  and enjoy your own deb package. 
[/list] 

Now you can install the guifications plugin. :)

---

### Post by Hikaru79 on 2004-12-07
Strange.... I just upgrade gaim with Synaptic and never even touched my GUIfications install; it just automatically carried over, I guess, because GUIfications is working fine with my new 1.1.0.  :D

---

### Post by muuseas on 2005-10-23
hi,
and i had problem with gaim and ssl. i got help there:

[http://gaim.sourceforge.net/faq-ssl.php#q14](http://gaim.sourceforge.net/faq-ssl.php#q14)

    $ sudo apt-get remove gaim

    1. You need to download the latest Gaim source.
    2. You need to install the GNU TLS library development files:

    $ sudo apt-get install libgnutls11-dev (for breezy)

    3. Compile Gaim:

    $ ./configure --enable-gnutls=yes
    $ sudo make
    $ sudo make install

---

