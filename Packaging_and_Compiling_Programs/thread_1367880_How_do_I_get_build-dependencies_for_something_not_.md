---
title: "How do I get build-dependencies for something not in repositories?"
date: 2009-12-30
forum: Packaging and Compiling Programs
---

### Post by s3a on 2009-12-30
Usually, all I need to do is apt-get source, apt-get build-dep packagename, go to the specific folder then do dpkg-buildpackage and then install the created .deb files.

So basically, the src line in the /etc/apt/sources.list file allows me to get the build-dependencies of the source package I am about to compile but what about if it's a source file from a website and the program is not in the repositories. What do I do then for the build dependencies? All I know is that I need to "debianize" the source by using dh-make (dh_make command).

Any input would be GREATLY appreciated!
Thanks in advance!

---

### Post by falconindy on 2009-12-30
The author might be nice enough to provide a list of dependencies. I'm not sure what you goal is here, but if you can get your hands on a pre-compiled binary, you can use 'readelf -d' on it to figure out what .so's are linked to the file. If all else fails, you're in for a long routine of:

make
check error
install missing dependency
repeat

---

### Post by SevenMachines on 2009-12-30
maybe theres some better way to do it but in general i check things in this sort of vague order
* look for a INSTALL or README in the source dir, often dependencies/how to install are mentioned in there, if theres a web page, see if theres an install guide.
* if it has ./configure, use that, it will check for dependencies and report the missing ones
* then if all else fails, as falconindy mentions, run make and install any missing packages it fails on. 

sometimes you can also do something like
$grep -r '#include' src/*.h
or simlilar, but generally just running make and waiting for an error is as easy a method as any

and make a note of of the -dev packages you've installed if your going to package it! 
pbuilder is also useful if you're packaging, it will check that all the dependencies are satisfied in your debian/control file rather than just happening to be installed on your computer

---

### Post by s3a on 2009-12-30
The whole point of me making the .debs is not to use the:

```
./configure
make
sudo make install
```
method and to benefit from package management, etc.

I'm guessing that unless I do *sudo make install* (given that it needs root powers), I'm not doing anything "tragic" but what exactly does ./configure and make do?

---

### Post by SevenMachines on 2009-12-30
maybe a little of a simplistic explanation but say you have the source of a program which uses autotools (./configure, etc) you could install it by

(1) build and install 
$./configure - check and sets up the build environment, including looking for dependencies 
$make - build the program in the source directory
$sudo make install - install the built program into the various system directories

or ,

(2) use a packaging wrapper such as checkinstall
This carries out the same sort of steps as in (1) but does it inside a 'fake' environment, then uses this environment to create a deb package of what would have happened had you run 'make install' .This is not 'debianised' code but it can be very useful as it allows the package management system to take care of installation/removal. 

finally,

(3) Create debian packaging for the source
Here you create the debian/ directory with all its various components. this is similar to (2) as it builds and 'fake installs' the built source then uses this to create the .deb package. but it allows for a much greater level of control over building, installation, patches and any number of things that are needed to create good packages.

personally i find using checkinstall quite useful for quickly installing experimental programs i want to play with while allowing for easy removal using the packaging system when i'm done. 
for proper packaging of code you always need to create the full debian directory though. luckily, if the source code uses ./configure && make, this can be remarkably simple (importing a couple of cdbs files into debian/rules)

---

### Post by s3a on 2010-07-28
> **SevenMachines said:**
> maybe a little of a simplistic explanation but say you have the source of a program which uses autotools (./configure, etc) you could install it by

(1) build and install 
$./configure - check and sets up the build environment, including looking for dependencies 
$make - build the program in the source directory
$sudo make install - install the built program into the various system directories

or ,

(2) use a packaging wrapper such as checkinstall
This carries out the same sort of steps as in (1) but does it inside a 'fake' environment, then uses this environment to create a deb package of what would have happened had you run 'make install' .This is not 'debianised' code but it can be very useful as it allows the package management system to take care of installation/removal. 

finally,

(3) Create debian packaging for the source
Here you create the debian/ directory with all its various components. this is similar to (2) as it builds and 'fake installs' the built source then uses this to create the .deb package. but it allows for a much greater level of control over building, installation, patches and any number of things that are needed to create good packages.

personally i find using checkinstall quite useful for quickly installing experimental programs i want to play with while allowing for easy removal using the packaging system when i'm done. 
for proper packaging of code you always need to create the full debian directory though. luckily, if the source code uses ./configure && make, this can be remarkably simple (importing a couple of cdbs files into debian/rules)

I'm not trying to be rude but could you give me instructions I can follow? (that is simple and direct instructions) I know this is a late reply but it shows how badly I can't get the answer I'm looking for.

---

### Post by SevenMachines on 2010-07-28
hi, if you're still looking just for a way to avoid doing something like 'sudo make install' and instead want to use the package management system then the simplest way is to use checkinstall.
Go to your source directory
$ checkinstall

it'll ask you a few questions and then create a debian package based on what 'make install' would do. see how that goes and post if you have any problems obviously

---

