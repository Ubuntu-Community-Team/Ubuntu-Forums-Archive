---
title: "How to make Alsa .deb files"
date: 2010-05-09
forum: Packaging and Compiling Programs
---

### Post by ravisunny2 on 2010-05-09
[FONT=Times New Roman][SIZE=3]I have two PCs. One is my work PC, the other for the kids.[/SIZE][/FONT]
 

[FONT=Times New Roman][SIZE=3]I want to create the **.deb** files on **my PC**, burn to cd, copy the **.deb** to the PIII, and install the .**deb **files using[/SIZE][/FONT]
 

[SIZE=3]**[FONT=Times New Roman]sudo dpkg [/FONT]****[FONT=Consolas]&#8208;[/FONT]****[FONT=Times New Roman]i package.deb[/FONT]**[/SIZE]
 

[FONT=Times New Roman][SIZE=3]I have also done some googling on how to make a **.deb** file. It seems that instead of **make install, **I should use **checkinstall**.[/SIZE][/FONT]
 

[FONT=Times New Roman][SIZE=3]Is this feasible ? How should how I modify the **Alsa** instructions ?[/SIZE][/FONT]
 

[COLOR=black][FONT=Times New Roman][SIZE=3]I got this from the **Alsa **site:[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]Make a directory to store the alsa source code in: [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cd /usr/src[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]mkdir alsa[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cd alsa[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cp /downloads/alsa-* .[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]Now unzip and install the alsa-driver package:[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]bunzip2 alsa-driver-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]tar -xf alsa-driver-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cd alsa-driver-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]./configure --with-cards=ymfpci --with-sequencer=yes ; make ; make install[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]Now unzip and install the alsa-lib package: [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]cd ..[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]bunzip2 alsa-lib-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]tar -xf alsa-lib-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cd alsa-lib-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]./configure ; make ; make install[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]Now unzip and install the alsa-utils package: [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]cd ..[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]bunzip2 alsa-utils-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]tar -xf alsa-utils-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]cd alsa-utils-xxx[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]./configure ; make ; make install[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]Now insert the modules into the kernel: [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Times New Roman][SIZE=3]modprobe snd-ymfpci ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss[/SIZE][/FONT][/COLOR]

---

### Post by ravisunny2 on 2010-05-14
Bump.

---

### Post by SevenMachines on 2010-05-14
hi there. checkinstall sounds like what you want. to use it you should just replace any 'make install' call in the above instructions with 'checkinstall' (although you may actually need to use 'sudo checkinstall' instead. this will give you simplified debian packages that can be installed as you mention. these packages will not do a lot of things that proper packages will do but are generally useful for managing local installations from source of the kind you are doing.
Note though that checkinstall just creates installable packages equivalent to 'make install' (with some common sense applied) and wont deal with things like maintainer scripts and other finer points that a proper package would have, although you can add some packaging information using --requires and/or --provides if you want so with although this is not necessary.

> **Checkinstall** - This handy program  acts as a kind of wrapper around the source codes build system and  creates a simple package that the packaging system can use to install  and uninstall compiled source
 
For example, a typical  gnu-type compilation process might look something like this 
-configure build for this system
 $./configure 
- compile the program
 $make 
- install the program
 $make install 
Checkinstall replaces the last step, it pretends to run  'make install' inside of a fake installation environment, sees what  files go where, and then creates a package that does the same thing. Essentially this means that the  package management system can handle installing and removing your  compiled program instead of 'make install' / 'make uninstall' 

---

### Post by ravisunny2 on 2010-05-14
Thank you, **SevenMachines.**
 
Basically, I needed to confirm that the **.deb** would be portable, and that the process of making the **.deb**, via **checkinstall**, wouldn't mess up the configuration on my PC.

---

### Post by SevenMachines on 2010-05-14
Best way to think of checkinstall is of a wrapper debian package around 'make install' rather than a proper debian package. It allows the packaging system to take care of installing and removing, in that sense it helps to protect your system by wrapping the installation with the packaging systems protections too, certainly more protection than a straight 'make install'
As for portability, its really only portable in the sense that the .deb package created can usually be easily transferred between 'similar' systems to the one its compiled on. In practice its usually fine for a bunch of similar debian or ubuntu systems but again the fact its being handled by the package manager should protect any system from anything bad happening.
Just to add, I'm no expert on checkinstall and I'm sure others would be able to give better explanations especially on the details and more advanced usage but i think the above is broadly accurate :)

---

### Post by Zoot7 on 2010-05-14
The better way to go about building debs from source is to actually "debianize" it and then build a deb that way, that way you let apt manage the dependencies which is always the best option. Checkinstall is very similar to the make install routine, it doesn't track any dependencies in general.

The best way to do it is to rename your archive to <package name>_<version>.orig.tar.gz eg. alsa-driver_1.0.23.orig.tar.gz, extract and from the source directory run **dh_make**. This will "debianize" the source code for you - it'll create a Debian subdirectory within the source one with a basic set of files needed to build the deb. The only files you need worry about within that are the **debian/control** file (which sets all the dependencies etc.) and the **debian/rules** file which sets the compile options ie. configure options and build flags etc. Then you can then build a deb with the command **dpkg-buildpackage** from the source directory.

Having said that, I suspect alsa to be a bit more involved to actively package yourself given that it's not a simple application rather a whole library, so I'm not sure how you'd go about tweaking the control and rules file to satisfy what you want, so checkinstall might be the easier option.

Regardless, this is a good read when it comes to building debs is this:
[http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html)

---

### Post by ravisunny2 on 2010-05-15
[SIZE=2]Thanks, **SevenMachines** and **Zoot7**.[/SIZE]
 
[SIZE=2]I'll try both methods.[/SIZE]
 
[SIZE=2]Basically, the **PIII** is a standalone (and I plan to keep it that way).[/SIZE]
 
[SIZE=2]I realize keeping it updated is going to be a difficult and cumbersome task.[/SIZE]
 
[SIZE=2]Also it isn't going to be easy to install all the tools I need, on the **PIII**, because it is not connected to the internet.[/SIZE]
 
[SIZE=2]So I have to build any **debs,** that I need for the **PIII**, on my **C2D**, and install them on the **PIII**.[/SIZE]
 
[SIZE=2]Of course, both machines have Karmic Koala.[/SIZE]
 
[SIZE=2]To begin with, there is no sound in the **PIII** (having a Yamaha YMF740 soundcard), so I'm trying to get the sound started using **Alsa**.[/SIZE]
 
[SIZE=2]And as the **PIII** doesn't have all the tools required, I have to build the **.deb** file on the **C2D**.[/SIZE]
 
[SIZE=2]I have no experience in this.[/SIZE]
 
[SIZE=2]I have written software in Fortran, Clipper, 'c' etc and I understand the process of compiling and linking. In all these cases, the run time components are built into the **exe** file.[/SIZE]
 
[SIZE=2]But I don't have any idea about the "**completeness**" of the **.deb** file.[/SIZE]

---

### Post by SevenMachines on 2010-05-15
I would just add that if your just looking to update a package thats already in the repository it can be extremely easy, at least in the straightforward case :), eg for alsa-utils

$ apt-get source alsa-utils      # get the repository source package
$ cd alsa-utils-1.0.22/     # or whatever the current version is
$ uscan     # download and unpack new version if found
$ cd ../alsa-utils-1.0.23/     # or whatever the new version is
$ debuild  -b -us -uc   # build binary deb of the new version

Obviously if patches and such dont carry into the new version you'd need to deal with that but if not then its probably the easiest way to get a 'proper' debian package of the new version

---

### Post by Zoot7 on 2010-05-15
Firstly, what Sevenmachines has said is a far easier way to go about things. The source is already "debianized" for you in the case of the repos, so you dont' have to go fiddling with the debian/rules file. I'd also recommend you try out packaging some more basic apps before you try packaging something the likes alsa.

However, if you want to build your own debs from the Alsa source provided on the Alsa website here's how to go about it. I'd recommend that you probably remove whatever version of alsa is installed before you replace it with your own self-built packages.

```
mkdir ~/alsa_build
cd !$
sudo apt-get install build-essential devscripts dh-make linux-headers-$(uname -r) fakeroot
```

There might be more build dependencies for Alsa on Ubuntu, I'm not sure.

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2
wget ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.17.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.23.tar.bz2
wget ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.23.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2

tar xvf *.bz2
```

Now run this from the source directory of each newly created directory.

```
dh_make -s --createorig
```

Now edit the debian/rules file in each directory with either nano, gedit or whatever editor. Here is what worked for me just a few hours ago (I gave it a shot for interest inspired by boredom an hour or two ago)

The rules file for Alsa-Driver:
```
#!/usr/bin/make -f
# -*- makefile -*-

override_dh_auto_configure:
dh_auto_configure -- 	--with-kernel=/usr/src/linux-headers-$(uname -r) \
			--with-cards=all \
			--with-card-options=all \
			--with-sequencer=yes \
			--with-oss=yes \
			--prefix=/usr

%:
	dh  $@
```

The rules file for everything else:
```
#!/usr/bin/make -f
# -*- makefile -*-

override_dh_auto_configure:
	dh_auto_configure -- --prefix=/usr

%:
	dh  $@
```

Save each one to look like the above and close them. Then build the debs from the source directory for each with the use this from the source directory. 
```
fakeroot dpkg-buildpackage -b -j4
```

You'll find newly created debs in the parent directory after that, which you can install with **dpkg** afterwards.  Namely:
```
alsa-driver_1.0.23-1_i386.deb
alsa-firmware_1.0.23-1_i386.deb
alsa-lib_1.0.23-1_i386.deb
alsa-oss_1.0.17-1_i386.deb
alsa-plugins_1.0.23-1_i386.deb
alsa-utils_1.0.23-1_i386.deb
```

NOTE - I haven't tried installing these myself to see how they'd work so I'm unsure of what the outcome would be, and once again I recommend you opt for "debianized" source code first. Nonetheless if you want to build your own debs, the above way is probably the best way to go about it.

---

### Post by ravisunny2 on 2010-05-21
[SIZE=2]Thanks, **Zoot7.**[/SIZE]
**[SIZE=2][/SIZE]** 
[SIZE=2]I am studying the **Packaging Guide** first.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I've decided to go slow but steady.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I have started to get the hang of it. :)[/SIZE]

---

### Post by X3lectric on 2010-07-14
Hi

I have followed this and resulting debs fail to install, ideally would be interested in packaging this straight to ppa, though I have tried many times I have failed all those times, though I have leaned somethings it is definitely not enough.

If anyone has the time to help me package this for ppa I would be very grateful.

Regards

---

