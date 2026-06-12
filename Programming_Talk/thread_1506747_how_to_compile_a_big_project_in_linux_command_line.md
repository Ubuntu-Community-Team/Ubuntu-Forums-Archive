---
title: "how to compile a big project in linux command line?"
date: 2010-06-10
forum: Programming Talk
---

### Post by jeremy28 on 2010-06-10
Hello all
I've got the "OpenCryptoKi" project source from "sourceforge.net" at here:
[http://sourceforge.net/projects/opencryptoki/](http://sourceforge.net/projects/opencryptoki/)
But I don't know how should I compile and build it by "GCC" or "Make"?!
I have ubuntu 9.04 and I've set the linux runlevel at 3, but I'm not so familiar with compiling such project at 
commandline environment of linux!
Please help me how to compile this?!!
I'm so hurry!!
THX

---

### Post by geirha on 2010-06-10
I had a quick look at it, and it appears to lack some documentation on the build process. It appears though, that you're supposed to run the bootstrap.sh script first.
```

chmod +x bootstrap.sh
./bootstrap.sh

```
That should generate the configure script so that you can run the "regular" set of commands:
```

./configure
make
sudo make install

```

Make sure you at least have the [build-essential](apt:build-essential) package installed first. You'll probably also need some dev packages; if ./configure complains that it can't find some library **foo**, then do a package search like ```
aptitude search 'lib**foo**.*-dev'
``` and install the package that looks "most right" and run ./configure again.

---

### Post by soltanis on 2010-06-10
You don't have to be in runlevel 3 in order to compile something. In general, avoid runlevel 3 unless you know what you're doing.

Most projects use autotools to compile:

```

./configure (options)
make
sudo make install

```

Because you are on an Ubuntu system, I suggest you do the following instead of the last step (make install). First install the checkinstall package:

```

# before compiling
sudo apt-get install checkinstall

# when compiling
./configure
make
sudo checkinstall

```

Checkinstall will generate a package for you that you can uninstall through your package manager, simplifying keeping your system tidy.

Also, sometimes people don't have the ./configure step, or in this case, there is an extra step before the configure step (which is really kind of pointless -- you have a script that generates a configure script that generates a makefile? Why not just have a makefile?).

---

### Post by Roptaty on 2010-06-11
> **soltanis said:**
> 
Also, sometimes people don't have the ./configure step, or in this case, there is an extra step before the configure step (which is really kind of pointless -- you have a script that generates a configure script that generates a makefile? Why not just have a makefile?).

OT:

Having a bootstrap/autogen.sh is NOT pointless. If you write an application using automake/autoconf you will write Makefile.am and configure.in files with a lot of macro functions. These files need to be converted into configure and Makefile.in (the configure script turns Makefile.in into Makefile). The configure scritps check for functions, type of system, sizes, libraries and so on, to ensure portability. Most source packages have also options to enable/disable features into the configure script. 

However, distributed source packages should have been boostrapped/autogen before release. Source from software repositories must most likely be bootstrapped. 

There are other build systems which dont have the configure step, but a similiar step (for instance CMake and QMake).

---

