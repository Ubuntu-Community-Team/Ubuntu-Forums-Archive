---
title: "Cannot install packages for armhf on amd64"
date: 2018-10-13
forum: Packaging and Compiling Programs
---

### Post by Joseph_Foster on 2018-10-13
I am trying to install Lua libraries for for cross compiling to my BeableBone Black, but I get the folling after running **sudo**** apt-get build-dep -****aarmhf**[B] lua5.2:

[/B]
```

Reading package lists... Done
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
builddeps:lua5.2:armhf : Depends: libreadline-dev:armhf but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I would just compile on the BeagleBone itself, but it takes 45 seconds per compile so I'm trying to switch to compiling on my development desktop running amd64. All my code that I cross compile without any 3rd party libraries builds and runs fine.

I've been trying for hours to get this set up, any help is appreciated!

---

