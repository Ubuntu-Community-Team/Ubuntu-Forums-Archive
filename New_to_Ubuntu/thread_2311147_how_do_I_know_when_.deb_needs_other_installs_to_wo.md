---
title: "how do I know when .deb needs other installs to work?"
date: 2016-01-25
forum: New to Ubuntu
---

### Post by anotherChris on 2016-01-25
I had my first installation mishap today...

The website for Anki says
> After downloading the .deb file, use your package manager to install the program. It's highly recommended that you install Anki from this package instead of relying on the version distributed with your OS, as the packages in the official repo are often very out of date.
So I downloaded from their website, then tried to install and got this:
```
anotherChris@anotherComputer:~$ sudo dpkg -i anki-2.0.33.deb
[sudo] password for anotherChris: 
dpkg: error processing archive anki-2.0.33.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 anki-2.0.33.deb
anotherChris@anotherComputer:~$ sudo dpkg -i /home/anotherChris/Downloads/anki-2.0.33.deb
Selecting previously unselected package anki.
(Reading database ... 144590 files and directories currently installed.)
Preparing to unpack .../Downloads/anki-2.0.33.deb ...
Unpacking anki (2.0.33) ...
dpkg: dependency problems prevent configuration of anki:
 anki depends on python-qt4; however:
  Package python-qt4 is not installed.
 anki depends on lame; however:
  Package lame is not installed.
 anki depends on python-sqlalchemy; however:
  Package python-sqlalchemy is not installed.


dpkg: error processing package anki (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for shared-mime-info (1.3-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Errors were encountered while processing:
 anki
anotherChris@anotherComputer:~$ 

```

Then I tried from Software Center and got 
> The package system is broken
Then I think I uninstalled
```
anotherChris@anotherComputer:~$ sudo apt-get --purge remove anki
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  anki*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 10.9 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 145145 files and directories currently installed.)
Removing anki (2.0.33) ...
Purging configuration files for anki (2.0.33) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for shared-mime-info (1.3-1) ...
Processing triggers for man-db (2.7.4-1) ...
anotherChris@anotherComputer:~$ ^C
anotherChris@anotherComputer:~$ 

```

Then I used Lubuntu Software Center and it seems to work now.

_**My question:**_
It looks like a lot of other stuff had to be installed along with/before Anki.  How do I know that when a website just puts up a .deb file?  (I don't want to be stuck using the Software Center GUI all my life...)

---

### Post by Sweet_Baby_Jamie on 2016-01-25
It's always safer and better to use the packages in Ubuntu's repositories!  Sometimes the version you download from a web site won't work on your version of Lubuntu (12.04, 14.04, 15.10, whatever).  

But suppose the software you want isn't in the Ubuntu repositories (like Seamonkey, for example).  Probably better to add a PPA (another source of software) so that it's always updated.

---

### Post by vasa1 on 2016-01-25
> **Sweet_Baby_Jamie said:**
> It's always safer and better to use the packages in Ubuntu's repositories!  Sometimes the version you download from a web site won't work on your version of Lubuntu (12.04, 14.04, 15.10, whatever).  

But suppose the software you want isn't in the Ubuntu repositories (like Seamonkey, for example).  Probably better to add a PPA (another source of software) so that it's always updated.

+1. In this case, you may want to get in touch with the developers explaining the dependency issues. I didn't like the way they just posted a link to the .deb without mention of the dependencies or at least stating the version of Ubuntu/Debian the software can run on without issues.

---

### Post by grahammechanical on 2016-01-25
There are rules for Debian packaging that developers should follow when packaging their software. I think that the rules include providing information about other packages that the software depends on and making arrangements for those packages to be also installed.

In the case of this software it depends on python-qt4; lame & python-sqlalchemy but the installer is not instructed to install these packages. It is most likely that these are large packages and the developer does not want to take liberties with what is automatically going to be installed on a user's system. Or there is a reasonable expectation that they may already be installed.

Those packages need to be installed separately. The web site should have provided information on what other software should already be installed on the system for this software to work. Anyway, apt-get will always tell us. As it has told you.

[https://wiki.debian.org/IntroDebianPackaging](https://wiki.debian.org/IntroDebianPackaging)

Regards

---

### Post by buzzingrobot on 2016-01-25
> **anotherChris said:**
> It looks like a lot of other stuff had to be installed along with/before Anki.  How do I know that when a website just puts up a .deb file?  (I don't want to be stuck using the Software Center GUI all my life...)

The package manager in Ubuntu (which the Software Center uses) examines the package selected for installation and determines which, if any, other packages the target packages requires -- the dependencies -- and it then downloads and installs them. If the package manager cannot find one or more of these packages in the repositories a system uses, then it will fail.

That's most likely to happen when you're trying to install a package from an independent site.  Just building a .deb package isn't enough to ensure it will install and work. All you can really be sure of is that the developer was able to build that package on his/her system. 

Synaptic is a popular GUI tool that many use instead of the Software Center. And, of course, you can use apt, apt-get, etc., on the command line. There's onlly one package manager, and all those tools use it.

---

### Post by stalkingwolf on 2016-01-25
if you are using a.deb from the web i always use gdebi to install them. it will tell you if something is missing and try to install it for you.

---

### Post by Dennis N on 2016-01-25
> **stalkingwolf said:**
> if you are using a.deb from the web i always use gdebi to install them. it will tell you if something is missing and try to install it for you.

We hope it does.

I like gdebi package installer too, and the dependencies are supposed to be given in the control file inside the .deb. Sometimes, I found no dependencies were named by the maker, or some are left out. gdebi will declare that "all dependencies are satisfied" and the program will install but will not run. This is very unlikely if you stick to the official repositories! 

All is not lost. You have to figure out yourself what else is missing. Usually by trying to run from a terminal, which informs you of a missing library file it can't load. You then install the package containing that file and try again. Even so, it still may not run due to other problems like graphics requirements.

Example from after a .deb install of World of Goo to Xubuntu 15.04:

```
dmn@Sydney:/opt/WorldOfGoo$ ./WorldOfGoo.bin64
./WorldOfGoo.bin64: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory

```

---

### Post by anotherChris on 2016-01-25
Thanks for good replies and links.  I have posted a message on the Anki website's support forum asking them to revise their presentation of the .deb file.

---

### Post by ian-weisser on 2016-01-25
> **anotherChris said:**
> It looks like a lot of other stuff had to be installed along with/before Anki.  How do I know that when a website just puts up a .deb file?  (I don't want to be stuck using the Software Center GUI all my life...)

All the dependencies are listed in the package's control file...which means you must download and manually open the package to read that control file. Not easy the first time you do it, but the information is both human- and machine-readable.

One pro tip: Apt stores packages in /var/cache/apt/archives. If you put the package there, and use apt instead of dpkg, apt will try to install all the dependencies automatically. 

Good practice is for the package creators to list the dependencies in a human-readable list before you download. Or, better yet, steer you to the appropriate download for your release of Ubuntu.

Better practice is for the package creators to use a PPA or other repositories so apt can install the package natively.

Best practice is for a community volunteer (not the upstream developers) to package the software for Debian, and to package the updates as they occur. This removes a burden from the upstream, and ensures that Debian and Ubuntu packages are both native and up-to-date.

---

