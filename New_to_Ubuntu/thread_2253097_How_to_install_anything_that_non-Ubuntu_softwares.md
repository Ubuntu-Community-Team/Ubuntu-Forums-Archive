---
title: "How to install anything that non-Ubuntu softwares?"
date: 2014-11-17
forum: New to Ubuntu
---

### Post by flaymond on 2014-11-17
Hey, this is the biggest problem for me. I don't know how to install other than the software on Ubuntu software center....is there anyway to install downloaded programs from firefox.

---

### Post by kc1di on 2014-11-17
That would depend on what type of program it is and how it is packaged. if your talking windows programs you can't install them on Linux.
(Except with wine, which can be a pain.) If it's a .deb pacakage - then you can install it using the command line tool dpkg. 
go to a terminal and type ```
sudo dpkg --help 
``` for more information on how this command works. 
I always install synaptic and gdebi also they are good , but older package management tools. 
you can install them with the following terminal commands ```
sudo apt-get install synaptic gdebi
``` or they can be installed from the software center.

Tell us a bit about what downloaded programs you are trying to install and we may be able to help further.

---

### Post by grahammechanical on 2014-11-17
It should also be noted that some Linux software that we can download from web sites is in the Redhat Package Manager Format (rpm) and that will not run on Ubuntu without being first converted to the Debian package format (deb).

Please be aware that software in the Ubuntu repositories has been code audited to make sure that it does not do anything nasty.

Regards.

---

### Post by flaymond on 2014-11-17
ok kc..let's say i try to download Google Chrome....using the installer was working (WINE)...and it done so well..but....when you close the browser...it disappear and you need to install it again an again (take a while with slow connection)...i want it to installed permanently into the machine....

---

### Post by monkeybrain20122 on 2014-11-17
Why do you use wine? Chrome runs natively on Linux, just download the 32 or 64 bit .deb depending on your archeticture, rght click it and wait for gdebi or the Software Center to install it and that's it. 

.Exe files are Windows exectuables.

---

### Post by slickymaster on 2014-11-17
Or, alternatively, you can add the Google Chrome PPA to your repository thus getting every Chrome update through the update manager.

To add the PPA in Ubuntu 14.04, download and install the key from Google Linux Repository```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
```Then just install it```
sudo apt-get update
sudo apt-get install google-chrome-stable
```

---

### Post by buzzingrobot on 2014-11-17
Software released for installation on Ubuntu is packaged in files ending with '.deb'. Those files can be installed with Software Center, Synaptic, gdebi, or with apt-get on the command line.  A '.deb' package is an archive that contains the actual program files plus scripts and other information needed to move the files to the correct locations, etc.

Not all '.deb' packages are intended for Ubuntu. Those intended for other distributions may install and work on Ubuntu, may install and not work on Ubuntu, or may not install.

You will sometimes see Linux software in 'tar.gz' files.  E.g., 'Widget.tar.gz.'  This is another kind of archive (the 'tar' bit) that's compressed (the '.gz' bit).  While they may contain any kind of a file, they almost always contain source code, not ready-to-install programs.So, 'widget.tar.gz' would contain all the source code files -- often dozens, maybe hundreds -- need to compile and build the program called 'widget'.   These are intended for use by software developers and should be avoided if at all possible by ordinary users, especially new ordinary users.

If you install software from outside the Ubuntu repositories *and* if that software did not come from a similar third-party repository, then the updating software on your system won't be able to install any updates to that software if and when they become available.  Your system maintains a list of software installed via Softwaer Center, Synaptic, or the other tools that know how to install a '.deb' package, and compares it with the software hosted in the repositories your system uses to determine which packages can be updated.

Software packaged in the 'rpm' format used by Red Hat, Fedora, OpenSuse, etc., can often be converted to the .'deb' format.  But, there is no guarantee they will install or run.  The scripts used by an 'rpm' package differ from the scripts used by a '.deb' package and they are not altered by the conversion process.

Re:  Chrome -- It's available for Linux.  Ubuntu packages are available at [www.google.com/chrome](www.google.com/chrome).

---

### Post by flaymond on 2014-11-17
thanks everyone for your help! now i know the concepts..at last

---

### Post by kc1di on 2014-11-17
as has already been pointed out google-chrome is available in .deb packages either from the chrome site or via a PPA (personal package archive)  If downloaded form chrome page 
.deb file and you have installed gdebi as I suggested, you can install the downloaded package by right clicking and selecting gedbi from the programs list.
once install it will automatically be updated as updates are made available by google. 
good luck

---

