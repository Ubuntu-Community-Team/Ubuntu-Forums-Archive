---
title: "New Install / Customized Packaging"
date: 2010-08-24
forum: Packaging and Compiling Programs
---

### Post by root2devnull on 2010-08-24
Does anyone here know about packaging deb files?

I'm in the process of reading [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete) but this is more of a question of, "is this the best way to do it?" than anything else.

I want to find the best way to distribute images for wallpapers, fonts, document files, and also a customized install-setup.sh as well. Right now I have an alternative Ubuntu ISO with a kickstart file that does a wget to.dropbox.com -O- | sh after Ubuntu is installed -- and while it works, it's crude. I don't really need to change the ISO image, only the script which resides on the Dropbox location.

The install-script.sh installs 3rd party applications, PPAs, sets up iptables, downloads some images files, a customized aliases file and imports it into the .bashrc and /etc/skel .bashrc, and a few other tasks as well.

Basically the idea I want to do is to do a new Ubuntu install, add the PPA, sudo apt-get update and then the deb file downloads and does all of the work.

Is this the best way to do that? One issue that may arise is the shell script does require some user input to it. Forgive me. I am not a programmer, new to packaging, etc. Just want some feedback on my method really.

If you want to see the ks.cfg and the ks-install-script.sh they are at:

[http://dl.dropbox.com/u/914191/ks-install-script.sh](http://dl.dropbox.com/u/914191/ks-install-script.sh)
[http://dl.dropbox.com/u/914191/install-script/ks.cfg](http://dl.dropbox.com/u/914191/install-script/ks.cfg)

---

