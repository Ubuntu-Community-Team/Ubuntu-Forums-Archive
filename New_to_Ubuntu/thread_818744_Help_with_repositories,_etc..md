---
title: "Help with repositories, etc."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by LoadedBum on 2008-06-04
I'm trying to download Banshee, for my Ubuntu 8.04. I keep getting an error message that says: ```
Sub-process /usr/bin/dpkg returned an error code (1).
``` According to most of the things I've read, it's from something like a repository. I have no idea how to open them, and most of the things on the net seem like older versions that don't work.

---

### Post by ZabiGG on 2008-06-04
There's a link on how to install anything in Ubuntu if you click on "Look here" in my signature below.

Happy reading,

Z.

---

### Post by sdennie on 2008-06-04
Can you paste all the output from the command?  There should be more information that might help.  Also, a common fix for these sorts of problems is to;

```

sudo apt-get install -f

```

---

### Post by mikewhatever on 2008-06-04
> **LoadedBum said:**
> I'm trying to download Banshee, for my Ubuntu 8.04. I keep getting an error message that says: ```
Sub-process /usr/bin/dpkg returned an error code (1).
``` According to most of the things I've read, it's from something like a repository. I have no idea how to open them, and most of the things on the net seem like older versions that don't work.

Does it also tell you to run <sudo dpkg --configure -a>? If so, run that command in Terminal.

---

### Post by LoadedBum on 2008-06-04
```
dylan@dylan-laptop:~$ sudo apt-get build-dep banshee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  autoconf automake1.7 autotools-dev boo build-essential cdbs check
  cli-common-dev debhelper dpkg-dev fdupes g++ g++-4.2 gettext html2text
  intltool intltool-debian libart-2.0-dev libatk1.0-dev libaudiofile-dev
  libavahi-client-dev libavahi-common-dev libavahi-glib-dev libavahi1.0-cil
  libbonobo2-dev libbonoboui2-dev libboo2.0-cil libc6-dev libcairo2-dev
  libdbus-1-dev libdbus-glib-1-dev libeel2-dev libesd0-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgail-dev libgconf2-dev
  libgcrypt11-dev libglade2-dev libglib2.0-dev libgnome-desktop-dev
  libgnome-keyring-dev libgnome2-dev libgnomecanvas2-dev libgnomeui-dev
  libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev
  libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgtk2.0-dev
  libhal-dev libice-dev libidl-dev libipod-cil libipodui-cil libjpeg62-dev
  libkarma-cil libkarma0 liblzo2-dev libmono-dev libmono-peapi1.0-cil
  libmono-relaxng1.0-cil libmono-system-runtime1.0-cil libmono-zeroconf1.0-cil
  libmtp-dev libmusicbrainz4-dev libnautilus-burn-dev
  libnautilus-extension-dev libnjb-cil libnjb5 libopencdk10-dev liborbit2-dev
  libpango1.0-dev libpixman-1-dev libpng12-dev libpopt-dev libpthread-stubs0
  libpthread-stubs0-dev libselinux1-dev libsepol1-dev libsm-dev libsqlite3-dev
  libstartup-notification0-dev libstdc++6-4.2-dev libtagc0 libtaglib2.0-cil
  libtasn1-3-dev libtimedate-perl libusb-dev libx11-dev libxau-dev
  libxcb-xlib0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev
  libxml-dom-perl libxml-perl libxml-regexp-perl libxml2-dev libxrandr-dev
  libxrender-dev linux-libc-dev lynx m4 mono-1.0-devel mono-gmcs mono-mcs
  mono-utils monodoc-base patch po-debconf x11proto-composite-dev
  x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 133 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/35.9MB of archives.
After this operation, 134MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
(Reading database ... dpkg: error processing /var/cache/apt/archives/x11proto-core-dev_7.0.11-1_all.deb (--unpack):
 files list file for package `ssl-cert' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/x11proto-core-dev_7.0.11-1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies
dylan@dylan-laptop:~$ 

```

That's what the site tells me to enter, and the result.

---

### Post by alexandremrj on 2008-06-05
Hello,

by the look of things it looks like you want to build banshee.

Why simply don't you use synaptic and search for banshee or if you want to use the command line use:
sudo apt-get install banshee

not sudo apt-get build-dep banshee (that by your post is what you are using)

---

### Post by appoloin on 2008-06-05
this might be adumb question but is banshee? what does it do?

---

### Post by Paqman on 2008-06-05
Yeah, like alexandremrj said, Banshee is in the Ubuntu repos already. No need to compile it from source. If you're looking for a more updated version than the one in the repos, try GetDeb.

It's always, always better to get your software from the repos or a .deb file than to compile something downloaded from a website.

---

### Post by Xiong Chiamiov on 2008-06-05
> **appoloin said:**
> this might be adumb question but is banshee? what does it do?
[Ban]("http://banshee-project.org/Main_Page")[shee]("http://en.wikipedia.org/wiki/Banshee_(music_player)")

It's not a dumb question, but (not trying to be rude here), it can be easily answered by our friend [Google]("http://www.google.com/search?hl=en&q=banshee&btnG=Google+Search").

---

### Post by Xiong Chiamiov on 2008-06-05
> **Paqman said:**
> Yeah, like alexandremrj said, Banshee is in the Ubuntu repos already. No need to compile it from source. If you're looking for a more updated version than the one in the repos, try GetDeb.

It's always, always better to get your software from the repos or a .deb file than to compile something downloaded from a website.
Unless you're wanting to add some extra ./configure parameters that aren't standard to the maintainer's version.  That's the main reason to use Gentoo nowadays, anyway.

---

