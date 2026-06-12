---
title: "Source Compiles"
date: 2007-04-17
forum: Packaging and Compiling Programs
---

### Post by ervt on 2007-04-17
This is a fairly general question/problem. I've just recently started using Ubuntu after having used Fedora and openSUSE. Compared to those two, successfully compiling source packages using the basic Ubuntu install as been an adventure. In fact I'd say only a fraction of the source packages I've tried compiled. This is especially problematic in that, at least at this point in time, few of the needed packages are available as binaries for Ubuntu. I guess what I need to have is a comprehensive list of the various useful library packages that aren't provided with a basic install.

Long question. Anyone have any simple answers?

---

### Post by amohanty on 2007-04-17
The answer is: it depends.
On:
1. What you are trying to compile?
2. Have you installed the required libraries?
3. Are you sure what you want is not in universe or some third-party repo?

There are tons of libraries for almost everything under the sun :) The base install is geared towards a basic desktop user so even the build tools are not installed by default. You can also install rpms via **alien** and source installs via **checkinstall**. At the end of the day, it depends on what you want, what are the dependencies of what your are trying to install. Technically it should compile unless the dependency version is newer than the one in the repos. 

If you have a specific example, it may be easier to tell you what you can do about it.

HTH
AM

---

