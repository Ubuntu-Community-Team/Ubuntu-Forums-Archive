---
title: "synaptic error"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by willy james on 2008-09-15
Hi having an issue with some dependencies here:

Synaptic Package Manager, when attempting to fix a broken dependency traced from the SKYPE package, wants to install "ia32-libs"  however, attempting to execute this change results in the following error:

"E: /var/cache/apt/archives/ia32-libs_2.2ubuntu11_amd64.deb: trying to overwrite `/usr/lib32/libGL.so.1', which is also in package nvidia-glx-new"

any ideas how  to deal w/this?

---

### Post by neurostu on 2008-09-15
open a terminal and try:
```

sudo apt-get -f install

```

---

### Post by willy james on 2008-09-15
Hi Neurostu tried that, here's what I'm getting:

will@will-desktop:~/Desktop/fromPC/garden/images$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libtwolame0 libsvga1 libpcrecpp0 libenca0 mplayer-skins faac libggi2 libgif4
  libgii1 ocrad libgii1-target-x vorbis-tools mkvtoolnix lame
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ia32-libs
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/20.9MB of archives.
After this operation, 101MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 131492 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu11_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.2ubuntu11_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/libGL.so.1', which is also in package nvidia-glx-new
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.2ubuntu11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by neurostu on 2008-09-16
Do you have XChat installed?  If don't you can use Pidin, anyway try connecting to the IRC server irc.freenode.net then join the #ubuntu-motu channel.  (use /join #ubuntu-motu) to join the channel.

You should be able to get more help in that channel. That is where the people who build the ubuntu packages talk and they should be able to help you out.

---

