---
title: "help with bloodsheds dev C++"
date: 2007-04-19
forum: Programming Talk
---

### Post by wolfgang959 on 2007-04-19
hi i used to program in C++on windows with 'Bloodshed Dev C++' but then i switched over to Linux ubuntu (6.06 LTS) and i found the same program but for linux so i downloaded it from source forage. but i carnt install it.

i have attached the files so you can see if you can help.

thanks

---

### Post by LaRoza on 2007-04-19
Linux comes with a compiler, in case that is what you need.

All Ubuntu installation packages end in .deb.
Try unzipping the .gz files.

Check their website for any installation instructions.

I also use Dev C++, one installed on my Windows machine, and one portable edition which runs off of my flash drive at any windows computer.

---

### Post by LaRoza on 2007-04-19
**********************************************

-- INSTALLATION INSTRUCTIONS --

* First you need to make sure you have a installed all the C/C++ development packages when installing your distribution (those packages contains gcc, g++, make, standard include files and libraries). You should be able to obtain them on you distribution CD/web site.

* You then need Qt libraries installed. If you don't you can download the Qt package at : [ftp://ftp.trolltech.com/qt/source/qt-x11-2.3.0.tar.gz](ftp://ftp.trolltech.com/qt/source/qt-x11-2.3.0.tar.gz)
Follow the Qt INSTALL file after unpacking it and you should be able to installit quite easily.

* Now that your system is ready to run Dev-C++, type (as root) :

$> sh install.sh
or :
$> ./install.sh

This will launch the installation script. Follow the instructions and after the installation finish, change to your dev-c++ directory ($HOME/dev-c++ by default) and type :

$> ./devcpp 

Dev-C++ is now being launched, enjoy :)

---

### Post by LaRoza on 2007-04-19
A .odt file extension means OpenOffice.org, which Ubuntu has.

That's where I got the above installation instructions.

instal for dev c++.odt 

Is the document that I cut and pasted.

Thanks for the links though, I wanted Dev C++ too for Linux.

Did you install and compile successfully?

---

### Post by Game_Ender on 2007-04-20
Just use the better DevC++ [Code::Blocks](http://www.codeblocks.org) (go to forum and download a nightly).

---

### Post by wolfgang959 on 2007-04-21
thanks allot for your help.

ill try and get it installed on the weekend so ill tell you later how it goes and if i need any more help.

wolfgang:KS

---

### Post by GutsyVirgin on 2008-08-10
LaRoza, I appreciate your effort in making the brief tutorial. However I can't find the "install.sh" file nor a makefile or anything else to compile with. I'm fairly sure I downloaded the right package, but just to be sure here's the link I downloaded from.
[http://www.bloodshed.net/dev/devcpp.htm](http://www.bloodshed.net/dev/devcpp.htm)

I've never actually compiled anything in Ubuntu, so I'm still trying to figure out the process. I did ensure all those libraries you mentioned were installed, and they appear to be so.

[IMG]http://img181.imageshack.us/img181/1663/spmgccscreenshotfu4.png[/IMG] 
[IMG]http://img181.imageshack.us/img181/4333/spmlibsscreenshotls0.png[/IMG]

---

