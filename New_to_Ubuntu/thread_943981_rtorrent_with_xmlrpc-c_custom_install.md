---
title: "rtorrent with xmlrpc-c custom install"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Nunnsby on 2008-10-10
Hi All

I need a bit of help with the following:

Running Ubuntu Server. Installed rtorrent from aptitude. Working fine. Can download torrents etc. Want to install rtgui to monitor via web.

Have gotten the rtorrent source via apt-get. Completed the build-install command (or whatever it is) to allow for building packages. When running the **sudo ./configure --with-xmlrpc-c** command I keep getting the following error:

[I]checking for STUFF... configure: error: Package requirements (sigc++-2.0 libcurl >= 7.12.0 libtorrent >= 0.11.3) were not met:

No package 'sigc++-2.0' found
No package 'libcurl' found
No package 'libtorrent' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you installed software in a non-standard prefix.[/I]

I can't understand why this is happening as it is already installed via aptitude, and all I want to do is create a custom install of it. I think it has to do with the PKG_CONFIG_PATH variable, and I have already updated this */usr/lib/pkgconfig*, as they recommend here: [http://libtorrent.rakshasa.no/wiki/CompilationHelp]("http://libtorrent.rakshasa.no/wiki/CompilationHelp"). However when I have a look in the pkgconfig directory it is empty. 

Any help would be much appreciated!

Regards

Richard

---

### Post by talsemgeest on 2008-10-10
Try installing the packages it mentions from the repositories, and if they are not there try to track them down yourself. If they are already installed, you will have to find the parts that reference it in the source code and make sure it points to the right file.

---

### Post by bodhi.zazen on 2008-10-10
apt-get install those packages and the "headers" or dev packages

add "-dev" to the end of those package names , for example 

sudo apt-get install *sigc++-2.0-dev*

---

### Post by Czar on 2009-01-23
> **bodhi.zazen said:**
> apt-get install those packages and the "headers" or dev packages

add "-dev" to the end of those package names , for example 

sudo apt-get install *sigc++-2.0-dev*
@bodhi.zazen, Thanks for the tip.  `sudo aptitude -P install sigc++-2.0-dev libtorrent-dev` did the trick.

---

