---
title: "how do i update aMSN"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by hedrian on 2008-07-22
aMSN shows that there is a new version of it( 0.97.1 )
how can i install it

---

### Post by Seisen on 2008-07-22
You will have to wait till it hits the repositories in order to update it, that is one downside of Ubuntu sometimes you don't have all the latest version of packages available.

---

### Post by hedrian on 2008-07-22
isnt there a code or sumthing lyk that to put in a terminal

---

### Post by Joeb454 on 2008-07-22
Not unless you want to compile it from source. I believe thats the only other way to update it sooner

---

### Post by ibuclaw on 2008-07-22
One of multiple ways to do this, some are better than others. But following the general flow of this topic, I won't submit any methods of achieving anything I've suggested.

1) You can download the sourcecode, extract the tarball and install it that way. It isn't rocket science to compile, it is just three basic commands and you are done.
But installing from source in a binary distribution has it's problems. for example, some files may be included in the source-compiled version that aren't in the official binary package version that is distributed along with ubuntu. So if you wish to remove/uninstall amsn in the future, it there is a chance that it **won't entirely uninstall itself**, due to unchartered residual configuration files/binaries hanging around your filesystem.
But, all in all. This is the safe option, you can trust it.

2) You can find a a ready made deb file from a site and install that instead.
This is **potentially dangerous**, especially if that file is downloaded from an **untrusted** source. And the foreign distributors, if they wish, could add malicious source to the program before compiling, leaving your system in a risk of attack and take-over.
But, if you feel confident with it. This is the easiest option, you are probably used to doing it all the time in windows...

3) You can Pin the Ubuntu stable repositories to have a higher priority and update/upgrade amsn to the testing branch.
This is possibly the most sound option available, but problems arise because it can lead to severe breakage if the package requires some dependencies that haven't been stabilised yet. It is also the most complex option. If you don't know what you are doing, you could potentially upgrade your entire system to testing and **ruin it indefinately**!
But, having the last laugh, you can have confidence in doing this because it comes straight from a trusted distributor.

Hope I've given you some food for thought.

Regards
Iain

---

### Post by sharks on 2008-07-22
u can compile a source code but upgrading via update manager will be better. When it hits the repos , some bugs may be fixed.

---

### Post by Sef on 2008-07-22
Amsn has Autopackage.  [URL="AutoPackage
aMSN Installer for Tcl/Tk 8.5
    Distribution independent installer for those who already have Tcl/Tk 8.5 final version"]Download[/URL] the second package: >  AutoPackage
aMSN Installer for Tcl/Tk 8.5
    Distribution independent installer for those who already have Tcl/Tk 8.5 final version 

It is fairly easy to follow the directions.  

If you don't want to use it nor wait to see if it hits the repositories, then compile the source code.

---

### Post by lamego on 2008-07-22
You can get the latest version from [http://www.getdeb.net/app/amsn](http://www.getdeb.net/app/amsn) .

---

### Post by simtaalo on 2008-09-08
> **lamego said:**
> You can get the latest version from [http://www.getdeb.net/app/amsn](http://www.getdeb.net/app/amsn) .


i d/l this installer file, uninstalled the older version using synaptics. ran the installer and it seemed to run fine.

i cant find it in my menu system, or find it anywhere on the hd to run it.

i reverted back to the version on the repository just because i couldnt find this newer version or know whether it installed :confused:

---

