---
title: "Xerces Circular Dependency Problem"
date: 2009-11-18
forum: Programming Talk
---

### Post by jcraig on 2009-11-18
I am building xerces on a Intel x86 machine targeting a hardware powerpc platform. I am including xerces in my application. I need to configure the shared library file for the powerpc. I am using KDevelop to build my application and I am linking the xerces shared library in my makefile. I found that I could download the debian package with a powerpc build from this website [[COLOR=#444444]https://launchpad.net/ubuntu/+source.../+build/978213[/COLOR]]("https://launchpad.net/ubuntu/+source/xerces-c/3.0.1-1/+build/978213"). I could invoke a build by using the command dpkg-cross -a powerpc -A -b <package name>.deb. Each time it would say it couldn't install the package because of a dependency, so I would find the dependency, which was based on another dependency. I ran into the problem, I can't install libgcc1 because it has a dependency of libc6. I can't install libc6 because it has a dependency of libgcc1. I believe that this is my last dependency to install to get the entire package to work, but I haven't found a way around the dependency issue. Any help on the circular depency would be much appreciated.

---

