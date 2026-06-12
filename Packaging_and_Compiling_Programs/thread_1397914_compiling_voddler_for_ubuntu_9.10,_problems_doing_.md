---
title: "compiling voddler for ubuntu 9.10, problems doing make"
date: 2010-02-03
forum: Packaging and Compiling Programs
---

### Post by DanielSamani on 2010-02-03
I am very new to compiling programs in linux, but now I have decided to give it a try. I started to install viddler .. and it seam to build upon xbmc. I am now going to write what I have done step by step including the errors that I received. 

First I downloaded the source and moved it to the desktop. When I had done this I did the following commands in the terminal.

```

sudo apt-get install subversion
   cd $HOME
   svn checkout https://xbmc.svn.sourceforge.net/svnroot/xbmc/branches/linuxport/XBMC
sudo aptitude install subversion make g++ gcc gawk pmount libtool nasm automake cmake gperf unzip bison libsdl-dev libsdl-image1.2-dev libsdl-gfx1.2-dev libsdl-mixer1.2-dev libsdl-sound1.2-dev libfribidi-dev liblzo2-dev libfreetype6-dev libsqlite3-dev libogg-dev libasound-dev python-sqlite libglew-dev libcurl4-dev x11proto-xinerama-dev libxinerama-dev libxrandr-dev libxrender-dev libmad0-dev libogg-dev libvorbis-dev libsmbclient-dev libmysqlclient-dev libpcre3-dev libdbus-1-dev libhal-dev libhal-storage-dev libjasper-dev libfontconfig-dev libbz2-dev libboost-dev libfaac-dev libenca-dev libxt-dev libxtst-dev libxmu-dev libpng-dev libjpeg-dev libpulse-dev mesa-utils libcdio-dev libsamplerate-dev libmms-dev
sudo apt-get update
sudo apt-get build-dep xbmc
cd /daniel/Desktop/source/
./configure --prefix=/usr
make

```Now when I did the make command I got the following error.

```
make[1]: *** No rule to make target `aes.o', needed by `utils.a'.  Stop.
make[1]: Leaving directory `/home/daniel/Desktop/source/xbmc/utils'
make: *** [xbmc/utils/utils.a] Error 2
```and if I try to do make install I not so surprisingly get the following error.

```
install: cannot stat `xbmc.bin': No such file or directory
make: *** [install] Error 1
```Now I have no idea why it didn't work doing the make thing. I got one core cpu btw. So I don't think I should do make -j2 and something similar. Any suggiestions, have I left out any information needed to get a picture of what's wrong?

---

### Post by SevenMachines on 2010-02-05
hi there. is it essential that you build xbmc from source? (you seem to say you downloaded the xbmc source AND used subversion to get the development source)
if not, xbmc has its own pre built ubuntu binaries, see [xbmc's ppa guide]("http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step")

---

### Post by WakkiTabakki on 2010-05-10
Hi
From what I understand, you're building XBMC from source because you'd like to get Voddler working, right?
The problem with Voddler and linux isn't really the client as such (the crash-happy Voddler client builds indeed on XBMC). The problem with Voddler is the proprietary protocol which connects the client with the streaming source. Under windows its written in .Net and apparently Mono (in its current state) isn't compatible.

So in short, it doesn't really matter whether you can compile XBMC or not, you'd still be unable to connect to the Voddler service... which sucks... and a LOT of people in the Voddler-forum agrees.

Tip: after being really frustrated with Voddler, I found  [Headweb]("http://www.headweb.com/:hairlessrat") which is an online video service ACTUALLY doing pretty much what Voddler promises. Headweb is browser and Flash-based and works really well under Linux!

Just my €2 cents...
/N

---

