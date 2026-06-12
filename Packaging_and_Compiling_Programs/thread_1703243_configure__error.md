---
title: "configure:  error????"
date: 2011-03-09
forum: Packaging and Compiling Programs
---

### Post by castiglione on 2011-03-09
Hi, all.

I've been trying to install/compile Zoom 1.1.4 on Ubuntu and have run into problems.  ./configure works fine up until "configuring features" at which point, this is displayed on the terminal:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for windres... no
checking if we're cross-compiling using mingw32... no
checking for Carbon... no
checking for X... no
[U][B]configure: error: No supported configurations found
[/B][/U]
Could someone tell me what the configure error message (bolded and underlined for emphasis) means?  I'm running Ubuntu 10.10 on an ASUS netbook (1005HA).

Thank you,

c

---

### Post by zenwalker on 2011-03-09
> checking for windres... no
checking if we're cross-compiling using mingw32... no
checking for Carbon... no
checking for X... no
As you can see, above libs or packages has to be present in your system. If its already installed, then development libs of those are missing.

---

### Post by castiglione on 2011-03-09
Thanks!

---

### Post by gmargo on 2011-03-09
For Maverick, you'll have to install at least these packages, plus build-essential:

libexpat1-dev libfontconfig1-dev libfreetype6-dev libice-dev libpng12-dev libsm-dev libt1-dev uuid-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxext-dev libxft-dev libxrender-dev zlib1g-dev

---

### Post by castiglione on 2011-03-09
Hello,

at the risk of appearing thick, how do I install Carbon, X and windres on Ubuntu?  I managed to find wingw32 using Synaptic Package Manager.

Thank you,

c

---

### Post by gmargo on 2011-03-10
> **castiglione said:**
> how do I install Carbon, X and windres on Ubuntu?  I managed to find wingw32 using Synaptic Package Manager.


The "./configure" script (a product of **autoconf** tools) is a tool for cross-domain configuration.  Some of the things it searches for are only applicable to non-Linux use.

The list I gave includes the X libraries.
Carbon = MacOSX window kit(?), you don't need it.
winres = Windows related I think, you don't need it.
mingw32 = Windows cross-compiler, you don't need it.

---

### Post by castiglione on 2011-03-10
Installing all the packages helped and configure worked.

However, upon typing "make install", I ended up with this little bit of news:

/usr/bin/install -c 'zoom' '/usr/local/bin/zoom'
/usr/bin/install: cannot create regular file `/usr/local/bin/zoom': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/roland/Downloads/zoom-1.1.4/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/roland/Downloads/zoom-1.1.4/src'
make: *** [install-recursive] Error 1

I believe the salient bit of information is "Permission denied".

Is there some sort of setting that I need to toggle for permission to be granted to create the file?

---

### Post by gmargo on 2011-03-11
Since users don't normally have permission to write in **/usr/local/**, you'll need to use "sudo make install" in the final step.

---

