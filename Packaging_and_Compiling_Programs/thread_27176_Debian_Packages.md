---
title: "Debian Packages"
date: 2005-04-15
forum: Packaging and Compiling Programs
---

### Post by Sniffer on 2005-04-15
Simple question i think....

Anyone has some kind of info (tutorial) to make Debian Packages from the source, i really want to do some ubuntu optimized packages, in special for gens and some others that i miss in the repositories.


Thks for the reply's in advance

Sniff.

---

### Post by lao_V on 2005-04-15
googling for "how to make debian package" will get you tons of results including the one from debian as below...

[http://www.debian.org/doc/maint-guide/]("http://www.debian.org/doc/maint-guide/")

---

### Post by az on 2005-04-15
There is: [http://women.alioth.debian.org/wiki/index.php/English/BuildingWithoutHelper](http://women.alioth.debian.org/wiki/index.php/English/BuildingWithoutHelper)


Or do you mean how to build from the source packages?  

Basically make sure that the deb-src entries are in your repositories and

sudo apt-get build-dep <package> will install all the build dependancies (what youneed installed to build)

sudo apt-get source -b <package>

man apt-get

---

### Post by Sniffer on 2005-04-15
Thks for your replys,

I have just make a decision of making ubuntu my linux distro of choice. Yes i have searched in google but just want it to know if i was missing something... :smile: 


So my objective is to download the source of a program, let's say for instance Gens (Genesis emulator), solve the dependecies and build a working debian package.

This way i think i could contribute to the ubuntu community and as well have a trace by synaptic of all my installed applications.

Sniff.

---

