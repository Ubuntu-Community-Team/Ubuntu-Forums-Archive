---
title: "downgrading bluefish to previous version"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by Arggg on 2013-06-29
Hi, 
I use Bluefish and I have recently updated it to version 2.2.5.beta1. However, I want to uninstall it and install/revert to a previous version. 
When I uninstall it in through the Software Center, I can only install the latest version I had, 2.2.5beta1...  
I searched the net and tried to install a previous version (after uninstalling the beta1) following the steps bellow but when using $ ./autogen.sh I got the following error "No such file or directory". I don't understand what it means, I need help... :-O
Thanks!

$ wget [www.bennewitz.com/bluefish/stable/source/bluefish-2.2.4.tar.gz](www.bennewitz.com/bluefish/stable/source/bluefish-2.2.4.tar.gz)
Extract Bluefish and cd into it:
$ tar -xzvf bluefish*.tar.gz
$ cd bluefish*
Create the makefile:
$ ./autogen.sh
Compile the sources:
$ make
Install the application:
$ sudo make install

---

### Post by snowpine on 2013-06-29
If you previously had it installed then the .deb should still be in your /var/cache/apt/archives folder. You can install a .deb by clicking on it, or from the command line with "sudo dpkg -i example.deb"

To keep it from upgrading you'll have to "hold" the package: [https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages](https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages)

---

### Post by Arggg on 2013-06-29
[QUOTE=snowpine;12711093]If you previously had it installed then the .deb should still be in your /var/cache/apt/archives folder. You can install a .deb by clicking on it, or from the command line with "sudo dpkg -i example.deb"

hmmm, the only bluefish debs there were the ones from the beta1 version. So, I searched the web and I downloaded a deb from [http://packages.debian.org/sid/all/bluefish-data/download](http://packages.debian.org/sid/all/bluefish-data/download) and installed it through the software center. However, I do not know how to activate it as no icon was created. If I click the file again, I only have the option to reinstall... :confused:  I searched for it in the dash but I only find the debs... so now I have 3 main questions: 
1- was it really installed?!  
2- where is it (can I use commands in the terminal and which ones?)?
3- how can I uninstall it in case I need or want to?!

---

### Post by Dennis N on 2013-06-29
You can download a .deb file for an older version from the Ubuntu packages archive.

1) Purge the current one you have.

2) Get an old one:

**.debs available for:** 
bluefish 1.0.7 (Lucid) - the most unobtrusive. No popup box. I prefer this one. Works fine in Precise (12.04) also. 
bluefish 2.2.2 (Precise)
bluefish 2.2.5 (Quantal)
 
**Source for bluefish 1.0.7 (32 and 64 bit):**
[http://packages.ubuntu.com/lucid/i386/bluefish/download](http://packages.ubuntu.com/lucid/i386/bluefish/download)
[http://packages.ubuntu.com/lucid/amd64/bluefish/download](http://packages.ubuntu.com/lucid/amd64/bluefish/download)


Install with gdebi package installer.

Lock the version so you are not pestered about upgrade.

---

### Post by andrew.46 on 2013-07-02
Easy enough to change versions by using this old guide:

[https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu](https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu)

Have a look at the version numbers before launching in though, looks like this wiki page is one version behind the current stable release...

---

