---
title: "How to create alsa .deb-packages?"
date: 2007-02-09
forum: Packaging and Compiling Programs
---

### Post by uli_bru on 2007-02-09
Hello,

I would like to get the newest alsa sources as a .deb package which would allow me to use e.g. Synaptic for installation/deinstallation.

So I have started with
* downloading and unpacking of e.g. alsa-driver-1.0.14rc2.tar.bz2 in /usr/src/alsa by

sudo tar -xvjf alsa-driver-1.0.14rc2.tar.bz2

* change dir

cd alsa-driver-1.0.14rc2

* preparation

sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r)  --with-cards=all --with-sequencer=yes

* then I tried

sudo dh_make --createorig 

and selected library (or is multibinary or kenel module the right choice?)

* the next step was to try (after editing debian/control and renaming the package name to alsa-driver-test)

sudo fakeroot debian/rules binary

but this ended with warnings like
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}


Please accept my playing around without knowing in detail what I'm doing. But I'm very new to this and I simply tried to follow some wikis. Anyway it allows me (hopefully) to ask more precise questions.

Can someone tell me what is the right sequence to build the alsa software  (driver, lib, lib-dev, utils ...) as usable packages for Ubuntu ?

Uli

---

### Post by pompeyjohn on 2007-03-01
*bump*

I would love to know this as well.

---

### Post by bracc0 on 2007-03-09
*bump*bump*
We're in three now!

Claudio

---

### Post by 2161warrior on 2008-03-15
Although this is an old topic, some newbies might find it interesting to know that you can easily add source to synaptic and create a deb file just by entering:

```
sudo checkinstall
```

instead of:

```
sudo make install
```

You'll probably want to enter some details about the package if it's for community use, but you really don't need to. Also, the order goes:

alsa-driver, alsa-lib, alsa-utils.

2161

---

### Post by Vorian on 2008-03-15
If want to make a real debian package, then read this guide.

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

It all starts with dh_make :)

---

### Post by pt123 on 2008-03-17
> **2161warrior said:**
> Although this is an old topic, some newbies might find it interesting to know that you can easily add source to synaptic and create a deb file just by entering:

```
sudo checkinstall
```


Thanks

---

### Post by alain57 on 2008-12-03
i did one with dh_make
but there is no kernel module in the deb, so it's useless :(

i then did one with checkinstall, but there are 2 problems

first : there is only a module for the current used kernel (and i use preposed, so my kernel is not the same like all other... so my deb will be useless for all people who don't have preprosed sources)

is there a way to include ALL kernels on my system ?

second : i need to install the deb with "dpkg -i --force-overwrite" because their is an other kernel module that have the same name... is there a way to do the replace automatically, without command line

---

