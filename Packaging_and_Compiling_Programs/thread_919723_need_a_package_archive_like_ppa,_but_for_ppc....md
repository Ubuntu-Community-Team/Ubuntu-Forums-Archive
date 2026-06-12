---
title: "need a package archive like ppa, but for ppc..."
date: 2008-09-14
forum: Packaging and Compiling Programs
---

### Post by NiN on 2008-09-14
Hi there,

I need a ppa on my own machine, as I need to compile the packages for ppc.
Since ppc is not supported officialy any more, the ubuntu ppa archives do not support this architecture.

Can someone point me to a quick & dirty howto to achieve the following:

 -> monitor a source archive (need pulseaudio + network-manager development packages)
 -> fetch more recent source packages and compile them for ppc
 -> add them to a local repository

I don't know much about how this process works (on the repository side, for monitoring and fetching I'm building a script ), so any help would be appreciated.

---

### Post by bobbocanfly on 2008-09-16
There is a tool called Deb-o-matic which is basically like a build daemon built on to of pbuilder. Of course to build ppc packages, you will need a PPC computer. 

From this you could use your script to get the result from the pbuild qand publish it in a repository format. If you are willing to wait a few weeks I just wrote a modules system (plugins) for debomatic that should be getting merged in soon to trunk. It can currently be found [https://code.edge.launchpad.net/~bobbo/debomatic/bobbo-dev](https://code.edge.launchpad.net/~bobbo/debomatic/bobbo-dev). Of course you would have to write the module yourself (not too difficult, just a bit of python knowledge needed) and it isnt perfectly stable yet but it should work for you just fine.

---

