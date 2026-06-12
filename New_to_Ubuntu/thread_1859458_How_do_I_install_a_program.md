---
title: "How do I install a program?"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by pathos_society on 2011-10-13
Major league noob question.

I'm trying to get an SNES emulator for my Ubuntu 11.4 machine.  First, I tried installing ZSNES.

pathos@MELFINA:~$ /home/pathos/Emulators/SNES/src/configure --enable-release
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... no
configure: error: You need NASM installed to compile ZSNES

I looked around, and it's possible that ZSNES isn't compatible with 64-bit Linux. (Maybe I'm wrong; if I am, correct me.  I'd rather run ZSNES if possible)

So then I tried installing SNES9X.

pathos@MELFINA:~$ sudo /home/pathos/Emulators/SNES/snes9x-gtk
/home/pathos/Emulators/SNES/snes9x-gtk: error while loading shared libraries: libpng14.so.14: cannot open shared object file: No such file or directory

Apparently, I need libpng 1.4.  I have no idea where to find this or how to get it.

I think I may be doing some stupid noob thing wrong when attempting to install things.  Please help as much as you can.

---

### Post by Brushstroke on 2011-10-13
Looks like it's calling for you to install NASM, which is a x86 (32-bit) assembler. Run: 

```
sudo apt-get install nasm
``` and try to install ZSNES again.

---

### Post by d4m1r on 2011-10-13
Try searching for it in the "Software Center", chances are it will come up.

If it doesn't it's a little more complicated:

[http://www.basicconfig.com/linux/ubuntu_package_management_system](http://www.basicconfig.com/linux/ubuntu_package_management_system)

Trying running > sudo apt-get install libpng in console.

---

### Post by pathos_society on 2011-10-13
pathos@MELFINA:~$ sudo apt-get install NASM
[sudo] password for pathos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package NASM

Hmm... That didn't work.  Anything else I can try?

---

### Post by madjr on 2011-10-13
if you dont know how to install applications in ubuntu check here (video number 2):

[http://www.omgubuntu.co.uk/2011/10/10-things-to-do-after-installing-ubuntu-11-10](http://www.omgubuntu.co.uk/2011/10/10-things-to-do-after-installing-ubuntu-11-10)

---

### Post by pathos_society on 2011-10-13
Oh lord, case sensitivity.  I tried "install nasm" instead of "install NASM" and it worked.  Now I'm getting a new error.

pathos@MELFINA:~$ sudo apt-get install nasm
[sudo] password for pathos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nasm
0 upgraded, 1 newly installed, 0 to remove and 48 not upgraded.
Need to get 1,025 kB of archives.
After this operation, 3,162 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main nasm amd64 2.09.04-1 [1,025 kB]
Fetched 1,025 kB in 36s (27.9 kB/s)                                            
Selecting previously deselected package nasm.
(Reading database ... 154242 files and directories currently installed.)
Unpacking nasm (from .../nasm_2.09.04-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
Setting up nasm (2.09.04-1) ...
pathos@MELFINA:~$ /home/pathos/Emulators/SNES/src/configure --enable-releasechecking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: SDL >= 1.2.0 is required

Not sure what SDL or SDL_CONFIG are.

---

### Post by alphacrucis2 on 2011-10-13
Maybe this:

[http://www.libsdl.org/index.php](http://www.libsdl.org/index.php)

libsdl is in the repos.

---

### Post by pathos_society on 2011-10-13
> **alphacrucis2 said:**
> Maybe this:

[http://www.libsdl.org/index.php](http://www.libsdl.org/index.php)

libsdl is in the repos.

Ok, I downloaded [SDL-1.2.14-1.x86_64.rpm]("http://www.libsdl.org/release/SDL-1.2.14-1.x86_64.rpm").

...What do I do with it?

I tried extracting it to /usr/, but everything within the / directory gives me "permission denied."  Or am I doing this wrong altogether?

---

### Post by alphacrucis2 on 2011-10-13
> **pathos_society said:**
> Ok, I downloaded [SDL-1.2.14-1.x86_64.rpm]("http://www.libsdl.org/release/SDL-1.2.14-1.x86_64.rpm").

...What do I do with it?

I tried extracting it to /usr/, but everything within the / directory gives me "permission denied."  Or am I doing this wrong altogether?

rpm (=Redhat Package Management) is for distros like fedora and redhat. Ubuntu uses deb packages.. It is possible to convert rpm's to deb's but not recommended. Just install from the repo. Try

```
sudo apt-get install libsdl1.2debian
```

---

### Post by pathos_society on 2011-10-14
pathos@MELFINA:~$ sudo apt-get install libsdl1.2debian
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl1.2debian is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 48 not upgraded.

---

### Post by pathos_society on 2011-10-14
Alrighty, tried apt-getting libsdl1.2-dev, and that worked.

Now I get:

ZSNES v1.51

SDL support                   Version 1.2.14
NASM support                  NASM version 2.09.04 compiled on Nov 26 2010
zlib support                  Version 1.2.3.4
PNG support                   Yes, version 1.2.44
OpenGL support                Yes
JMA support                   Yes
ZSNES debugger                Enabled

The binary will be installed in /usr/local/bin

Configure complete, now type 'make' and pray.

pathos@MELFINA:~$ make
make: *** No rule to make target `tools/depbuild.cpp', needed by `tools/depbuild'.  Stop.

What should I do now?

---

### Post by alphacrucis2 on 2011-10-14
Maybe you need the sdl dev lib. Try this.

```
sudo apt-get install libsdl1.2-dev
```

Edit. OK I see you worked that out yourself.

---

### Post by alphacrucis2 on 2011-10-14
> **pathos_society said:**
> Alrighty, tried apt-getting libsdl1.2-dev, and that worked.

Now I get:

ZSNES v1.51

SDL support                   Version 1.2.14
NASM support                  NASM version 2.09.04 compiled on Nov 26 2010
zlib support                  Version 1.2.3.4
PNG support                   Yes, version 1.2.44
OpenGL support                Yes
JMA support                   Yes
ZSNES debugger                Enabled

The binary will be installed in /usr/local/bin

Configure complete, now type 'make' and pray.

pathos@MELFINA:~$ make
make: *** No rule to make target `tools/depbuild.cpp', needed by `tools/depbuild'.  Stop.

What should I do now?

Can you ask the ZSNES devs if they have a forum perhaps? 


Edit. I looked myself and they do have a support forum. Might be best to register and ask for further help there.

---

### Post by pathos_society on 2011-10-14
Yeah, this is starting to get a bit program-specific.  Am I going to have to do stuff like this every time I install something?

---

### Post by Brushstroke on 2011-10-14
> **pathos_society said:**
> Yeah, this is starting to get a bit program-specific.  Am I going to have to do stuff like this every time I install something?
Not for every program you install. Most programs can be found in the repositories through the Ubuntu Software Center or Synaptic, but for something like this you need to install from source as you've tried to do. The only reason you have to install this from source is because there is not a 64-bit version of ZSNES available in the repositories. It's only available in the 32-bit repositories.

---

### Post by pathos_society on 2011-10-14
Huh.  Yeah, I just looked and ZSNES is listed under the Ubuntu Software Center, but it says "There isn't a software package called zsnes in your current software sources."

SNES9X is there, though.  Installing it and seeing if it works.

---

### Post by madjr on 2011-10-14
> **pathos_society said:**
> Huh.  Yeah, I just looked and ZSNES is listed under the Ubuntu Software Center, but it says "There isn't a software package called zsnes in your current software sources."

SNES9X is there, though.  Installing it and seeing if it works.

you can also find more apps from getdeb:

[http://www.getdeb.net/](http://www.getdeb.net/)

just read carefully the install instructions and choose your version

---

