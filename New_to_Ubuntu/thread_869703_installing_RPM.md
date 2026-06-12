---
title: "installing RPM"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by cranston on 2008-07-25
i am trying to install from scratch Unbuntu server. how do i install RPM onto Ubuntu? IMHO Linux is very different from windows when it comes to installing software.  your help will be very much appreciated

---

### Post by bumanie on 2008-07-25
Ubuntu needs .deb files. Rpm files are for distributions such as red hat. There is a program called alien that can convert .deb --> .rpm and .rpm --> .deb but usually there is an equivalent .deb file you can find instead.

---

### Post by ibuclaw on 2008-07-25
You can also install the rpm as it is.
```
apt-get install rpm
```

And then run
```
sudo rpm -i **file**.rpm
```
To install it.

This won't be added to the apt manager, so you'll have to keep the files if you wish uninistall at a later date.
```
sudo rpm -e **file**.rpm
```

But, on a more personal note. What are you installing? And why does it need to be rpm?

The Ubuntu repository has a vast amount of packages, and within it, there probably is what you are looking for and more...

Type in
```
aptitude
```
and have a search for the package in there.

Regards
Iain

---

### Post by SunnyRabbiera on 2008-07-25
RPM and Debs are installer packages simular to windows installer files though work more like a zip (tar) file.
If there is an application out there you need make sure it has a debian installer for it, otherwise use alien to convert it.

---

### Post by hyper_ch on 2008-07-25
what are you trying to install? Normally you don't have to download stuff yourself but you use the package manager.

---

### Post by ByteJuggler on 2008-07-25
Yes, to reiterate what others have said/implied:  .rpm is the native package format for Redhat/Fedora based distributions.  Ubuntu uses the .deb (Debian) package format, being that it is based on Debian.  It is preferable to use native (meaning .deb) packages on Ubuntu since other systems aren't laid out exactly the same way as Ubuntu, and so their packages might sometimes run into problems when run on ubuntu and vice versa.  You should also find that most packages that you can find an .rpm for you should usually also be able to find an Ubuntu (or failing that at least a Debian) package for.  Although that said, there's always exceptions.  Also, it's usually easiest to just use the package manager (synaptic) to search for and install a package, rather than manual downloading and then installing it.

What package are you looking for/trying to install?

---

