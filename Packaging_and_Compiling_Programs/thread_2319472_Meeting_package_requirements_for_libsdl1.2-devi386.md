---
title: "Meeting package requirements for libsdl1.2-dev:i386 on an x86-64 system"
date: 2016-04-04
forum: Packaging and Compiling Programs
---

### Post by colin-bourassa on 2016-04-04
I'm attempting to build a 32-bit project (which is using CMake) on my x86-64 system. The project depends on SDL1.2, which I think means that I need libsdl1.2-dev:i386 installed on my system. However, when I attempt to install that package:

```
$ sudo apt-get install libsdl1.2-dev:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libsdl1.2-dev:i386 : Depends: libglu1-mesa-dev:i386 but it is not going to be installed or
                               libglu-dev:i386
E: Unable to correct problems, you have held broken packages.
```

If I attempt to install libglu1-mesa-dev:i386 or libglu-dev:i386 manually, apt-get tells me that it will first uninstall a large number of packages, including all of the Qt5 dev libraries. I certainly do not want this. What should I do to satisfy the requirement for libsdl1.2-dev:i386?

--Colin

---

