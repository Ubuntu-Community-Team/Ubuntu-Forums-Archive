---
title: "Why is Gentoos' Package Manager Garbage?"
date: 2007-09-27
forum: Other OS Talk
---

### Post by wolfen69 on 2007-09-27
every time ive tried gentoo or sabayon i cant get anything to download correctly. dependency problems, wrong kernel, etc. not to mention how long it takes for it to figure out dependencies. after all that, it doesnt work anyway. how anyone can put up with it is beyond me.

---

### Post by rsambuca on 2007-09-27
I have never had a problem with Portage (yet!).  Portage should be taking care of installing the dependencies for you so perhaps something else isn't quite set right.  For example, to install tuxpaint, all I had to do was type "emerge tuxpaint", and it installs both the desired ebuild as well as all required dependencies.

---

### Post by mips on 2007-09-27
Also never had an issue. The only hurdle I ever encountered were masked packages but thats a different story.

---

### Post by fuscia on 2007-09-27
from what i've read, it seems like a really good idea. i just couldn't take how slow it is and ended up coming back to ubuntu, from sabayon, twice, for that very reason.

---

### Post by igknighted on 2007-09-27
> **mips said:**
> Also never had an issue. The only hurdle I ever encountered were masked packages but thats a different story.

I get he is referring to masked or blocked packages...

The problem is not that the package manager is broken, but that what you are telling it to do is not possible.  There are almost always ways around this (like removing a package and adding it again after the install because it wasn't compiled with support for the new app to begin with, for example).

Also, Sabayon has a lot of their own packages and many times they conflict with Gentoo's, so while you CAN install from Gentoo's repos, it is not often easy (or advised).  Your best bet is either a true Gentoo install, or install the miminal Sabayon install and compile the rest.

---

### Post by jinx099 on 2007-09-27
I gave gentoo a fair shot recently and have been rather bothered by emerge.  When I do an "emerge gnome" it keeps failing on certain dependencies asking for USE flags.  Sometimes when I add or subtract the flags from my make.conf it will work and emerge can continue, but other times not, it will fail for the exact same reason on the same package.  I can't figure it out.

I've got X, gdm and fluxbox compiled, but I cant seem to get all the way through.  What is the most sane set of USE flags for compiling gnome for the first time?

---

### Post by igknighted on 2007-09-27
> **jinx099 said:**
> I gave gentoo a fair shot recently and have been rather bothered by emerge.  When I do an "emerge gnome" it keeps failing on certain dependencies asking for USE flags.  Sometimes when I add or subtract the flags from my make.conf it will work and emerge can continue, but other times not, it will fail for the exact same reason on the same package.  I can't figure it out.

I've got X, gdm and fluxbox compiled, but I cant seem to get all the way through.  What is the most sane set of USE flags for compiling gnome for the first time?

I would just use the standard desktop profile

---

### Post by jinx099 on 2007-09-27
do you mean I can just switch to the desktop profile as opposed to setting USE flags in my make.conf file?

---

### Post by igknighted on 2007-09-27
> **jinx099 said:**
> do you mean I can just switch to the desktop profile as opposed to setting USE flags in my make.conf file?

You can set a profile, and then make.conf modifies that profile.  Read this page for more info on the priorities of use flags:

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=2](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=2)

Basically you make the file /etc/make.default a symlink to the profile you want (in /usr/portage/profiles/).  Any use flags in make.conf will over-write the profile's setting.

---

### Post by cotcot on 2007-09-28
I installed gentoo a couple of years ago because of depency problems for several apps in other distros ubuntu included (opera, hugin, ...). I have to admit that some of these dependency problems are meanwhile solved in the more recent versions of ubuntu. 
From time to time the emerge of an app is interrupted but with reading the error message it is quickly solved (thanks to the excellents docs and a good working forum).

---

