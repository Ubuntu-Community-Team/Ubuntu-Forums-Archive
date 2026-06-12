---
title: "Kaffe Install"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Bob_Ascott on 2008-07-03
I am attempting to install the Kaffe JVM with the objective of making changes to the source code as part of a project.  I have been trying this  for a while and frustration is setting in.  I see that the Kaffe package can be installed with the package loader, and I see a ubuntu web page with:
    * kaffe_1.1.8.orig.tar.gz (13.5 MiB)
    * kaffe_1.1.8-3ubuntu1.diff.gz (80.4 KiB)
    * kaffe_1.1.8-3ubuntu1.dsc (1.4 KiB)
What must I do to download, confgigure, compile, and install Kaffe?  

I have been getting a series of errors from the ./configure command and randomly loading other packages is not resolving the issue.  

Bob Ascott, Austin, TX, USA

---

### Post by ramjet_1953 on 2008-07-04
If you are new to Linux, I suggest that you do a bit of reading-up on 'rolling your own' from sourcecode.

It can be a minefiled for the unwary. 

First, you need to install the [COLOR="Blue"]build-essential[/COLOR] package, which is a meta package that adds all of the goodies that you need to compile.

Type this in a terminal:

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

I would also install the [COLOR="Blue"]checkinstall[/COLOR] package.

[COLOR="Red"]sudo apt-get install checkinstall[/COLOR]

This package allows you to create a debian package and then use the package installer. It is then much easier to remove a package that you have compiled and installed, as it appears in Synaptic.

You also need to visit the website of Kaffe builder and have a good look around and search for a list of dependencies and install them.

It gets better.

When installing these dependencies, if there is also a development (dev) package associated with it, you will also need to install that.

As you can see, installing from sourcecode is not for newcomers, or the feint-hearted.

Regards,
Roger :cool:

---

### Post by Bob_Ascott on 2008-07-04
Thanx Roger, 
I appreciate your assistance.... I had been plodding on this path for quite a while, and after using the actual ubuntu source code downloads, the proper dependencies, and a little web searching for other issues, finally got both KAFFE and JAMVM to compile (with trivial modifications) and run.  Now on to learning their internals and making serious mods.  Thanx again, ''

Bob Ascott, Austin, TX, USA

---

### Post by jamesstansell on 2008-07-04
Hi Bob,

From looking at apt-get, this command may be of interest to you.
```
$ apt-get --build source kaffe
```

Also you should check out the GNU classpath project: [http://developer.classpath.org/mediation/](http://developer.classpath.org/mediation/)

Just curious - what kind of changes are you wanting to make?

-james.

---

### Post by wrathod on 2009-11-17
hello bob, im a newbie and i know little about compiling from the source code...
what i need to do is to get the JVM source code and make changes in it and run it then.
I would like to know more in detail about how did u get to the configuration and installation of the kaffe jvm....

---

