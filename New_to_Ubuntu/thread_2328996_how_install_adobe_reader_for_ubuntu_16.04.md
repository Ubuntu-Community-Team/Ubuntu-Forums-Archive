---
title: "how install adobe reader for ubuntu 16.04"
date: 2016-06-26
forum: New to Ubuntu
---

### Post by newblank25 on 2016-06-26
I was following instructions for installing adobe for ubuntu 16.04. This is what i got on terminal screen. sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner"[sudo] password for michael: 
-p7-1456c:~$ sudo apt-get update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]   
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                        
Hit:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Ign:9 [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                    
Get:10 [http://archive.canonical.com](http://archive.canonical.com) precise Release [8,180 B]
Get:11 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]
Get:13 [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages [6,997 B]
Get:14 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [7,860 B]
Get:15 [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en [4,440 B]
Fetched 122 kB in 0s (141 kB/s)                                    
Reading package lists... Done
W: [http://archive.canonical.com/dists/precise/Release.gpg:](http://archive.canonical.com/dists/precise/Release.gpg:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)
michael@michael-p7-1456c:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 acroread : Depends: nspluginwrapper but it is not installable
E: Unable to correct problems, you have held broken packages
Can any one help? Is it possible to download as window file & use wine to operate adobe?THX

---

### Post by TheFu on 2016-06-27
I'm fortunate in that I don't need to use Adobe for anything - there are F/LOSS tools that replace Acrobat reader for my requirements.
**evince** for reading, searching, viewing.
**xournal** for editing.

But if you need the true, Acrobat stuff, and *sometimes people do*, [https://appdb.winehq.org/appview.php?appId=847](https://appdb.winehq.org/appview.php?appId=847) has info on making it work under WINE.

The nspluginwrapper is just for the web-broswer plug-in. Shouldn't have anything to do with downloading a pdf file and using the reader on the desktop directly.

BTW, whenever posting "code", it is best to use "code tags" so the output is readable and lined up for people used to seeing it inside a terminal. Thanks.

---

### Post by enrigp on 2016-10-06
I have Ubuntu Xenial 16.04 and I have installed Acrobat Reader 9.5.5 by the package adobereader-enu (apt-get install adobereader-enu)
Try it! it works for me and the program works OK BUT the plugin for the browser doesn't appear, I suppose because the broken dependency of nspluginwrapper

I need the plugin in the browser to fill documents OnLine from firefox, but it doesn't work in xenial (in 14.04 works OK) If anyone knows how to make it works, please tell it me

---

### Post by kurt18947 on 2016-10-07
> **enrigp said:**
> I have Ubuntu Xenial 16.04 and I have installed Acrobat Reader 9.5.5 by the package adobereader-enu (apt-get install adobereader-enu)
Try it! it works for me and the program works OK BUT the plugin for the browser doesn't appear, I suppose because the broken dependency of nspluginwrapper

I need the plugin in the browser to fill documents OnLine from firefox, but it doesn't work in xenial (in 14.04 works OK) If anyone knows how to make it works, please tell it me

If no one else has a recommendation, you might try using Chrome. Adobe's support for Linux has been sketchy and Google seems to have their own thing with cooperation from Adobe. There's talk that Mozilla may incorporate support for some of Google's stuff like pepperflash and PDF.  Another option might be playonlinux:

[https://www.playonlinux.com/en/app-2653-Adobe_Acrobat_Reader_DC.html](https://www.playonlinux.com/en/app-2653-Adobe_Acrobat_Reader_DC.html)

This would not be my first choice due to security concerns 
> Known issues  Adobe Acrobat Reader DC cannot open in Protected Mode, on first run select 'Always open with Protected Mode disabled'.
  Premium features, online services and updates do not work.


but sometimes we have to choose the less risky rather than the more safe.

---

### Post by kevdog on 2016-10-09
Can you post the instructions?  You're using xenial however it seems like you are using a package from the precise repository?

---

### Post by the-mcnaveen on 2017-04-23
Installing Dependencies for adobe reader

sudo apt-get install gtk2-engines-murrine:i386 libcanberra-gtk-module:i386 libatk-adaptor:i386 libgail-common:i386

Install Adobe Reader using the following commands
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner" 
sudo apt-get update 
sudo apt-get install adobereader-enu

  After installing you have to Remove precise repository using the following commands
sudo add-apt-repository -r "deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner" 
sudo apt-get update

---

