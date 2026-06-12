---
title: "aoTuV beta 4 tunnings for Vorbis"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by pjssilva on 2005-10-15
Hello,

I have succeeded to compile a specially tuned version of libvorbis
made by Aoyumi and highly praised in hydrogenaudio forum as one
of the best tunings around:

[http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/)
[http://www.hydrogenaudio.org/forums/index.php?showtopic=15049](http://www.hydrogenaudio.org/forums/index.php?showtopic=15049)
[http://www.hydrogenaudio.org/forums/index.php?showtopic=36465](http://www.hydrogenaudio.org/forums/index.php?showtopic=36465)
[http://www.hydrogenaudio.org/forums/index.php?showtopic=35438](http://www.hydrogenaudio.org/forums/index.php?showtopic=35438)


The old beta 2 version of those tunings was incorporated in Xiph's
official source in vorbis 1.1. Beta 4.51 is the latest version.

I have then decided to upload the modified source version, ready for
compilation in a Ubuntu machine, to my web site. Anyone ca downloaded
it here:

[http://www.ime.usp.br/~pjssilva/libvorbis_1.1.0-local-aotuv-b4.51.tar.gz](http://www.ime.usp.br/~pjssilva/libvorbis_1.1.0-local-aotuv-b4.51.tar.gz)

To compile it and install it on your machine, all you need to do is:

1) Download the source:

wget [http://www.ime.usp.br/~pjssilva/libvorbis_1.1.0-local-aotuv-b4.51.tar.gz](http://www.ime.usp.br/~pjssilva/libvorbis_1.1.0-local-aotuv-b4.51.tar.gz)

2) Untar the source in a temporary directory and move to the 
"aotuv-b4.51_20051117" directory just created.

3) Type 

dpkg-buildpackage -rfakeroot -b

on the shell prompt. You'll need to have the package dpkg-dev
installed and probably some more (the compilation will fail if you
don't have all the dependencies installed. For example, I remember I
had to install g++3-4 and libogg-dev). Just install the suggested
packages using apt-get or synaptic.

Wait the compilation finish.

4) Move to the previous directory: "cd .."

5) Type 

sudo dpkg -i libvorbisenc2_1.1.0-local-aotuv-b4.51_i386.deb libvorbis0a_1.1.0-local-aotuv-b4.51_i386.deb

to install the new version of libvorbis.

6) Have fun!

If anyone wants to know the steps I used to create this source, 
they are described below. Note that I don't know much about creating
deb's. That's the reason I used the "debian" directory from the
original Ubuntu sources, an ugly, and lazy, hack. But It worked! 
This steps maybe useful for compiling newer versions.

Enjoy good music.

Paulo

Obs: If anyone finds a major mistake in the steps below, please let
me know. 

--- Steps to compile and generate an aoTuV beta 4 source for  ---
--- Ubuntu (probably equivalent steps can be used for Debian) ---

1) Download vorbis merged source with aoTuV Beta 4 tunning from
Aoyumi page:

[http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/)

The source is in 

[http://www.geocities.jp/aoyoume/aotuv/libvorbis-aotuv_b4.tar.gz.tgz](http://www.geocities.jp/aoyoume/aotuv/libvorbis-aotuv_b4.tar.gz.tgz)

2) Unpack the source in a temporary directory.

3) Download Ubuntu's source for libvorbis using

apt-get source libvorbis

4) Remove debian directory in aoTuV source

5) Copy debian directory from Ubuntu's vorbis source onto aoTuV
source.

6) Edit the changelog file to create a new version of the library
with number 1.1.0-local1 (so that it won't be overwritten by Ubuntu's
updates).

7) Use chmod +x to make "configure" executable in aoTuV base
directory.

8) Compile the package with "dpkg-buildpackage -rfakeroot"

Obs: In this step you may be prompted to install some packages needed
to build the source (like libogg-dev and g++-3.4).

9) Install libvorbis0a and libvorbisenc2 deb's created after
compilation in your own system.

Obs: I have Checked a song against the following pre-compiled version of
oggenc with aotuv beta 4 tunnings:

[http://www.rarewares.org/quantumknot/oggenc-aotuvb4.gz](http://www.rarewares.org/quantumknot/oggenc-aotuvb4.gz)

and the new oggenc in my system.

10) I have then uploaded the source to my website.

---

### Post by bionnaki on 2005-10-22
cool thanks

whats a good commandline for this encoder?

---

### Post by pjssilva on 2005-11-13
Just use the same line options as the usual oggenc binary. Actually, you are only changing the library that is used by oggenc or by soundjuicer (gstreamer) to encode. The enconder binary doesn't change.

I usually rip my music using -q5 for listening at the computer and -q1 for my portable player (512Mb flash based, size is important).

---

### Post by eduardgrebe on 2005-12-23
Thanks for this excellent source package and howto. One note: the -rfakeroot switch on the dpkg-buildpackage command line didn't work on my machine, but everything worked fine with -rsudo.

I have placed the debs compiled for breezy powerpc on my website for the sake of convenience. You can download and install them with the command as given above, i.e. 
```
sudo dpkg -i libvorbisenc2_1.1.0-local-aotuv-b4.51_powerpc.deb libvorbis0a_1.1.0-local-aotuv-b4.51_powerpc.deb
```

They can be found here:
[http://maanskyn.za.net/ubuntu/](http://maanskyn.za.net/ubuntu/)

I will get a friend to compile them on i386 and AMD64 and create a proper repository.

---

### Post by DigitalAxis on 2006-10-28
Nice!  Thanks to this guide I now have working versions of AoTuV beta 5 running on my system!

Well, I haven't tested them beyond playback yet.

---

