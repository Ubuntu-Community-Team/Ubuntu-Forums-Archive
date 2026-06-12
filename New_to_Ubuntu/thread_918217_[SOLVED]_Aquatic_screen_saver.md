---
title: "[SOLVED] Aquatic screen saver"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by bj218 on 2008-09-12
Is their a good easy to install Aquatic screen saver for Ubuntu8.04?

---

### Post by phidia on 2008-09-12
There is [this]("http://linux.softpedia.com/get/Desktop-Environment/Screensavers/Shermans-aquarium-1003.shtml") which is sort of comical.
If you're looking for a photorealistic one I'm not sure where to go for that.

---

### Post by t0p on 2008-09-12
> **phidia said:**
> There is [this]("http://linux.softpedia.com/get/Desktop-Environment/Screensavers/Shermans-aquarium-1003.shtml") which is sort of comical.


Hi phidia, I installed that fishy aquarium, but I can't find it to start it up.

Well, I *think* I installed it.  I issued the commands, and ubunty didn't say it failed... but the installation wasn't as wordy as I expected.

Here's the output from my installation:

```
t0p@ubunty:~/Desktop/shermans_aquarium-3.0.1$ ./configure
checking whether to try to include Screensaver support... yes
checking whether to try to compile applet support ... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking operating system... Linux
checking for pkg-config... true
checking for gai... no
checking for sdl-config... false
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: creating shermans/Makefile

 Sherman's aquarium v3.0.1
===========================
 - Compile Sherman's aquarium - dockapp/wmapplet:       no
 - Compile Sherman's aquarium - Gnome 2 Panel applet:   no
 - Compile Sherman's aquarium - Screensaver:            no
t0p@ubunty:~/Desktop/shermans_aquarium-3.0.1$ make
(cd shermans;make all)
make[1]: Entering directory `/home/t0p/Desktop/shermans_aquarium-3.0.1/shermans'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/t0p/Desktop/shermans_aquarium-3.0.1/shermans'
t0p@ubunty:~/Desktop/shermans_aquarium-3.0.1$ sudo make install
[sudo] password for t0p: 
(cd shermans;make install)
make[1]: Entering directory `/home/t0p/Desktop/shermans_aquarium-3.0.1/shermans'
mkdir -p /usr/local//share/pixmaps/shermans
cp -r ../aquarium/* /usr/local//share/pixmaps/shermans/
make[1]: Leaving directory `/home/t0p/Desktop/shermans_aquarium-3.0.1/shermans'
t0p@ubunty:~/Desktop/shermans_aquarium-3.0.1$ 

```

Did it install?  And if so, how do I make them fishes swim?

---

