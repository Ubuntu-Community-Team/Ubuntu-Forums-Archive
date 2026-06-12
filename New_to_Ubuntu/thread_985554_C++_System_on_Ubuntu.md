---
title: "C++ System on Ubuntu"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by euopun on 2008-11-17
I am trying to install a C++ compiler on my distribution of ubuntu and i cant seem to find one.

A C++ compiler is required for an apache web server on linux right? whats the best one for ubuntu 8.04 hardy heron?

---

### Post by OutOfReach on 2008-11-17
People usually use gcc.

You can install all tools necessary to compile something with this command:
```

sudo apt-get install build-essential

```

---

### Post by euopun on 2008-11-17
> **OutOfReach said:**
> People usually use gcc.

You can install all tools necessary to compile something with this command:
```

sudo apt-get install build-essential

```
Just so you know i have the UI version of 8.04 not the server version.
Ok so i do this and the terminal spews out(Even when i have the install cd in the drive):
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

```
I have tried downloading gcc and ended up with a new OS... I have had a problem downloading any updates on my comp whenever i try to update simply because i set the wrong proxy since my install:
```

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'philsproxy'

```

---

### Post by jenkinbr on 2008-11-17
> **euopun said:**
> I am trying to install a C++ compiler on my distribution of ubuntu and i cant seem to find one.

A C++ compiler is required for an apache web server on linux right? whats the best one for ubuntu 8.04 hardy heron?
C++ is only required if you want to compile the apache server (I would highly recommend using apache2) from souce.  Ubuntu has a great apache2 binary in the repositories as well as all the needed parts.  You may not have the bleeding-edge newest, but rest assured - critical updates are made when security risks are found, so security shouldn't be an issue.

(now if they would stop messing with the virtualhost naming system, I would be happy)

---

### Post by euopun on 2008-11-17
I have followed the instructions at [http://httpd.apache.org/docs/2.2/install.html](http://httpd.apache.org/docs/2.2/install.html) and when i get to configuring part it says there is a problem with the C compiler. When i try to update the build-essential it says i have a problem with the source.

---

### Post by DGortze380 on 2008-11-17
Short answer. Don't bother.

gcc is installed by default. (g++ is included for c++)
if it's not, run sudo apt-get install build essential.

---

### Post by Swerve1000 on 2008-11-17
Yeah, gcc should be installed by default. Check in Synaptic and it should be under installed programs, the Ubuntu icon next to it signifying it's part of the standard installation.

The debugger is much more easy to understand than Visual Studio I will say.

---

### Post by jenkinbr on 2008-11-17
> **DGortze380 said:**
> Short answer. Don't bother.

gcc is installed by default. (g++ is included for c++)
if it's not, run sudo apt-get install **build-essential**.

fixed your code in the quote.

---

### Post by snova on 2008-11-17
Just install the apache2 package, and don't bother building it.

---

### Post by euopun on 2008-11-17
okok but what does this mean when i try to configure the apache webserver?
```
checking for chosen layout... Apache
checking for working mkdir -p... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1

Configuring Apache Portable Runtime library ...

checking for APR... reconfig
configuring package in srclib/apr now
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
Configuring APR library
Platform: i686-pc-linux-gnulibc1
checking for working mkdir -p... yes
APR Version: 1.3.3
checking for chosen layout... apr
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr

```
I have just looked in the synaptic package manager and it looks like i have the gcc installed... still it says the compiler cannot create executables.

---

### Post by jenkinbr on 2008-11-17
> **snova said:**
> Just install the apache2 package, and don't bother building it.
+1 to that.

as I mentioned above, security updates are constantly applied and the binary is far easier to install than from source

Ubuntu is not like slackware or similar - you don't need to compile everything from source.  Chances are, it's been done for you already.

---

