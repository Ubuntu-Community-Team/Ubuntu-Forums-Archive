---
title: "Installing packages in Octave"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by browny254 on 2008-06-15
Hi, I was wondering if someone knows how to install Octave packages, when i try i get the following

```
octave:5> pkg install signal-1.0.7.tar.gz
make: mkoctfile: Command not found
make: *** [remez.oct] Error 127
error: 'make' returned the following error: make: Entering directory `/tmp/oct-Eo2mX0/signal-1.0.7/src'
mkoctfile -s remez.cc
make: Leaving directory `/tmp/oct-Eo2mX0/signal-1.0.7/src'
error: called from `pkg:configure_make' in file /usr/share/octave/3.0.0/m/pkg/pkg.m near line 1058, column 2

```

thanks for any help.

---

### Post by argail1980 on 2008-06-15
no idea really, but have you tried unpacking it first outside octave?

```
tar xvzf signal-1.0.7.tar.gz
```

Maybe there's a README inside ;-)

---

### Post by browny254 on 2008-06-15
no, i dont think its that...this is what the faq says...

How do I install a package?

First you need to download the package, by going to the package web page and clicking download. Then start Octave and go to the directory where you placed the downloaded package using the cd command. Then type
pkg install package_file_name.tar.gz

where package_file_name.tar.gz is the file name of the package you downloaded. 



but that didnt work for me.

---

### Post by argail1980 on 2008-06-15
ok, then I have absolutely no idea, sry

---

### Post by jonlemur on 2008-07-02
I think you need the octave3.0-headers.

```
sudo apt-get install octave3.0-headers
```

They include the mkoctfile command that you're missing.

---

### Post by foxvan on 2011-02-06
Thank you, this worked for me:

1. Install the header package corresponding to your octave version. In my case it was octave3.2-headers
2. Download the package you want
3. Start octave as sudo or any other user with copy permission to /usr/share/octave.
4. Navigate to the downloaded package path and run the command: pkg install package-name

---

### Post by richard.peter3 on 2013-03-06
Hi I just had this same problem when I was trying to install the audio package in Octave - I'm a nube to both ubuntu and Octave but it seems to be working now: I'm on Ubuntu 12.10 and installed GNU Octave then QtOctave from the Software Center.

The above install didn't work for me, and after trying to install the octave3.2-header package the suggestion was that liboctave-dev replaced it.

```
sudo apt-get install liboctave-dev
```

The output suggested upgrading 2 packages (libgl1-mesa-glx libglapi-mesa) and installing another 32 (hdf5-helpers libdrm-dev libfftw3-bin libfftw3-dev libgl1-mesa-dev libgl1-mesa-glx libglapi-mesa libhdf5-dev libpthread-stubs0 libpthread-stubs0-dev libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-glx0-dev libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxxf86vm-dev mesa-common-dev x11proto-core-dev x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev) This seemed a bit toppy but as its a relatively fresh install I went with it anyway.

I have no idea what this stuff means or does but its working now - hope that helps the next person. Out of curiosity, as a newcomer, why are the headers not installed with the main Octave application?

---

### Post by sandyd on 2013-03-07
**Necromancing - thread closed**

Please do not post in threads more than one year old as many things change between Ubuntu Releases. Instead, start a new thread.

Thanks!

---

