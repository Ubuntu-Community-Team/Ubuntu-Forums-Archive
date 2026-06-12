---
title: "NS2 files"
date: 2013-12-14
forum: New to Ubuntu
---

### Post by ichie on 2013-12-14
Hello,
im new at Ubuntu and NS2 so i have a question.
I installed NS2 using sudo apt-get ns2 and it all works fine
but i cant find where the files where installed in order o modify some of them. Specifically i want to modify aodv.h and aodv.cc for a project of mine.

With the other method of installing ns2 (nsallinone) i know where the files are because i choose where to put them, but i have other problems with this method so i gave up.

Can anyone please help me? Where did the files go? I searched for the installation via synaptics but is isnt there but the program works fine.
Thnx everyone in advance

---

### Post by oldos2er on 2013-12-14
```
dpkg -L ns2
``` will show where are the files in the package are. Synaptic can show you the same info; click Status, Installed, Installed Files tab.

If you want the source code, run ```
apt-get source ns2
```

---

### Post by ichie on 2013-12-14
> **oldos2er said:**
> ```
dpkg -L ns2
``` will show where are the files in the package are. Synaptic can show you the same info; click Status, Installed, Installed Files tab.

If you want the source code, run ```
apt-get source ns2
```


thnx for the quick response. I find the files but i cant locate specifically the aodv.h and aodv.cc files. 
When i try a simple simulation example the protocol works normally so i figure that there has to be somewhere in my files. Sorry to bother you again but i cant find them anywhere

---

### Post by steeldriver on 2013-12-14
Those files are part of the source code for ns2 itself I think (not part of the binary ns2 package)

```

$ find ns2-2.35~rc10+dfsg/ -name 'aodv.*'
ns2-2.35~rc10+dfsg/tcl/test/test-output-energy/aodv.gz
ns2-2.35~rc10+dfsg/tcl/test/test-output-wireless-lan/aodv.gz
ns2-2.35~rc10+dfsg/aodv/aodv.h
ns2-2.35~rc10+dfsg/aodv/aodv.cc

```

---

### Post by ichie on 2013-12-14
> **steeldriver said:**
> Those files are part of the source code for ns2 itself I think (not part of the binary ns2 package)

```

$ find ns2-2.35~rc10+dfsg/ -name 'aodv.*'
ns2-2.35~rc10+dfsg/tcl/test/test-output-energy/aodv.gz
ns2-2.35~rc10+dfsg/tcl/test/test-output-wireless-lan/aodv.gz
ns2-2.35~rc10+dfsg/aodv/aodv.h
ns2-2.35~rc10+dfsg/aodv/aodv.cc

```

i cant seem to get the source code i run
```
sudo apt-get source ns2
```

and i get an error ```
E: Unable to find a source package for ns2
```

also i use your commands and i get ```
[No such file or directory


```

---

### Post by oldos2er on 2013-12-14
You don't need to use 'sudo' with the 'apt-get source <package>' command. By default it will put the source in your home folder.

Do you have the source repositories enabled? ```
cat /etc/apt/sources.list
```

---

### Post by ichie on 2013-12-14
> **oldos2er said:**
> You don't need to use 'sudo' with the 'apt-get source <package>' command. By default it will put the source in your home folder.

Do you have the source repositories enabled? ```
cat /etc/apt/sources.list
```

i dont know really :) im new at this and i try to undestand how it works so after i put your command i get
```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ftp.ntua.gr/pub/linux/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.ntua.gr/pub/linux/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.ntua.gr/pub/linux/ubuntu/ precise universe
deb http://ftp.ntua.gr/pub/linux/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.ntua.gr/pub/linux/ubuntu/ precise multiverse
deb http://ftp.ntua.gr/pub/linux/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ftp.ntua.gr/pub/linux/ubuntu/ precise-backports main restricted universe multiverse


deb http://ftp.ntua.gr/pub/linux/ubuntu/ precise-security main restricted
deb http://ftp.ntua.gr/pub/linux/ubuntu/ precise-security universe
deb http://ftp.ntua.gr/pub/linux/ubuntu/ precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by ichie on 2013-12-14
nevermind i enable source code through synaptics and i downladed the source code for ns2. i found the files i wanted in the package but i have one other silly question.
If i modify these files inside the ns2_2.35~rc10+dfsg.orig.tar will it affect my simulation? i ask because i try to understand how it works..

my main goal is to modify aodv.h and aodv.cc to perform a black hole attack.

if i do this in this file will it work? sorry for the stupid questions but i m trying all day to get the ns2 to work

---

### Post by oldos2er on 2013-12-14
You'll need to re-compile it, then install the newly compiled version. We're getting a bit beyond an 'Absolute Beginners' question; see [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by ichie on 2013-12-14
What good will it be if i re-compile the packet? is it going to be the same as installing it using ```
 sudo apt-get install ns2? 
``` without the questionmark.
i'm only asking because i'm unexperienced

Nevertheless, thnx for all the help and quick responses, I really appreciate it!

---

### Post by steeldriver on 2013-12-14
You would need to do something like this

1. download any additional source dependencies (mostly development headers and libraries - in the case of ns2 these will predominantly be Tcl/Tk packages, because that's the toolkit used to build ns2)

```
sudo apt-get build-dep ns2
```

2. enter the root of the ns2 source directory that you downloaded with the 'apt-get source ns2' command e.g.

```
cd ns2-2.35~rc10+dfsg/
```

3. configure the package to be built - you may want to add an install prefix at this stage to 'sandbox' your modified version instead of overwriting the currently installed version e.g.

```
./configure --prefix=/usr/local
```

4. if the configure runs without producing any errors (which it should, if you installed all the build-deps), you can try building the source

```
make
```

At this point it should just produce a 'local' version of the ns2 binary somewhere within the downloaded source tree

Once you're happy that the new version has built OK, you can install it with

```
sudo make install
```

(the sudo is necessary if the prefix dir is somewhere that only root has permission to write). If you configured with a non-default prefix directory you may need to modify your executable search path (the $PATH environment variable) in order to make the system find your modified version ahead of the standard system version.

If you make any changes to the source code, you should just need to 'make' and 'sudo make install' again

---

### Post by ichie on 2013-12-15
> **steeldriver said:**
> You would need to do something like this

1. download any additional source dependencies (mostly development headers and libraries - in the case of ns2 these will predominantly be Tcl/Tk packages, because that's the toolkit used to build ns2)

```
sudo apt-get build-dep ns2
```

2. enter the root of the ns2 source directory that you downloaded with the 'apt-get source ns2' command e.g.

```
cd ns2-2.35~rc10+dfsg/
```

3. configure the package to be built - you may want to add an install prefix at this stage to 'sandbox' your modified version instead of overwriting the currently installed version e.g.

```
./configure --prefix=/usr/local
```

4. if the configure runs without producing any errors (which it should, if you installed all the build-deps), you can try building the source

```
make
```

At this point it should just produce a 'local' version of the ns2 binary somewhere within the downloaded source tree

Once you're happy that the new version has built OK, you can install it with

```
sudo make install
```

(the sudo is necessary if the prefix dir is somewhere that only root has permission to write). If you configured with a non-default prefix directory you may need to modify your executable search path (the $PATH environment variable) in order to make the system find your modified version ahead of the standard system version.

If you make any changes to the source code, you should just need to 'make' and 'sudo make install' again

thnx for the quick response.
i think this method is similar as installing ns-allinone- described [here]("http://nson1210.blogspot.gr/2012/12/installing-ns235-in-ubuntu-1210.html") but i had problems with the variables..i wasnt sure how to do it and *nam* wasnt working so i gave up and installed through ```
sudo apt-get install ns2
``` and all worked fine, except the fact that i could find the aodv.h and aodv.cc files. anyway thnx again for the help. i will try your method and i hope it works.

---

### Post by steeldriver on 2013-12-15
They are different things.

```
sudo apt-get install ns2
```

installs a *standard, pre-built, binary package* of ns2. If you want to create a *modified* version of ns2, you will need to install the source code and build dependencies - then you will be able to make whatever changes you want to the aodv.cc and aodv.h files and compile/install/run the modified version.

---

### Post by ichie on 2013-12-15
> **steeldriver said:**
> They are different things.

```
sudo apt-get install ns2
```

installs a *standard, pre-built, binary package* of ns2. If you want to create a *modified* version of ns2, you will need to install the source code and build dependencies - then you will be able to make whatever changes you want to the aodv.cc and aodv.h files and compile/install/run the modified version.


thnx i just tried installing ns2 with ns-allinone-2.35 packet and it seems to work fine now. i changed the environmental variables and i also have access to the files i want. thnx for all the help! i really appreciate it!!

---

