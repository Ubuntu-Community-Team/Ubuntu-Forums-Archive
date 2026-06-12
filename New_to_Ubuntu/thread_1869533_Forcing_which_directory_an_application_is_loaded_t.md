---
title: "Forcing which directory an application is loaded to"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by BobWalance on 2011-10-25
Greetings all,

I'm brand new to Linux and Ubuntu. With hopes that I can ween myself from Microsoft, I bought another PC and loaded Ubuntu 11.10 on to it.

I have been told that it is possible to set up a Linux system such that all new (non-base-installed) applications can be stored in a separated disk or partition so that if the operating system needs to be reloaded my installed apps don't need to be reloaded, too.

One experienced Linux user suggested that I create a separate partition for the /home directory, then create /home/opt, and then finally mount /home/opt onto /opt. Then, if all new apps were loaded to /opt, they would could be left safe and intact if the operating system were to be re-installed.

However, in practice, this doesn't seem to be possible (i.e. loading my apps into the /opt directory). I have not been able to find a method to tell Ubuntu Software Center or Synaptic where to install applications.

Does anybody know if forcing the newly-loaded applications' (and all of their components) install directory into /opt is possible?

Thanks much,
Bob

---

### Post by cariboo on 2011-10-26
The Software Center will install packages where the install scripts tell it to. You'd have to download the package, extract it, modify the install script then rebuild the package and install it, to put it where you think you want it.

What your expert friend meant, I think, is to install programs that aren't available as .debs to /opt.

The only program I use that isn't packaged as a deb, is [Calibre]("http://calibre-ebook.com/"), as the version in the repositories is quite buggy. The Calibre installation script automagically installs it to /opt. Many other programs that use an install script usually give you the option to set  where you want to install them.

---

