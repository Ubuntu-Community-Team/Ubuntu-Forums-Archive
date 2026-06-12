---
title: "Single file program installation"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by ekaspar on 2011-10-17
Why is there no apparent way to install programs offline in Debian based distros? Perhaps I'm totally missing something, but I've tried various ways of downloading packages and trying to install, but it never works.
Windows has .exe files, Redhat based distros even achieve this somewhat with .rpm. Why doesn't Debian have some equivalent?

---

### Post by egalvan on 2011-10-17
> **ekaspar said:**
> Why is there no apparent way to install programs offline in Debian based distros? **Perhaps I'm totally missing something**, but I've tried various ways of downloading packages and trying to install, but it never works.
Windows has .exe files, Redhat based distros even achieve this somewhat with .rpm. Why doesn't Debian have some equivalent?

Debian-based distros use **deb**, similar to RPM.

another way is to open Synaptic, choose what package/packages you want, then go to the "file" tab, and choose "Generate package download list".

take this list to any internet-connected machine and execute it...
(you may need a small program in MS-Windows)
this will download all packages needed...
you then take the resultant download and again use Synaptic to install the results.

---

### Post by mcduck on 2011-10-18
In addition to .deb, there's always .bin installers (which would be *exactly* like  the .exe installers you are used to in Windows, a single executable package containing both the program and an installer).

...and then there's [Autopackage]("http://en.wikipedia.org/wiki/Autopackage"), just as easy as .exes are, and contains all the dependencies and required stuff (meaning it's also just as inefficient as .exes are :D). Great system anyway, especially if you have no option of getting your computer online, but for some reason or other rather rarely used.

And finally, there is [Keryx]("http://keryxproject.org/"), a tool specifically made to make package management on off-line Ubuntu machines easy.

---

### Post by ekaspar on 2011-10-19
Well, I followed the instructions on the Ubuntu help page (all of which made sense) and this time actually got the .deb's to install! I'd tried it already with a couple other programs but it hadn't worked. Apparently the concept is correct. Thanks!

---

### Post by 3rdalbum on 2011-10-19
> **ekaspar said:**
> Why is there no apparent way to install programs offline in Debian based distros?

There is; it's known as a "binary installer" and is the direct equivalent of "Windows exe files" (which are just programs, FYI).

The difference is that binary installers are a waste of effort when you have a native package format such as Deb packages or RPMs, and they are grossly inefficient in terms of size compared to a proper packaging format. Also, quite inflexible - you can tell a package manager to install 30 Deb packages, but you can't do the same with a binary installer.

---

