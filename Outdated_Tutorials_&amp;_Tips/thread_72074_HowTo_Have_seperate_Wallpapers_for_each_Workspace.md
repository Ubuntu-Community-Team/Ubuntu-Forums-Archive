---
title: "HowTo: Have seperate Wallpapers for each Workspace"
date: 2005-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by trinaryouroboros on 2005-10-05
Hey all,

This is an easy one, took me a short bit to find a decent way to do this. Basically after doing this you should be able to have a unique wallpaper for every Workspace you have in Gnome. This is what KDE does already, but Gnome never implemented.

You'll firstly need to have the proper libraries. 

The first one should be available in your Synaptic Package Manager. Install: libglademm-2.4-1

Also, while you're in the Package Manager, if you haven't done so already, you should install the g++ packages. I decided to install:

g++
g++-3.3
g++-3.4
g++-4.0

Although I'm sure installing all are not neccessary.

The second library, has to be installed from a terminal: libxml++-2.10

I haven't been able to use sudo apt-get install to do this, but was able to install this library by doing the following:

First go here to get the package: 
[http://ftp.acc.umu.se/pub/GNOME/sources/libxml++/2.10]("http://ftp.acc.umu.se/pub/GNOME/sources/libxml++/2.10")

Then do the following in a terminal:

Unpack it:
$ tar -jxvf libxml++-2.10.tar.bz2

Or:
$ tar -zxvf libxml++-2.10.tar.gz

Go inside the directory:
$ cd libxml++-2.10

Configure it:
$ ./configure --prefix=/usr

Compile it:
$ make

Get the root permission:
$ su

Install it:
# make install

(note: if you want to uninstall this lib ever: # make uninstall)

The next step is to download and install Wallpapoz:

Download: [http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2]("http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2")

Installation:
$ tar -jxvf wallpapoz-0.2.tar.bz2
$ cd wallpapoz-0.2
$ make
$ su
# sh install.sh /usr

( for future reference to uninstall: # sh uninstall.sh /usr )

That's about it! What I did at this point was right-clicked my panel, and added "wallpapoz" up there to make the management easier. The program also has the ability to randomly shift the wallpapers after a certain time period. It has a daemon to do this, so I would check out the program website if you're having trouble getting it to start up at boottime (I didn't, but you never know). Also check the site for more information or help.

Big thanks really go out to the Wallpapoz designer. 

Check out the page here: [http://wallpapoz.sourceforge.net/]("http://wallpapoz.sourceforge.net/")

---

### Post by manicka on 2005-10-05
I have made a deb of  libxml++-2.10 that is available here if you don't feel like compiling  the source code
[http://members.iinet.net.au/%7Egracey88/libxml++-2.10.0-1_i386.deb](http://members.iinet.net.au/%7Egracey88/libxml++-2.10.0-1_i386.deb)

> (note: if you want to uninstall this lib ever: # make uninstall)
This should be 'sudo make clean' from the directory you compiled it in.

:D

---

### Post by MetalMusicAddict on 2005-10-05
Cool. Ill try this when I get home.

---

### Post by trinaryouroboros on 2005-10-05
[QUOTE=manicka]I have made a deb of  libxml++-2.10 that is available here if you don't feel like compiling  the source code
[http://members.iinet.net.au/%7Egracey88/libxml++-2.10.0-1_i386.deb](http://members.iinet.net.au/%7Egracey88/libxml++-2.10.0-1_i386.deb)


This should be 'sudo make clean' from the directory you compiled it in.

:D[/QUOTE]

Ah, forgive my cut n paste frenzy. I haven't even really tried to uninstall it, cool deb package by the way! :mrgreen:

---

### Post by Tomy on 2005-10-05
[quote=trinaryouroboros]Hey all,

This is an easy one, took me a short bit to find a decent way to do this. Basically after doing this you should be able to have a unique wallpaper for every Workspace you have in Gnome. This is what KDE does already, but Gnome never implemented.

You'll firstly need to have the proper libraries. 

The first one should be available in your Synaptic Package Manager. Install: libglademm-2.4-1
...
[/quote] 
I installed several more libraries -- maybe I did not need them but Akbar's instruction's mentioned them and based on other posts it seemed they were required. I also came up with an error that was resolved by installing libxml++2.6.

A while back I posted this:
**HOWTO: Install "wallpapoz" and have different wallpapers on each workspace**
[http://ubuntuforums.org/showthread.php?t=69507]("http://ubuntuforums.org/showthread.php?t=69507")
It includes a script that worked for me on Hoary.

If some of the dependencies are not needed I will edit my script. No need to install extra stuff.

Tomy

---

