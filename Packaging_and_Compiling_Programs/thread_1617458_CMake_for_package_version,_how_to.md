---
title: "CMake for package version, how to?"
date: 2010-11-09
forum: Packaging and Compiling Programs
---

### Post by jiapei100 on 2010-11-09
Hi, all:

I'm trying to build my own package using cmake version 2.8.2 .
Everything goes fine until I was trying to install it by myself on my own computer.

According to my habit, I'd love to install it in such a way:

```
$mkdir build
$cd build
$ccmake ../
$make
$checkinstall --fstrans=no
```

Problem occurs when I was trying to checkinstall my package.
> *****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@jiapei-laptop ]
1 -  Summary: [ Package created with checkinstall 1.6.2 ]
2 -  Name:    [ build ]
3 -  Version: [ 20101109 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ build ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ build ]
12 - Conflicts: [  ]
13 - Replaces: [  ]


I would like option 2 - Name should not show "build", but the name of my package; and I was hoping option 3 - Version should not show "20101109", but the version of my package.

I understand I can pick up these two options and manually update the values in these two options in sequence. However, that's not what I expected. I seriously hope the default values are already in there because this is not a subversion, but a standard release. How to?

Please give me a hand.


Best Regards
JIA

---

### Post by SevenMachines on 2010-11-11
As far as i can see, checkinstall (its not super-intelligent) makes guesses for package name and version based on...

* Package Directory - It tries to extract a name from this ie, if the source directory is 
hello-0.1
hello
etc..
it should get a package name of hello

*Package Version seems to be a decending list of 'best guesses'. 

1. Try extracting a version from the source directory name, eg
hello-0.1
version = 0.1

2. If not then try to find a #define VERSION line in the build config.log

3. lastly, if we've got nothing yet then just use todays date

In general i find its generally better to specify these things at the command line
$ sudo checkinstall --pkgname hello --pkversion 1.0 --pkgrelease 1

---

### Post by jiapei100 on 2010-11-11
Thank you so so so much.
Very clear answer.

Best Regards
JIA

---

