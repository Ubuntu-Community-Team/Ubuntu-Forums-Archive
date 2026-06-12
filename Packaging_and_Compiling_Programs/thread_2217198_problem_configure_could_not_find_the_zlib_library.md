---
title: "problem: configure could not find the zlib library"
date: 2014-04-16
forum: Packaging and Compiling Programs
---

### Post by jmbell on 2014-04-16
I've been trying to install some software with a zlib dependency (as well as a few others). The typical procedure for this is to install the packages:  **zlib1g ** and **zlib1g-dev**; however, once installed (and after I've rebooted for safe measure), the configuration script run with the necessary prefix ```
 ./configure --prefix=/opt/ lscsoft 
``` returns the following:

```
checking for ZLIB... no
checking for library containing compress... no
configure: error: could not find the zlib library
configure: error: ./configure failed for lal
```

I've attached the configuration log here: [ATTACH]252105[/ATTACH] for the software I'm trying to configure. I've tried the lib32 versions of zlib in the repos with no success as well. Note, too, that I've installed most of the dependencies to /opt/lscsoft as instructed here: [https://www.lsc-group.phys.uwm.edu/daswg/docs/howto/lscsoft-install.html](https://www.lsc-group.phys.uwm.edu/daswg/docs/howto/lscsoft-install.html). Once installed, I'm supposed to be able to run ```
 ./00boot && ./configure --prefix=/opt/lscsoft && make install 
``` as per the instructions here: [https://www.lsc-group.phys.uwm.edu/daswg/docs/howto/lal-install.html](https://www.lsc-group.phys.uwm.edu/daswg/docs/howto/lal-install.html), though in this post I'm only concerned with solving the configuration problem I'm having. Once it's resolved, the rest of the code is easily installed.

I'm not sure what to do from here. I've tried installing from the source code provided at [www.zlib.net]("http://www.zlib.net"), which worked on my laptop after the apt-get method did not. For it to work on the laptop, though, I had to install from source as root, which made me little nervous. Sadly, this approach did not work on my desktop.

FYI, I'm running Kubuntu 13.10 on my laptop and desktop. This problem has arisen each time I've reinstalled on a new system (I've tried using Arch, Manjaro, and Kubuntu). Interestingly, after installing Arch Linux, I had to download all the dependencies from source to work. Those stored in the Arch repos gave me the same error message as those in debian's apt-get repos. The same was required for two other dependencies, "libframe" and "metaio", which I had to install from the arch user repository instead of the lscsoft data analysis packages found at: [www.lsc-group.phys.usm.edu/daswg/download/software/source]("http://www.lsc-group.phys.usm.edu/daswg/download/software/source").

I've been searching for a while on google and can't seem to find anything but recommendations to install from source, and more often from the apt-get repos. If these won't work, I hope someone else can help me find a method that will! Hopefully I've provided sufficient details.

---

### Post by oldos2er on 2014-04-16
Moved to Packaging & Compiling Programs.

---

### Post by jmbell on 2014-04-16
Is there anything I can do to make my post clearer? This problem has occured almost each time I try to reinstall on another system/OS. Oddly, each time seems to require different procedures to make the software function properly. Certainly, it's something I'm doing wrong, but I haven't figured out what.

---

### Post by steeldriver on 2014-04-16
Is the software you're trying to compile publicly available? I looked for it on the site and was going to see if I could replicate the problem but could only find prerequisite packages and related software - not the lscsoft source itself

---

### Post by jmbell on 2014-04-16
The prereqs are "lscsoft", whereas the software I'm installing is called "lalsuite". As I understand it, lalsuite is not publicly available; however, I believe you can configure/install the read-only version via these instructions: [https://www.lsc-group.phys.uwm.edu/daswg/docs/howto/advanced-lalsuite-git.html#clone](https://www.lsc-group.phys.uwm.edu/daswg/docs/howto/advanced-lalsuite-git.html#clone). 

All of lscsoft can be installed from the shell script found here: [https://www.lsc-group.phys.uwm.edu/daswg/docs/howto/lscsoft-install-x.sh](https://www.lsc-group.phys.uwm.edu/daswg/docs/howto/lscsoft-install-x.sh). HTML Instructions are here: [https://www.lsc-group.phys.uwm.edu/daswg/docs/howto/lscsoft-install.html](https://www.lsc-group.phys.uwm.edu/daswg/docs/howto/lscsoft-install.html). I've done the following after downloading the shell script to ~/Downloads:

```

sudo mkdir /opt/lscsoft
sudo chown username /opt/lscsoft
bash lscsoft-install-x.sh --from-tar=/opt/lscsoft

```
Then I added the necessary lines to my bash .profile and .bashrc. Lastly I did the following:
```

cd ~/src
git clone git@repository.location:lalsuite.git ~/src/lalsuite
cd lalsuite
./00boot && ./configure --prefix=/opt/lscsoft --disable-laldetchar && make -j4 install

```

Again, it's during the configure where the compile fails. If it doesn't fail on zlib, it will fail on lalframe and metaio in sequence.

---

### Post by steeldriver on 2014-04-18
I've had another look at this, and as far as I can tell it's a case of lasuite (and the overall lscsoft framework) being incompatible with more recent versions of zlib

I was able to get everything to configure and make after building an older local version of zlib (1.2.3.5) and setting an appropriate PKG_CONFIG_PATH

---

### Post by jmbell on 2014-04-21
I tried installing zlib 1.2.3.5; however, the same error message was produced. Could you specify how you set your PKG_CONFIG_PATH? Mine appears to contain all pertinent directories. **echo $PKG_CONFIG_PATH** returns:
```
/opt/lscsoft/non-lsc/lib/pkgconfig:/opt/lscsoft/libframe/lib/pkgconfig:/opt/lscsoft/libmetaio/lib/pkgconfig:/opt/lscsoft/non-lsc/lib/pkgconfig:/opt/lscsoft/libframe/lib/pkgconfig:/opt/lscsoft/libmetaio/lib/pkgconfig:/opt/lscsoft/non-lsc/lib/pkgconfig:/opt/lscsoft/libframe/lib/pkgconfig:/opt/lscsoft/libmetaio/lib/pkgconfig:/opt/lscsoft/non-lsc/lib/pkgconfig:/opt/lscsoft/libframe/lib/pkgconfig:/opt/lscsoft/libmetaio/lib/pkgconfig:/opt/lscsoft/non-lsc/lib/pkgconfig:/opt/lscsoft/libframe/lib/pkgconfig:/opt/lscsoft/libmetaio/lib/pkgconfig:
```

---

### Post by steeldriver on 2014-04-22
I *think* that what worked for me in the end was to configure and install the older zlib into **/usr/local** and then run sudo ./lscsoft-install-x.sh --from-tar=/opt/lscsoft and then configure and make lalsuite

I originally tried to install zlib to /opt/lscsoft/non-lsc since it seemed like the 'right' place to put it, but no matter what I did with configure parameters (e.g. --with-zlib=/opt/lscsoft/non-lsc) or PKG_CONFIG_PATH got ignored (at least by the lscsoft-install-x.sh script - I didn't try it for lalsuite because I couldn't get past that)

---

### Post by jmbell on 2014-04-24
No luck yet. I tried your suggestions, but I'm still getting the same message. FYI, I can run the lscsoft-install shell script without any problems. It's when I run the configure script for lalsuite that I run into the zlib problem.

---

### Post by steeldriver on 2014-04-24
You may need to remove the 'system' zlib1g-dev so that the ./configure script finds your locally build version first

---

### Post by jmbell on 2014-04-27
Alright! I've determined the problem. It wasn't the version of zlib, though it was worth looking into. Instead, it was that pkg-config from lscsoft was overwriting pkg-config from the apt repos. I reinstalled pkg-config and added the following to my .bashrc:

```
export PKG_CONFIG=/usr/bin/pkg-config
```

After logging off and then back on, I was able to run the configure script and install without any errors.

Thank you so much for your time, steeldriver. I'll mark this as solved.

---

### Post by jmbell on 2014-05-06
It turned out that the shell script installed versions of the software that were too old for the lalsuite code to utilize. I removed them and updated my pkg-config environment variable accordingly. Once done, the installation went smoothly. Wish I had realized that earlier! Thanks for your help, steeldriver. If nothing else, this might help promote an update of the online documentation for lscsoft/lalsuite.

---

