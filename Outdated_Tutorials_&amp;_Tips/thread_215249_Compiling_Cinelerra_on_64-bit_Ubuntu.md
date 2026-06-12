---
title: "Compiling Cinelerra on 64-bit Ubuntu"
date: 2006-07-13
forum: Outdated Tutorials &amp; Tips
---

### Post by chainzz on 2006-07-13
Yesterday I received my AMD64 processor (AMD Athlon 64 3400+) and I decided to give the 64-bit edition of Ubuntu a go. One of the first things I did was trying to compile Cinelerra, I heard that it worked best on 64-bit PC's. Before this I already compiled it a few times on my old 32-bit Ubuntu installation but compiling on 64-bit gives a few problems you don't get with 32-bit. I finally completed the compilation about 5 minutes ago, but I got numerous errors and other problems so I decided to make a small tutorial on how to do it.

In this tutorial you will downloaded a lot of source-code and stuff like that so I recommend you to make an empty folder on your desktop, cd to that folder and execute all the commands there.

Before you start with the tutorial, you need to install all the packages that are needed (you need to have the extra repositories enabled for this, check out the Ubuntu wiki if you want to know how to do this, or check this thread: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)):
```
sudo apt-get install build-essential automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng3-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad2-dev fftw3-dev libraw1394-dev libavc1394-dev libtiff4-dev subversion checkinstall
```

I learned most of this from this thread: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)
Thanks to Iprofil for learning me the (Cinelerra) compiling basics :)
Cinelerra community version homepage: [http://cvs.cinelerra.org](http://cvs.cinelerra.org)
Offical Cinelerra homepage with explanation of what Cinelerra is: [http://www.heroinewarrior.com/cinelerra.php3](http://www.heroinewarrior.com/cinelerra.php3)

**1. Compiling and installing x264**

First we need to compile x264, because the x264 packages in the Ubuntu repositories are not compiled correctly to be used for compiling Cinelerra (in 32-bit Ubuntu they are compiled correctly but in 64-bit Ubuntu they are not). The first thing we need to do is get the latest x264 revision:
```
svn co svn://svn.videolan.org/x264/trunk x264
```
Then cd into the folder (cd x264) and execute the configure file. However, you need to add the flag --enable-pic, this way x264 will compile in the right way so you can use it with the compilation of Cinelerra.
```
./configure --enable-pic
```
When this is ready, we will compile x264, just type 'make' when you are inside the x264 folder:
```
make
```
After this, install it with 'make install':
```
make install
```
Now you are done with installing x264, let's move on to the important part: compiling and installing Cinelerra!

**2. Compiling and installing Cinelerra**

Get the latest revision of Cinelerra:
```
svn checkout svn://cvs.cinelerra.org/repos/cinelerra/trunk/hvirtual
```
cd into the hvirtual folder that was created when downloading to latest revision and edit the autogen.sh file with gedit:
```
gedit autogen.sh
```
Find this:
```
# export AUTOMAKE=/usr/bin/automake-1.7
# export ACLOCAL=/usr/bin/aclocal-1.7
```
and remove the hashes (#) in front of both lines, and save the file.
Now we are going to compile Cinelerra. cd to the hvirtual directory and execute the following commands:
```
./autogen.sh
./configure
make
```
You have the biggest chance on compile errors in the make process. If you follow this tutorial carefully it shouldn't go wrong but sometimes it still does. Don't panic, I solved most of the problems with Google, just enter (parts of) the error message. With a little smart thinking most of the problems can be easily solved.

When everything is compiled succesfully, the only thing left to do is installing Cinelerra. Most people do it with 'make install' but I prefer to do it with 'checkinstall' because it creates a Debian package of the program so you can easily remove the program again and you can also easily distribute it to others.
The only thing you have to do is type this when you are in the hvirtual folder:
```
checkinstall
```
It will create a Debian package and will also lead you through a simple process where you can set all the options of the Debian package, like the name, description, version, maintainer, architecture etc. Be sure to set the architecture to 'amd64' (not 'x86_64'!) otherwise it will not install.

This is the end of my tutorial, I hope you will enjoy Cinelerra, it's a great piece of software. Be sure to checkout [http://cvs.cinelerra.org](http://cvs.cinelerra.org) regulary to see if a new version has been released, then you will have to recompile again. If you have any questions feel free to ask them here or in Iprofil's thread: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)

---

### Post by chainzz on 2006-07-14
I'm sorry, I accidentally double-posted this thread, could someone delete it? This is the other thread: [http://www.ubuntuforums.org/showthread.php?t=215252](http://www.ubuntuforums.org/showthread.php?t=215252)

---

