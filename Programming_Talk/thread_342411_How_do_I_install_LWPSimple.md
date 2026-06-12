---
title: "How do I install LWP::Simple?"
date: 2007-01-20
forum: Programming Talk
---

### Post by Spaced Monkey on 2007-01-20
Hi,

I'm new to Ubuntu, and I'm setting up Xplanet (the new version), and I've got so far, but the perl script to fetch the cloud images is failing because it can't locate LWP::Simple

I know next to nothing about Perl (more of a Python person) - so I'm not sure if the module is present, but just not being found, or if it needs to be installed.   Searching for LWP didn't give any results in my filesystem, so I presume I need to install it.

How on earth do I do this?  I tried "ppm install LWP::Simple" as suggested via Googling, but that didn't work.

Any help much appreciated.

Spaced Monkey

---

### Post by Spaced Monkey on 2007-01-20
Ignore me - after pretty much giving up I tried Synaptics, expecting it to not install individual Perl modules, which is doesn't.   It does however install the entire LWP library if you ask it to - hurrah!   (I tell you this for the aid of future searchers.)

---

### Post by therealcmj on 2008-08-05
And for the benefit of others the name of the package you want is libwww-perl

---

### Post by phaedrus on 2008-08-15
> **therealcmj said:**
> And for the benefit of others the name of the package you want is libwww-perl

Thanks for that therealcmj! I had just installed four modules manually, before deciding there had to be module packs or something like that... libwww-perl is exactly what I needed :)

---

### Post by siouzi on 2008-08-16
The Perl modules in the synaptic packages are nearly always outdated. To install the latest versions use the **cpan** command. The problem with this is the default paths - cpan tries to install the modules and such to /usr/local/... directories. This means you would have to install modules as root, which is a security risk.

To use cpan safely and install all the modules and documentation to a directory of your choice, you have to create a configuration file for cpan. This is not very beginner friendly, but basically editing an existing cpan configuration file and adding paths to your .bashrc is enough. 

See: [Using CPAN with a non-root account](http://sial.org/howto/perl/life-with-cpan/non-root/)

---

