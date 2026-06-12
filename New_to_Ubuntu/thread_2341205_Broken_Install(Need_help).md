---
title: "Broken Install?(Need help)"
date: 2016-10-25
forum: New to Ubuntu
---

### Post by krisb1220 on 2016-10-25
Hi, I'm new to Ubuntu, and well Linux as a whole.. 

I downloaded the 16.04.1 .iso from the download, and used a Live USB Installer(Universal USB) to convert my flashdrive to a bootable drive. 

I installed everything normal, I suppose, basic computer and web functions etc works fine, but it's basically like I'm running on Windows without a few key functions. 

When I try to install things, such as "Wine" for example I would type in: 

```

sudo apt-get install wine-devel-i386

```

but I would get a return of a list of unmet dependencies, and then: 

```
E: Unable to correct problems, you have held broken packages.
```
to see full console output please click here, as it is quite lengthy: [http://pastebin.com/ww5Recyd](http://pastebin.com/ww5Recyd)


Additional problems include(but really, really isn't limited to) Python 2.7.12 is installed, but I cannot run ANY .py programs through terminal. 

```

user@user-Inspiron-20-Model-3043:~$ python hello.py
python: can't open file 'hello.py': [Errno 2] No such file or directory

```
Yes, hello.py does exist :P 
The contents of it are as follows: 
```

#!/usr/bin/env python
print "Hello world!"

```
Additionally, I have a helloworld.py also that doesn't set the path in the first line(simply print "hello world"), and that also does not work either, same problem.
I have verified my python verison many times, and I do have python3 installed(but also 2), and have tried to write in py3 but it also, again, typically has the exact same outcome. 

I also do not have anything outside of what is already installed on my computer available in Ubuntu Software. I'm not sure if this is the function of U.S, but if it's not then here what I mean: 
I haven't been able to install a single program through Ubuntu Software, Command line(via online repositories, links, sudo apt-get etc, none of it works), and 99% of the time installers don't work either. Program wise, I basically have only what the computer came with. 

I will gladly work with anyone willing to help, and any feedback or attempted help is very much appreciated! Thank you! :)

---

### Post by Bucky Ball on 2016-10-26
Welcome. Please run these commands one after the other.
```

sudo apt update
sudo apt full-upgrade
```

Please post back any errors either command spits out. 

May I ask why you're not just installing Wine from the package manager or with:

```
sudo apt install wine
```

?

---

### Post by krisb1220 on 2016-10-26
> **Bucky Ball said:**
> Welcome. Please run these commands one after the other.
```

sudo apt update
sudo apt full-upgrade
```

Please post back any errors either command spits out. 

May I ask why you're not just installing Wine from the package manager or with:

```
sudo apt install wine
```

?
Doing now my apologies for the late response!!!
I'm likely to get errors with update, but I haven't tried full upgrade. Will post within 5 minutes.

```
> 
***_kris@kris-Inspiron-20-Model-3043:~$ sudo apt update_***
[sudo] password for kris: 
Ign:1 cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary InRelease
Err:2 cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     
Ign:5 http://security.ubuntu.com/ubuntu hoary-security InRelease               
Ign:6 http://gb.archive.ubuntu.com/ubuntu hoary InRelease                      
Hit:7 http://ppa.launchpad.net/diesch/testing/ubuntu xenial InRelease          
Err:9 http://security.ubuntu.com/ubuntu hoary-security Release                 
  404  Not Found [IP: 91.189.88.149 80]
Ign:10 http://gb.archive.ubuntu.com/ubuntu hoary-updates InRelease             
Hit:11 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease       
Err:12 http://gb.archive.ubuntu.com/ubuntu hoary Release                       
  404  Not Found [IP: 91.189.88.161 80]
Err:13 http://gb.archive.ubuntu.com/ubuntu hoary-updates Release               
  404  Not Found [IP: 91.189.88.161 80]
Err:14 http://ubuntu-backports.mirrormax.net hoary-backports InRelease         
  Could not resolve 'ubuntu-backports.mirrormax.net'
Err:15 http://ubuntu-backports.mirrormax.net hoary-extras InRelease
  Could not resolve 'ubuntu-backports.mirrormax.net'
Reading package lists... Done
E: The repository 'cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu hoary-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu hoary Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu hoary-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
_***kris@kris-Inspiron-20-Model-3043:~$ sudo apt full-upgrade***_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
_***kris@kris-Inspiron-20-Model-3043:~$ sudo apt install wine***_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is a virtual package provided by:
  winehq-staging 1.9.21~ubuntu16.04.1
  winehq-devel 1.9.21~ubuntu16.04.1
You should explicitly select one to install.

E: Package 'wine' has no installation candidate
kris@kris-Inspiron-20-Model-3043:~$ 

```

Additionally, I tried to install Gimp. After installing the PPA with minimal errors, and did the whole update/upgrade shibbang i did this
```

kris@kris-Inspiron-20-Model-3043:~$ gimp
The program 'gimp' is currently not installed. You can install it by typing:
sudo apt install gimp
kris@kris-Inspiron-20-Model-3043:~$ sudo apt install gimp
[sudo] password for kris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libbabl-0.1-0 (>= 0.1.10) but it is not installable
        Depends: libgegl-0.3-0 (>= 0.3.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

```
and again, nada :/

Oh, I noticed what was up with the first Wine error, and I fixed the command BUT - 
```

**kris@kris-Inspiron-20-Model-3043:**~$ sudo apt install wine-devel
[sudo] password for kris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-devel : Depends: wine-devel-i386 (= 1.9.21~ubuntu16.04.1)
E: Unable to correct problems, you have held broken packages.
**kris@kris-Inspiron-20-Model-3043:~$ sudo apt install wine-devel-i386**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-devel-i386:i386 : Depends: libasound2:i386 (>= 1.0.16) but it is not installable
                        Depends: libc6:i386 (>= 2.23) but it is not installable
                        Depends: libglib2.0-0:i386 (>= 2.12.0) but it is not installable
                        Depends: libglu1-mesa:i386 but it is not installable or
                                 libglu1:i386 but it is not installable
                        Depends: libgphoto2-6:i386 (>= 2.5.9) but it is not installable
                        Depends: libgphoto2-port12:i386 (>= 2.5.9) but it is not installable
                        Depends: libgstreamer-plugins-base1.0-0:i386 (>= 1.0.0) but it is not installable
                        Depends: libgstreamer1.0-0:i386 (>= 1.4.0) but it is not installable
                        Depends: liblcms2-2:i386 (>= 2.2+git20110628) but it is not installable
                        Depends: libldap-2.4-2:i386 (>= 2.4.7) but it is not installable
                        Depends: libmpg123-0:i386 (>= 1.13.7) but it is not installable
                        Depends: libopenal1:i386 (>= 1.14) but it is not installable
                        Depends: libpcap0.8:i386 (>= 0.9.8) but it is not installable
                        Depends: libpulse0:i386 (>= 0.99.1) but it is not installable
                        Depends: libudev1:i386 (>= 183) but it is not installable
                        Depends: libx11-6:i386 but it is not installable
                        Depends: libxext6:i386 but it is not installable
                        Depends: libxml2:i386 (>= 2.9.0) but it is not installable
                        Depends: zlib1g:i386 (>= 1:1.1.4) but it is not installable
                        Depends: libasound2-plugins:i386 but it is not installable
                        Depends: libncurses5:i386 but it is not installable
                        Recommends: libcapi20-3:i386 but it is not installable
                        Recommends: libcups2:i386 (>= 1.4.0) but it is not installable
                        Recommends: libdbus-1-3:i386 (>= 1.9.14) but it is not installable
                        Recommends: libfontconfig1:i386 (>= 2.11.94) but it is not installable
                        Recommends: libfreetype6:i386 (>= 2.2.1) but it is not installable
                        Recommends: libgnutls30:i386 (>= 3.4.0) but it is not installable
                        Recommends: libgsm1:i386 (>= 1.0.13) but it is not installable
                        Recommends: libjpeg8:i386 (>= 8c) but it is not installable
                        Recommends: libncurses5:i386 (>= 6) but it is not installable
                        Recommends: libodbc1:i386 (>= 2.3.1) but it is not installable
                        Recommends: libosmesa6:i386 (>= 10.2~) but it is not installable
                        Recommends: libpng12-0:i386 (>= 1.2.13-4) but it is not installable
                        Recommends: libsane:i386 (>= 1.0.24) but it is not installable
                        Recommends: libtiff5:i386 (>= 4.0.3) but it is not installable
                        Recommends: libv4l-0:i386 (>= 0.5.0) but it is not installable
                        Recommends: libxcomposite1:i386 (>= 1:0.3-1) but it is not installable
                        Recommends: libxcursor1:i386 (> 1.1.2) but it is not installable
                        Recommends: libxi6:i386 but it is not installable
                        Recommends: libxinerama1:i386 but it is not installable
                        Recommends: libxrandr2:i386 but it is not installable
                        Recommends: libxrender1:i386 but it is not installable
                        Recommends: libxslt1.1:i386 (>= 1.1.25) but it is not installable
                        Recommends: libxxf86vm1:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.
kris@kris-Inspiron-20-Model-3043:~$ 





```

---

### Post by Bucky Ball on 2016-10-26
Eeeeeeeeeeek!!! You Hoary Hedgehog repos still active??? No wonder you're having issues. Get rid of them ASAP. 5.04 has been dead so long there's little left but dust and a little maggot faeces.

You also still have this activated as a repo by the looks, the Hoary install CD:

```
Ign:1 cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary InRelease
Err:2 cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release
```

Disable it. Go to Software and Updates, and untick anything that is CD or remotely Hoary. Basically, disable all repos that are not 16.04.

PS: It is difficult to understand that if you "downloaded the 16.04.1 .iso from the download, and used a Live USB Installer(Universal USB) to convert my flashdrive to a bootable drive. I installed everything normal ..." you could end up with Hoary repos and the mess that you've got. :-k

My advice would be to completely wipe the drive, make sure you are using a 16.04 install media, and go again.

---

### Post by mastablasta on 2016-10-26
LOL only two PPAs are in sources from xenial:
Hit:7 [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) xenial InRelease          
Hit:11 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease 

i would say 16.04 is not installed in this PC.

---

### Post by krisb1220 on 2016-10-28
> **mastablasta said:**
> LOL only two PPAs are in sources from xenial:
Hit:7 [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) xenial InRelease          
Hit:11 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease 

i would say 16.04 is not installed in this PC.

[COLOR=#1D2129][FONT=Helvetica]wait what did i do.... should i just reinstall??[/FONT][/COLOR]

---

### Post by Bucky Ball on 2016-10-28
I'd say it might clear up this mess. Not sure what you did, but I'd advise getting rid of that partition you are trying to install to (delete it and recreate during install) and install Ubuntu to a clean, new empty partition.

---

### Post by Koobelakahn on 2016-10-28
If i may chime in with a question of my own here...
Why are his Hoary repos still active at all? I figured with each new update of the OS it'd deactivate old/defunct repos. Did this just slip through the cracks, or is this a pretty common occurrence?

---

