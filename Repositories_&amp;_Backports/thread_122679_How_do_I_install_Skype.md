---
title: "How do I install Skype?"
date: 2006-01-28
forum: Repositories &amp; Backports
---

### Post by dsokus on 2006-01-28
Thanks to the suggestion the other day I used Synaptic PM to install KDE and it worked all right... But now would like to install Skype and that's not in the Package Manager. I downloaded the .deb file from the website but I can't open it with Archive Manager - it says it's a not supported file type. I tried with KPackage and it gives me dependancy errors - very similar to what happened with all .deb packages I have tried to install this way. 

```
dpkg -i '///home/zsuzsi/Desktop/skype_1.2.0.18-1_i386.deb' ;echo RESULT=$?
Selecting previously deselected package skype.
(Reading database ... 98074 files and directories currently installed.)
Unpacking skype (from .../skype_1.2.0.18-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
RESULT=1
 
```

But I can't find that package in Synaptic. What do I do? :confused: 

Zs

---

### Post by mirons on 2006-01-28
You can install the missing dependencies through synaptic (try find-->libqt3c102-mt) and then skype. I personally installed skype from this archive:
[http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf). (distro "breezy" sections "free non free", everything without quotes). If you add it to your repositories you can play all through synaptic. That's the best solution IMHO.

---

### Post by kcr on 2006-01-28
Use [Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix") it installs skype along with just about every other thing you'll ever need.

---

### Post by Ramon on 2006-01-28
sudo apt-get install skype

---

### Post by dsokus on 2006-01-28
[QUOTE=mirons]You can install the missing dependencies through synaptic (try find-->libqt3c102-mt) and then skype. I personally installed skype from this archive:
[http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf). (distro "breezy" sections "free non free", everything without quotes). If you add it to your repositories you can play all through synaptic. That's the best solution IMHO.[/QUOTE]
But I can't find libqt3c102-mt in Synaptic. :(

---

### Post by dsokus on 2006-01-28
Meanwhile I have found Skype in the Applications->Internet tab and it works - I don't know how it got in there but, oh well. :D

I still get the package dependancy thingie in Synaptic, the broken package stuff, but that package cannot be installed, it says. :confused: On the other hand, I just installed Automatix and that seems to work ok now too. 

Thank you!!

---

### Post by aysiu on 2006-01-28
Even the Wiki advises this (and it worked for me), but for some strange reason the best way to install Skype in Ubuntu is to use [the RPM for Fedora Core 3](http://www.skype.com/go/getskype-linux-fc2) and then save it to your desktop and ```
sudo alien -i skype*.rpm
```

---

### Post by Sparkalo on 2006-01-28
Just a reminder, if it still says that the packages are broken, why not remove them and reinstall?  sudo apt-get remove packagenamehere will do the trick : P

Have a wonderful time!

---

### Post by kecci on 2006-02-01
you can download the package of the library you miss from here
[http://debian.fastweb.it/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb](http://debian.fastweb.it/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb)
and install it with 
```
 sudo dpkg -i ~path_you_downloaded_the_DEB/libqt3c102-mt_3.3.4-3_i386.deb
```
if it still complains about dependencies, you can try to fix them with
```
 sudo apt-get install -f 
```

---

### Post by Kaustav on 2006-02-03
I installed Skype on Ubuntu using the an RPM and alien.  It installed with no error and appears in my Internet Apps folder but when I select it nothing loads.  Anyone know why?  How do I uninstall it?  If I try and run it from the command line I get more info:

kbhattac@ubuntu-kaustav:~/Desktop$ sudo skype &
[1] 2201
kbhattac@ubuntu-kaustav:~/Desktop$ skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

[1]+  Exit 127                sudo skype
kbhattac@ubuntu-kaustav:~/Desktop$ sudo apt-get install libqt-mt.so.3
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libqt-mt.so.3
kbhattac@ubuntu-kaustav:~/Desktop$


1. Where do I download a package list from?
2. Where do I copy the package list to?

---

### Post by durand on 2006-02-03
I found a different way to install it using apt. Just add there repositories to /etc/apt/sources.list:
```
sudo gedit /etc/apt/surces.list
```
In gedit, go to the last line in the file and add:
```
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
```
Then update apt:
```
sudo apt-get update
```
install skype :
```
sudo apt-get install skype
```
That did it for me.\\:D/

---

### Post by davidmaxwaterman on 2006-02-06
[QUOTE=kcr]Use [Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix") it installs skype along with just about every other thing you'll ever need.[/QUOTE]

Correct me if I'm wrong, but that's fine and dandy if you have an x86 CPU; anything else, and you're out of luck.

---

### Post by davidmaxwaterman on 2006-02-06
[QUOTE=mirons]You can install the missing dependencies through synaptic (try find-->libqt3c102-mt) and then skype. I personally installed skype from this archive:
[http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf). (distro "breezy" sections "free non free", everything without quotes). If you add it to your repositories you can play all through synaptic. That's the best solution IMHO.[/QUOTE]

Any places that have it for amd64?

---

### Post by sophtpaw on 2006-02-08
[QUOTE=kecci]you can download the package of the library you miss from here
[http://debian.fastweb.it/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb](http://debian.fastweb.it/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb)
and install it with 
```
 sudo dpkg -i ~path_you_downloaded_the_DEB/libqt3c102-mt_3.3.4-3_i386.deb
```
if it still complains about dependencies, you can try to fix them with
```
 sudo apt-get install -f 
```[/QUOTE]
 

the problem with this is that it requires first removing libqt3-mt. This is probably required for other things in Ubuntu. I don't know that it is safe to replace it with libqt3c102-mt.
which means having to install skype and get around the libqt3c102-mt dependency requirement of skype by other means. 

some say using alien to install skyp.rpm works.

I tried that. Don't know if i had to remove my pre-existing version of skype first, or if the .rpm version would have just replaced it. In all case i still don't have a working skype on desktop. 

Keep getting 'dial failed' and sometimes error with sound device ???

I love Linux and i know it's not their fault, but sometimes i am envious of mac and windows users where things like this just work and where they have the latest developments like video cam easily available

*sigh*

--
sophtpaw

---

### Post by davidmaxwaterman on 2006-02-08
[QUOTE=sophtpaw]
I love Linux and i know it's not their fault, but sometimes i am envious of mac and windows users where things like this just work and where they have the latest developments like video cam easily available
[/QUOTE]

Works just fine on Fedora....which I've switched back to for the moment :(

Max.

---

### Post by rohitsb on 2008-04-30
> **davidmaxwaterman said:**
> Any places that have it for amd64?

Try this:

   1. Install the ia32-libs package from Synaptic
   2. Download Skype package for Ubuntu ([WWW] [http://skype.com/download/skype/linux/](http://skype.com/download/skype/linux/))
   3. Install it: sudo dpkg --install --force-architecture --force-depends <downloaded_package>

Basically, the libs will allow you to use the 32-bit applications on 64-bit systems. Detailed information can be found at [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

RSB

---

### Post by kiridude on 2009-03-24
Easiest way to install skype:

- Goto skype.com and download for Ubuntu.
- Right click on the downloaded file and select "open with gdebi package installer"
- Then just follow instructions. Additional packages necessary will be downloaded automatically.

EASY !

---

### Post by outskut on 2010-01-29
Wow, that was hard.  Thank you kiridude.  It looks either like a lot of the secondary list update sites are out of date or there's some other problem with updating the package manager such as url typos.  Skype.com should never be out of date though as long as skype exists.

---

### Post by Francewhoa on 2010-03-05
Same issue here. The following worked for me _[http://ubuntuforums.org/showpost.php?p=8919096&postcount=6](http://ubuntuforums.org/showpost.php?p=8919096&postcount=6)_

---

### Post by Arun_Sukre on 2011-03-23
> **kecci said:**
> you can download the package of the library you miss from here
[http://debian.fastweb.it/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb](http://debian.fastweb.it/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb)
and install it with 
```
 sudo dpkg -i ~path_you_downloaded_the_DEB/libqt3c102-mt_3.3.4-3_i386.deb
```
if it still complains about dependencies, you can try to fix them with
```
 sudo apt-get install -f 
```


thanks

---

### Post by mav+ on 2011-03-29
i already have skype installed on my maverick but when i run it , skype never show up. I try the other way, using terminal and when i start it, there's something issue like this 
> skype: symbol lookup error: /usr/lib/libQtNetwork.so.4: undefined symbol: _ZN16QIODevicePrivate4peekEPcx
what should i do next? :(

---

### Post by stchman on 2011-03-31
Skype is in the partner repository and works VERY well.  I use it all the time.

---

