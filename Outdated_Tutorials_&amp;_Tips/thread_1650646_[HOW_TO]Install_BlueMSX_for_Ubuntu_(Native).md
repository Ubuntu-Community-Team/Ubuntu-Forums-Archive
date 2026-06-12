---
title: "[HOW TO]Install BlueMSX for Ubuntu (Native)"
date: 2010-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by twogunmickey on 2010-12-22
How to install BlueMSX lite (Native non-gui version) in Ubuntu

I did this on Ubuntu 10.10 64bit.  I'm sure it will work on older version of Ubuntu, but I can not verify it.  Also there is an i586 rpm in the OpenSUSE repository if anyone wants to take a try it on non-64 bit systems.

You need to convert the rpm to a deb.  So you need 'alien' installed.  If you do not have alien install then do so by opening the terminal and pasting in the following command to install all required packages.

#apt-get install alien

and this command will download the BlueMSX rpm 

#wget ftp://ftp.pbone.net/mirror/ftp5.gwdg.de/pub/opensuse/repositories/Emulators/openSUSE_Factory/x86_64/blueMSX-2.8-3.21.x86_64.rpm

This will convert it to a deb

#sudo alien -k blueMSX-2.8-3.21.x86_64.rpm

this will install it.

#sudo dpkg -i bluemsx_2.8-3.21_amd64.deb

Extra info

Config is found in ~/.bluemsx

Once you have BlueMSX lite installed you will need to know the Command Line Arguments since this is a non-gui version.  They can all be found here:
http://www.msxblue.com/manual/commandlineargs_c.htm

Example 
#bluemsx - /rom1 "/home/username/Downloads/game1.mx2"

*Note for some reason when I use ~ in place of "/home/username/" it does not start the game

Also you can tell ubuntu to open .mx2 file with bluemsx - /rom1 (and whatever other settings you want) and games will run with a double click.

If anyone has a recommendation on a simple frontend that would be awesome.

** I can't figure out what key (or key combo) makes it exit.  when windowed you just click (x).  But fullscreen this is a problem.  I'm sure that keys can be remaped by messing with the ini file and it's just a matter of mapping exit to what ever combo you want but I've not figured it out yet.

That's all for now enjoy.

---

