---
title: "Installing lib32stdc++6 on Natty"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by aimless_prophet on 2011-12-11
Hello!

I'm having trouble installing the package lib32stdc++6 on my machine. When I try and install it via sudo apt-get install lib32stdc++6 it gives me:

```

E: Unable to locate package lib32stdc++6
E: Couldn't find any package by regex 'lib32stdc++6'

```

I tried looking for the .deb file to install it manually and I found this page: [http://packages.ubuntu.com/natty/lib32stdc++6](http://packages.ubuntu.com/natty/lib32stdc++6)

It doesn't seem to have a link to the .deb and at the side it says 'Download Source Package gcc-4.5'. Does this mean that this package is part of gcc-4.5? If not, do I need to add another repository for apt or am I not looking hard enough for the .deb file?

Thanks in advance!

---

### Post by llamabr on 2011-12-11
What kind of computer do you have, and why do you think you need to install this package?  Looks like gcc is a dependency, though it would be easy enough to install it.

---

### Post by aimless_prophet on 2011-12-11
It's a 32-bit amd laptop. The reason I think I need the package is that it is on a list of packages for compiling another piece of software. However, that list was for 8.04, so maybe some packages have been merged since then. I have gcc 4.5.2 already installed. I am just not sure if lib32stdc++6 was merged into another package.

---

### Post by arzali on 2011-12-12
that is the 32bit version of the library, meant for AMD64 systems.
If you have  a 32bit system, then you should use libstdc++6.
for compiling you need the dev packages.
My tip: ```
$sudo apt-get install build-essential 
```this is the first step if you want to build something from source :)

---

