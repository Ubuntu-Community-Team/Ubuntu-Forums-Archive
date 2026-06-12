---
title: "mplayer doesn't have x11 support?"
date: 2004-10-21
forum: Packaging and Compiling Programs
---

### Post by Vulc on 2004-10-21
Error: X11 support required for GUI compilation

I get this error when I try to ./configure mplayer following disposable's multimedia faq....anyone have an idea of how to fix?

---

### Post by flygmaskin on 2004-10-21
I think you need to install x-window-system-dev (apt-get install x-window-system-dev)

---

### Post by Vulc on 2004-10-21
I tried that and it tells me it needs about 20 other files but won't download them

The following packages have unmet dependencies:
  x-window-system-dev: Depends: libdps-dev but it is not going to be installed
                       Depends: libdps1-dbg but it is not going to be installed
                       Depends: libice-dev but it is not going to be installed
                       Depends: libice6-dbg but it is not going to be installed
                       Depends: libsm-dev but it is not going to be installed
                       Depends: libsm6-dbg but it is not going to be installed
                       Depends: libx11-6-dbg but it is not going to be installed                       Depends: libx11-dev but it is not going to be installed
                       Depends: libxaw7-dbg but it is not going to be installed
                       Depends: libxaw7-dev but it is not going to be installed
                       Depends: libxext-dev but it is not going to be installed
                       Depends: libxext6-dbg but it is not going to be installed                       Depends: libxi-dev but it is not going to be installed
                       Depends: libxi6-dbg but it is not going to be installed
                       Depends: libxmu-dev but it is not going to be installed
                       Depends: libxmu6-dbg but it is not going to be installed
                       Depends: libxmuu-dev but it is not going to be installed
                       Depends: libxmuu1-dbg but it is not going to be installed                       Depends: libxp-dev but it is not going to be installed
                       Depends: libxp6-dbg but it is not going to be installed
                       Depends: libxpm-dev but it is not going to be installed
                       Depends: libxpm4-dbg but it is not going to be installed
                       Depends: libxrandr-dev but it is not going to be installed
                       Depends: libxrandr2-dbg but it is not going to be installed
                       Depends: libxt-dev but it is not going to be installed
                       Depends: libxt6-dbg but it is not going to be installed
                       Depends: libxtrap-dev but it is not going to be installed                       Depends: libxtrap6-dbg but it is not going to be installed
                       Depends: libxtst-dev but it is not going to be installed
                       Depends: libxtst6-dbg but it is not going to be installed                       Depends: libxv-dev but it is not going to be installed
                       Depends: libxv1-dbg but it is not going to be installed
                       Depends: xlibmesa-gl-dev but it is not going to be installed
                       Depends: xlibmesa-glu-dev but it is not going to be installed
                       Depends: xlibmesa-gl-dbg but it is not going to be installed
                       Depends: xlibmesa-glu-dbg but it is not going to be installed
                       Depends: xlibosmesa-dev
                       Depends: xlibs-static-dev but it is not going to be installed
                       Depends: xlibs-static-pic but it is not going to be installed
E: Broken packages

---

### Post by drynwhyl on 2005-01-26
Hi!

I had the same problem and after my  /etc/apt/sources.list looked like the following,   I got it working  \\:D/ 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty multiverse

Cheers!

---

### Post by erick.red on 2006-10-19
so, guys , what are exactly the packages that need to be downloaded?

thanks u

---

