---
title: "building debs for rpm builders"
date: 2010-03-30
forum: Packaging and Compiling Programs
---

### Post by ffi on 2010-03-30
I know how to make rpm's, is there a quick guide somewhere to get me going, preferably one which starts or assume you know a little about rpm ?

---

### Post by SevenMachines on 2010-03-31
hi there, afraid i dont know of such a guide myself. I'd still think the easiest way is to whisk through the [ubuntu packaging guide]("https://wiki.ubuntu.com/PackagingGuide/Complete").

Although it might be helpful to look at the general structure of [debian packaging files]("https://wiki.ubuntu.com/PackagingGuide/PackagingOverview") for an overview first, since you'll quickly spot the .spec file equivalents in debian.

Maybe even a cup of tea and [some videos ]("https://wiki.ubuntu.com/MOTU/Videos")(thanks dholbach!)

Excuse my rpm ignorance :) but (and anyone please correct this if its wrong!)
In a .spec file to debian sort of generally equivalent way
.spec license/authors -> debian/copyright
name/version/description sections -> debian/control
%changelog -> debian/changelog :)
and build/install etc sections -> debian/rules

Might be half an idea to take an rpm you know well and to convert it with
$sudo alien --to-deb -g <package>.rrpm
it wont create a particularly great package in a lot of cases but if you look through the debian directory it creates you might get a quick idea of the similarities and diferences rpm .spec files and debian/ files

---

### Post by ffi on 2010-04-02
thanks maybe lter i'll try and have a go at building a deb

---

