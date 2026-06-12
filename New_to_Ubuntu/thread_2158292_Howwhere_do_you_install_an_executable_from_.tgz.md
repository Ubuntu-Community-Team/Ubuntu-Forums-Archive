---
title: "How/where do you install an executable from .tgz"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by Eleutharios on 2013-06-28
I downloaded two programs (Paraview and gmsh) and am trying to install them manually since the vesions in the repositories for Ubuntu 12.04 are outdated. I have estracted the folders to Desktop. In each program's folder there are several subfolders but no installation instructions, ./configure, or makefile. In /bin there is an executable to run each program directly from the folder. I would like to install them so I can run them from the application menu or the command line though. How to I do this and where should I installl them to? Thanks in advance forthe help.

---

### Post by kabukiM0n0 on 2013-06-28
You unzip

tar  -zxvf   program.tar.gz 
tar  -zjvf  program.tar.bz2

You cd into the extracted folder

then

./configure
make
sudo make install

And you should be ready to roll.

And where to install it - that's automatically done for you, unless you want it somewhere specific which you have to specify. 
If you are looking for a programs folder, try 

whereis programname

---

### Post by sanderj on 2013-06-28
For gmsh: probably better off to activate the PPA. See [https://launchpad.net/ubuntu/+source/gmsh](https://launchpad.net/ubuntu/+source/gmsh)

---

### Post by Paqman on 2013-06-28
> **sanderj said:**
> For gmsh: probably better off to activate the PPA. See [https://launchpad.net/ubuntu/+source/gmsh](https://launchpad.net/ubuntu/+source/gmsh)

+1 to this. There's also a PPA of [paraview]("https://launchpad.net/~gladky-anton/+archive/paraview") available. It's from an individual, but they do seem to be a contributor to gmsh.

In general the solution to the repos being out of date isn't to install software from a tarball. Doing so means you're stepping outside the package manager, which is a bad idea. It can lead to problems with stability and security. You're much better off using a PPA, 3rd party repository, or a .deb file, all of which install through the package manager and don't break the dependency system on your machine.

---

### Post by Lars Noodén on 2013-06-28
> **Paqman said:**
> +1 to this. There's also a PPA of [paraview]("https://launchpad.net/~gladky-anton/+archive/paraview") available. It's from an individual, but they do seem to be a contributor to gmsh.

In general the solution to the repos being out of date isn't to install software from a tarball. Doing so means you're stepping outside the package manager, which is a bad idea. It can lead to problems with stability and security. You're much better off using a PPA, 3rd party repository, or a .deb file, all of which install through the package manager and don't break the dependency system on your machine.

+1 to the +1  ;)

A step in between the PPA and the standard 12.04 repository would be the backports repository.  Depending on the application, there may be updates available from there.

---

