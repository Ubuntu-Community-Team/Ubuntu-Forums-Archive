---
title: "What do I need to create C cross-platform development ?"
date: 2008-03-25
forum: Packaging and Compiling Programs
---

### Post by Browser_ice on 2008-03-25
I have downloaded the IOQuake3 source code because I want to have a go at it to create a total conversion. I do not need any of the Quake-3 data. I will be making my own.

Now my problem is that the site and files are not newbish friendly. Its been ages since I programed in C and I have never done it into Linux.  The IOQ3 source code is setup for a Linux environment. I was told it would be easier to develop on it in Linux then Windows. I want to do cross-platform development for what I want to do.

What I need is an exact list of what I need to do to be able to create a successful compile for Linx and WIndows :

- I have Ubuntu 7.10 so there is already a C compiler on it.
- I need a C editor with cross-reference of symbols (eclipse, code::blocks, ...)
- I need to know what additional libraries I have to install before doing a compile (I was told some libc-dev but either I got the name wrong or it doesn't exist, also been told bison but don't know why)
- I know what a makefile is but I have no clue as to its command syntax
- I will need to know how to make packages Ubuntu and non-ubuntu based (I could probably find it on my own)
- the link for a IOQuake3 Debian package is broken so I had to resort using an Openarena package for at least testing my game data until I am able to fully compile my IOQ3

Before you go on and tell me to check with the IOQ3 guys, I did. The site doesn't have enough infos on what I need. I already started chatting with folks on #ioquake3 but answers are very slow to get by. The IOQ3 forum, well, I subscribed last week and I still didn't get my logon-id confirmation.

---

### Post by Browser_ice on 2008-03-25
I have been told through @ioquake3 to install the followings :

libc6-dev
bison for creating qvms files
libsdl-dev for client apps => found libsdl1.2-dev instead
libcurl-dev  for client apps => didn't find it at all
libopenal-dev


because I couldn't find the the libcurl-dev I was told by someone else to "sudo apt-get build-dep tremulous" to at least be able to compile my ioquake3 but it would probably not give me my libcurl library.

I still don't know if I am heading in the right direction or this will get me into more problems...

---

### Post by WW on 2008-03-25
When I know something about the library that I want installed, but I don't know the exact package name, I find it useful to use the search feature at [http://packages.ubuntu.com/](http://packages.ubuntu.com/).  For example, searching for "libcurl" results in [this](http://packages.ubuntu.com/search?keywords=libcurl&searchon=names&suite=gutsy&section=all).  Scrolling through the packages, I see several candidates for the development package for libcurl. In particular, you probably want either libcurl4-gnutls-dev or libcurl4-openssl-dev.

You can also use Synaptic to search for likely matches.  I've seen people give examples of an apt-* command to search, but I can never remember which one.

---

### Post by jaddle on 2008-03-25
By cross-platform development, I assume you mean that you want to compile windows binaries from inside linux.

I've just gotten into this too - it's a bit of a hassle, but it generally works very well!

You need to install mingw32 to start with. The really annoying bit is that you have to get the source for any libraries you want to use and recompile windows versions of them (apt-get source libjpeg for example). Usually this is just a matter of './configure && make && make install' just like installing any other source package, except that you'll need some options for the configure script.

I use something like this:
./configure --host=i586-mingw32msvc --prefix $HOME/src/w32libs/

Then the libraries get put into my home dir under src/w32libs when the make install step is run. Without the prefix line, they'd probably get installed to /usr/local somewhere, but then you'd need root access and it just gets a little messier. I prefer to keep it all under my home dir. 

To use those libraries, you'll have to add the switches -I$HOME/src/w32libs/include and -L$HOME/src/w32libs/lib to any compile that you do.

---

### Post by Browser_ice on 2008-03-25
ok, so I installed the tremulous library packages (at first it was asking for my Ubuntu CD but I removed it from the repo list).

Then when I started the build (make), it ended ok. I have qvm files, 2 i386 files and some tools (were built to build qvm files). 

I have been told I do not need the pak0.pk3 file if I want to mod (then I need to use those built qvm files ???).

Upon trying to execute my first base build, it doesn't recognize that I have a pak0.pk3 file in my baseq3 folder. Seams also, ubuntu doesn't know how to handle any pk3 files other then the ones from OpenArena. Don't know why.


>>> Jaddle, sounds complicated to develop under Windows when its a Linux package.

>> to all : by cross platform, I mean to platforms like Windows, Linux, Mac, Solaris, ....

---

### Post by Browser_ice on 2008-03-25
I was told I needed to install the quake-3 data to be able to run it. It needs the quake3 patch to be able to run and not the plain pak0.pk3 file.

**sudo apt-get install quake3-data**
==> will ask you to put your quake-3 cd in to validate

After that, when I executed my built ioquake3.i386 it finaly started a quake-3 game !!!

Now I can start my project.

I just wish all this was indicated somewhere to same me 6 hours of pain !!!

---

### Post by Browser_ice on 2008-03-25
Oh I forgot, I still need a C editor with symbols cross-ref.

Know of any good one ?

---

### Post by sentenced on 2008-03-26
Have you tried XVT? I know they support C (and C++) and I think they support Ubuntu (if they don't, request it--if they get enough requests, they will support it). I know they support several Linux environments now (and unix, Windows and Mac). You can go to [www.xvt.com](www.xvt.com) to check.

---

