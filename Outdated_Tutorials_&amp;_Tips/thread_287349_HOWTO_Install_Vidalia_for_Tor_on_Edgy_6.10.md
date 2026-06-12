---
title: "HOWTO: Install Vidalia for Tor on Edgy 6.10"
date: 2006-10-28
forum: Outdated Tutorials &amp; Tips
---

### Post by j-strap2 on 2006-10-28
Vidalia is a nice user-interface for the Tor anonymising proxy. It sits nicely on the taskbar and provides useful information such as bandwidth and node locations.

First, install the packages gt4-dev-tools and qt4-designer. qt4-designer will install a host of -dev packages it is dependent on.

Download and the vidalia source code from [http://www.vidalia-project.net/download.php](http://www.vidalia-project.net/download.php) and expand into a folder.

In a terminal window, go to the vidalia source folder and compile it with the following commands:

```
QMAKE=/usr/bin/qmake-qt4
./configure
make
sudo make install
```

Now edit the torrc file to enable the control port (9051 by default):

```
sudo kate /etc/tor/torrc
```

Uncomment the line '#Control_Port 9051' by removing the #. Save the changes.

Now, restart the Tor service:

```
sudo /etc/init.d/tor restart
```

Run vidalia:

```
vidalia
```

voila!

---

### Post by ephman on 2006-10-29
hi,

just a couple issues.  
1) the icon on my panel is missing, all i get is a grey box.  any idea about how to get the icon up there?  no biggie though, i kind of find it ironic.

2) i'm unable to write any configurations to the disk.  i tried changing permissions to the torrc file but to no avail...

great howto thanks!!!  never knew something like this actually existed.

thanks for the bandwidth,
ephman

---

### Post by AgenT on 2006-10-29
Very impressive! This looks to be a really nice project and a great addition to Tor.

---

### Post by beefcurry on 2006-11-14
Well a ive got a few problems with this HOWTO which is essentailly the same one on the vidalia website

#1. No response after typing QMAKE=/usr/bin/qmake-qt4 <- i have install all required qt4 packages

#2. After typing ./configure:
configure: Configuring vidalia 0.0.9...
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

#3. After typing make:
make: *** No targets specified and no makefile found.  Stop.

Ive followed the instructions word by word..so where could i have gotten wrong?

---

### Post by j-strap2 on 2006-11-19
beefcurry, you need to install the compiler and associated packages. Simplest way to do this is to install the package build-essential, which will install all the required packages through its dependencies.

---

### Post by beefcurry on 2006-11-19
> **ephman said:**
> hi,

just a couple issues.  
1) the icon on my panel is missing, all i get is a grey box.  any idea about how to get the icon up there?  no biggie though, i kind of find it ironic.

2) i'm unable to write any configurations to the disk.  i tried changing permissions to the torrc file but to no avail...

great howto thanks!!!  never knew something like this actually existed.

thanks for the bandwidth,
ephman

Thanks to j-strap i have installed vidalia fine but then im left with the exact same problem as ephman. Anyone have solutions?

---

### Post by j-strap2 on 2006-11-20
This problem applying and saving the settings in Vidalia seems to be a bug that the developers are aware of. Vidalia does not seem to take into account that Ubuntu runs Tor as a service with its own user account.

---

### Post by TrinitronX on 2007-01-21
I'm having troubles with installing the qt4-designer package.
```
The following packages have unmet dependencies.
  qt4-designer: Depends: libqt4-dev but it is not going to be installed
E: Broken packages

```

Tracing the dependencies back through, trying to install libqt4-dev:
```
The following packages have unmet dependencies.
  libqt4-dev: Depends: xlibmesa-gl-dev but it is not going to be installedor
                       libgl-dev
              Depends: libglu1-xorg-dev but it is not going to be installedor
                       libglu1-mesa-dev but it is not going to be installedor
                       libglu-dev
E: Broken packages
```

Then, finally the problem:
```
The following packages have unmet dependencies.
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
                    Depends: libgl1-mesa-dev but it is not going to be installedor
                             libgl-dev
```

So I think this is something from the beryl repository that ended up making it impossible to get the libqt4-dev package I need to build vidalia.  I'm not too savvy with packages yet, so I'm not sure how to resolve this dependency problem without breaking things.  The version of libglu1-mesa I have appears to be the same version as needed, however It's cvs.  So, I'm hoping that there's a way to force this package dependency to be ignored without breaking anything.

---

### Post by aashay on 2007-03-19
Sorry for bumping an old thred .. but instead of threee steps:
```

sudo /etc/init.d/privoxy start
sudo /etc/init.d/tor start
vidalia
```
Is it possible to run all three as user  "debian-tor" by just launching vidalia alone?
Vidalia tries to start tor as the current user instead of "debian-tor"... for which tor refuses to start. Also gksu vidalia fails to work.
I tried taking ownership of the config / log / lib files for tor... but then tor just crashes midway

---

### Post by beefcurry on 2007-04-06
btw, i just noticed a error in your howto. You wrote:

> gt4-dev-tools

it is ment to be qt4-dev-tools. Q not G :D

---

### Post by dimeotane on 2007-04-09
vidalia looks cool, but ..

25 megs to install gt4-dev-tools first ?

maybe I'll wait until it's packaged properly...

---

