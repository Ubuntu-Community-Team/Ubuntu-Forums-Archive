---
title: "Issues with 'make'"
date: 2012-04-27
forum: Packaging and Compiling Programs
---

### Post by NickSH on 2012-04-27
Hi all,
I am trying to get mtrack working on mac-air.  It didn't install correctly when I ran the script used to update drivers.

So I am following these instructions from the mtrack thread, posted by helios 747.


Follow these instructions.


Install git if you don't have it already

Code:
sudo apt-get install git
Get a copy of the stable code for the driver

Code:
git clone [https://github.com/BlueDragonX/xf86-input-mtrack.git](https://github.com/BlueDragonX/xf86-input-mtrack.git)

cd into the directory

Code:
cd xf86-input-mtrack

Install the required dev libs for compiling

Code:
sudo apt-get install xorg-dev libmtdev-dev

compile

Code:
make

Install the driver

Code:
sudo make install

edit your /etc/X11/xorg.conf (if this does not exist, create it.)

Code:
sudo nano /etc/X11/xorg.conf

Put this code into it to activate the driver

Code:
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
 EndSection
Reboot your computer, or restart X to activate the driver.

When I get to the compile step, I get the following error..

make: *** No targets specified and no makefile found. Stop.

However, using ls, I am able to see the file

Makefile.am in the xf86-input-mtrack directory.

Anythoughts on why this might not be working?

Thanks,
Nick

---

### Post by dumdidum on 2012-04-27
> **NickSH said:**
> H
When I get to the compile step, I get the following error..

make: *** No targets specified and no makefile found. Stop.

However, using ls, I am able to see the file

Makefile.am in the xf86-input-mtrack directory.

I can't really help you with the problem at hand (hopefully, someone else will chime in) but I can explain you why you get the error.

if you run "make" without the -f option, make looks for files named GNUmakefile, makefile, and Makefile. You're getting the error as no file with one of those names is present in the directory. (Makefile.am doesn't help.)

Makefile.am is typically there for automake. So you probably need to use the autotools. Again, unfortunately, I'm not familiar with what you're trying to build so hopefully someone else will chime in.

---

### Post by marinara on 2012-04-27
make sure you're in the right directory and run autogen.sh (if there) and configure

---

### Post by NickSH on 2012-04-28
Ok.  I tried to run autogen.sh, and it says command not found.  When I tried automake, it returned that automake was not found but could be found in the following packages:
automake
automake1.10
automake1.4
automake1.9
automake1.7.

I'm wondering, since the file in question is an automake file, if I should just sudo apt-get install one of the automake packages, and then run automake?  Will that accomplish the same task that the make command would have?

Thanks,
Nick

---

### Post by marinara on 2012-04-28
please run ./configure
then run make

---

### Post by NickSH on 2012-04-28
There is no such file...the computer says.

There is a configure.h.in and a configure.ac file in the directory.  These are the only two configure files when I type ls -a.

Sorry for all the newb questions....I've never used make before, not to mention automake.

---

### Post by marinara on 2012-04-29
the reason you cant build mtrack is because they didn't provide autotools in the git archive
you might retry by downloading the tar.gz which will hopefull include autotools

---

### Post by r-senior on 2012-04-29
This is a painful build! If you don't want lots of development libraries installed on your system, I'd strongly recommend doing all of this in a virtual machine.

OK, for reference, here is the directory listing from the git clone:

```
$ ls
config.h.in   COPYING  debian  include      README.md  tools
configure.ac  CREDITS  driver  Makefile.am  src

```

We can see from configure.ac and Makefile.am that it uses GNU autotools, i.e. automake and autoconf. Source archives like this often include the products of those tools, in which case it's just a matter of running './configure' and 'make install', but this one needs you to run those tools first.

Sometimes a package will provide 'autogen.sh' to help with this, but this one doesn't do that either. So let's make one in the top-level directory -- it will be easier to re-run if things go wrong. (This package requires libtool, which you won't find in all autogen.sh examples):

*autogen.sh*
```
#!/bin/bash

aclocal \
&& libtoolize -c -f -i \
&& automake --add-missing \
&& autoconf

```

Then run it (assuming the xorg-dev and libmtdev-dev are installed)

```
$ chmod +x autogen.sh
$ ./autogen.sh
```

If that doesn't work, you are probably missing some of the basic build tools. The easiest way to install them in one shot is:

```
$ sudo apt-get install build-essential
```

When I tried it, I was also missing xutils-dev and libtool, so:

```
$ sudo apt-get install xutils-dev libtool
```

Run 'autogen.sh' again:

```
$ ./autogen.sh
```

At that point you should end up with a 'configure' file. So go ahead and compile:

```
$ ./configure
$ make

```

You could do 'sudo make install' at that point but, to avoid going through this torturous process again, you can build a .deb file and squirrel it away somewhere in case you ever need to reinstall it:

These steps are optional if you successfully use 'make install':

Install the tools to build .deb files:

```
$ sudo apt-get install gnupg pbuilder ubuntu-dev-tools bzr-builddeb apt-file
```

Build the .deb file:

```
$ debuild -us -uc

```

Then find the .deb file, which will be one level up:

```
$ cd ..
$ ls *.deb
```

Save the .deb file somewhere safe. Install with:

```
$ dpkg -i xserver-xorg-input-mtrack_0.2.0_*.deb
```

There, that was simple wasn't it? :lolflag:

Ideally the developer would provide a PPA that allows you to install this -- they've done packaging for Debian/Ubuntu but I couldn't find a PPA.

---

### Post by howefield on 2012-04-29
Thread moved to the "*Packaging and Compiling Programs*" forum.

---

### Post by NickSH on 2012-04-29
Sorry to be such a newb here, but when you say


Sometimes a package will provide 'autogen.sh' to help with this, but this one doesn't do that either. So let's make one in the top-level directory -- it will be easier to re-run if things go wrong. (This package requires libtool, which you won't find in all autogen.sh examples):

Do you mean that I should create a text file in the root directory?  Or are you saying that I should put this file in the directory that directly contains the Makefile.am.

Also, do I just use something like nano to create this (i.e. cd into the directory I want to create the file in, open nano, type and save?). 

Thanks,
Nick

---

### Post by r-senior on 2012-04-29
That's right. You can use any text editor -- gedit, nano, vi, etc.

Just make a file in the same directory as configure.ac, call it autogen.sh and copy/paste paste the stuff I showed. By default, scripts like this are not executable, hence this step:

```
$ chmod +x autogen.sh
```

To run a script from the current directory, you prefix with './', which means current directory.

```
$ ./autogen.sh
```

In all cases, you don't type the '$' sign -- that's your command prompt.

I tested this on Ubuntu 12.04, by the way, not on Lubuntu. But it should work the same. Follow the steps and you should be OK but let me know if you get errors.

---

### Post by NickSH on 2012-04-29
Thanks for all your help.

The installation seemed to go fine...well, I didn't recieve any errors anyway.

However, after rebooting, and double checkings the /etc/X11/xorg.conf file, the driver does not seem to actually be working (i.e. I can't scroll).

Anythoughts?

Thanks,
Nick

---

### Post by r-senior on 2012-04-29
Could you confirm the installation was OK by checking that you have the following two files:

```
/usr/local/lib/xorg/modules/input/mtrack_drv.la
/usr/local/lib/xorg/modules/input/mtrack_drv.so

```

I don't know anything about the program itself -- just how to compile it. I'm assuming you did the required setup in xorg.conf?

If you have the driver installed and it's not working, you should probably open another question in General Help, or perhaps in [Apple Users]("http://ubuntuforums.org/forumdisplay.php?f=328")? There's already a thread going in there about the MacBook Air.

---

### Post by NickSH on 2012-04-30
It appears to have installed, as both of the files you mentioned are there.  Also, I was able to find the configuration file mentioned in the post, so it should be good to go.

I'll start a new thread in the macbook section and see what I can figure out there.

Thanks for your help.

Nick

---

