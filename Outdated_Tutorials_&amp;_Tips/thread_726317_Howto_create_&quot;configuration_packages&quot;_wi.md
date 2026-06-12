---
title: "Howto: create &quot;configuration packages&quot; with equivs"
date: 2008-03-16
forum: Outdated Tutorials &amp; Tips
---

### Post by ruibernardo on 2008-03-16
This howto is to create "configuration packages". Packages that you install with your configuration to replace the original/default one. It was created because I wanted to make "configuration packages", but couldn't find a webpage to make it from scratch. This started after I found [this page]("http://www.eyrie.org/%7Eeagle/notes/debian/server.html") and curiosity made the rest.

Very important, you should... you have to... no, you *must* read the [Debian policy Manual]("http://www.debian.org/doc/debian-policy/"), specially (but not only) about "[dpkg-divert]("http://www.debian.org/doc/debian-policy/ap-pkg-diversions.html")", files inside a [.deb package]("http://www.debian.org/doc/debian-policy/ch-controlfields.html") (control and the others) and the [Debian package management system]("http://www.debian.org/doc/manuals/reference/ch-package.en.html"), among the other chapters, to understand the whys of all this. I recommend it. After reading the Debian Policy Manual you'll have a better understanding of how and why Debian and Ubuntu work - a must read.

References:[LIST]
[*]  [equivs: option to add additional files to a package]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=449542") in [http://bugs.debian.org](http://bugs.debian.org) (Thank you for this [long awaited] feature, [Anthony Towns]("http://azure.humbug.org.au/%7Eaj/blog/2007/11/14/")!);
[*]  [http://wiki.debian.org/ConfigPackages](http://wiki.debian.org/ConfigPackages)
[*]  [Diversions - overriding a package's version of a file (from old Packaging Manual)]("http://www.debian.org/doc/debian-policy/ap-pkg-diversions.html")
[*]and this [page]("http://www.eyrie.org/%7Eeagle/notes/debian/server.html")..[/LIST]This howto assumes a fresh Ubuntu install. If you make it on a system where you already modified configuration files, things will revert to those modified files after you remove the new "configuration package". Your call. It assumes you installed "equivs 2.0.7-01, install the package from [Debian repository]("http://packages.debian.org/lenny/all/equivs/download").

So here is my *mini* version of what I found about all this. It's not for enterprise deployment, but it can get you started. Add debian-installer + preseed_file + dummy package of dependencies (usually called virtualpackage )("equivs") + configuration packages ("equivs"+"dpkg-divert") = a good start. Add [puppet]("http://reductivelabs.com/trac/puppet/wiki/PuppetIntroduction") to all this and you're a pro.

For this tutorial, I've created two dummy packages with "equivs" version 2.0.7-0.1 (from Debian unstable repos, Ubuntu don't have this new version - apparently Hardy will miss it too). If you can't or don't want to install "equivs" from Debian repos, you still can download the test dummy packages I made and try this howto: [http://nonetdebs.unixpod.com/main-package/](http://nonetdebs.unixpod.com/main-package/).

The "**main-package**" will be a dummy package with only one configuration file (the one we want to change later). Think about this "main-package" as "openssh-server" or any other package from the repositories with (at least) a configuration file. The other dummy package will be "**main-package[COLOR=Black]-config[/COLOR]**". It will have our new configuration file. It will be our "configuration package".


[SIZE=4]Objective[/SIZE]

To install "main-package" with its default configuration file (as usual when you install a package). To install "main-package-config" with my new configuration files without overwriting the original/default files of "main-package" and preserving them somewhere untouched. Later, I remove my "main-package-config" package and the original configuration of "main-package" is restored (the "normal" behaviour for "normal" files, but not with "conffiles").

Downloads: if you don't or can't create the packages, download them here: [http://nonetdebs.unixpod.com/main-package/](http://nonetdebs.unixpod.com/main-package/).

Now let's make the dummy packages.

[SIZE=4]
main-package[/SIZE]

With "equivs" 2.0.7-0.1 installed, create a dummy "control" file to create the new package (as a normal user - "man equivs-control" and "man equivs-build" for more info):
```
equivs-control main-package
```Edit that file and change/paste to look like this:
```
nano main-package
``````
### Commented entries have reasonable defaults.
### Uncomment to edit them.
Section: misc
Priority: optional
Standards-Version: 3.6.2

Package: main-package
Version: 0.0.1
Maintainer: Your Name <a.spam.box@mail.sj>
# Pre-Depends: <comma-separated list of packages>
# Depends: <comma-separated list of packages>
# Recommends: <comma-separated list of packages>
# Suggests: <comma-separated list of packages>
# Provides: <comma-separated list of packages>
# Replaces: <comma-separated list of packages>
Architecture: all
# Copyright: <copyright file; defaults to GPL2>
# Changelog: <changelog file; defaults to a generic changelog>
# Readme: <README.Debian file; defaults to a generic one>
Files: /home/myuser/main-package.conf /etc/main-package.conf
Description: <short description; defaults to some wise words>
 long description and info
 .
 second paragraph

```**Notes about this file**: look at the "Files:" line. It will say to the "equivs-build" command that a file (/home/myuser/main-package.conf - change the path to adapt to your case) will be included on the package and will be installed in /etc/main-package.conf. Because that a file is declared in "Files:" and is to be installed by the .deb package to "/etc/main-package.conf", this automatically makes it a "conffiles", so dpkg will be always with an eye on it (if you change it, dpkg will find out when it upgrades the package - Debian Policy).

Before we build the package, create the /home/myuser/main-package.conf:
```
nano ~/main-package.conf
```And put the following in it:
```
# Original main-package.conf file. 
# Do not touch it!! It belongs to dpkg.

```Now we can build the package with equivs-build:

> $ equivs-build main-package
dh_testdir
dh_testroot
dh_clean -k
dh_testdir
dh_testroot
dh_install
dh_installdocs
dh_installchangelogs
dh_compress
dh_fixperms
dh_installdeb
dh_gencontrol
dh_md5sums
dh_builddeb
dpkg-deb: construindo pacote `main-package' em `../main-package_0.0.1_all.deb'.

The package has been created.
Attention, the package has been created in the current directory,
not in ".." as indicated by the message above!
$ ls -la main-package*
-rw-r--r-- 1 myuser myuser  856 2008-03-16 17:17 main-package
-rw-r--r-- 1 myuser myuser 2174 2008-03-16 17:22 main-package_0.0.1_all.deb
-rw-r--r-- 1 myuser myuser   76 2008-03-16 17:22 main-package.conf[SIZE=4]main-package-config[/SIZE]

Half done. Now create the "control" file for the second dummy package. It will be the "configuration package":
```
equivs-control main-package-config
```Paste/adapt the following on the file main-package-config:
```
nano ~/main-package-config
``````
### Commented entries have reasonable defaults.
### Uncomment to edit them.
Section: misc
Priority: optional
Standards-Version: 3.6.2

Package: main-package-config
Version: 0.0.1
Maintainer: Your Name <a.spam.box@mail.sj>
Pre-Depends: main-package
Depends: main-package
# Recommends: <comma-separated list of packages>
# Suggests: <comma-separated list of packages>
# Provides: <comma-separated list of packages>
# Replaces: <comma-separated list of packages>
Architecture: all
# Copyright: <copyright file; defaults to GPL2>
# Changelog: <changelog file; defaults to a generic changelog>
Readme: /home/myuser/README
Extra-Files: /home/myuser/configs/main-package-config/main-package-config.tar.gz
File: postinst
 #!/bin/sh -e
 # preinst for main-package-config. Divert some configuration file of main-package.
 .
 set -e
 .
 PKG=main-package-config
 .
     if [ "$1" = configure ] ; then
 .
     tar zxvf --no-same-owner /usr/share/doc/$PKG/$PKG.tar.gz -C /
 .
     # make sure to include all the files inside $PKG.tar.gz in this *for* cycle.
     for f in main-package.conf
     do
         dpkg-divert --add --package ${PKG} --rename --divert /etc/$f.distrib /etc/$f
         [ \! -e /etc/$f -o -L /etc/$f ] && ln -sf /etc/site/$f /etc/$f
     done
 .
     fi 
 .
 #DEBHELPER#
 .
     exit 0
File: prerm
 #!/bin/sh -e
 # prerm for main-package-config. Divert some configuration file of main-package.
 .
 set -e
 .
 PKG=main-package-config
 .
  if [ "$1" = remove -o "$1" = purge ] ; then
 .
     # make sure to include all the files inside $PKG.tar.gz in this *for* cycle.
     for f in main-package.conf
     do
         [ -L /etc/$f ] && rm /etc/$f
         dpkg-divert --remove --package main-package-config --rename --divert /etc/$f.distrib /etc/$f
     done 
 .
 fi
 .
    #DEBHELPER#
 .
    exit 0
Description: <short description; defaults to some wise words>
 long description and info
 .
 second paragraph

```**Notes about this file:** this package is more complicated (it has to deal with several things). Basically it has 2 external files and the deb scripts. The external files must exist and in the place the files path points to (change the path to adapt to your case):

Readme: /home/myuser/README (my sample README [here]("http://nonetdebs.unixpod.com/main-package/README"). Change it if you want)
Extra-Files:  /home/myuser/configs/main-package-config.tar.gz (download it from [here]("http://nonetdebs.unixpod.com/main-package/main-package-config.tar.gz"), if you want).

The README file is supposed to be in /home/myuser/README. It explains what this config package is and what it does. The "Extra-Files:" line says "equivs-build" to include the ~/configs/main-package-config.tar.gz file (we'll do it right after this...). This main-package-config.tar.gz file will have our new configuration file. Files listed in the "Extra-Files:" line in the "control" file will always be installed in /usr/share/docs/$PACKAGENAME/. So that's where we'll find it when the "configuration package" is installed. «Why not use "Files:" like in "main-package"? It would install it over the original file and the job would be done!» But we can't. If our new configuration file was in a "Files:" line, dpkg would try to install it over the other file (overwrite). Also, it would be considered a "conffile", so any changes we would made in it would be found by dpkg later.

> Configuration file `/etc/ssh/ssh_config'
   ==> Deleted (by you or by a script) since installation.
   ==> Package distributor has shipped an updated version.
     What would you like to do about it ?  Your options are:
      Y or I  : install the package maintainer's version
      N or O  : keep your currently-installed version
        D     : show the differences between the versions
        Z     : background this process to examine the situation
   The default action is to keep your current version.
So we will "disguise" our file in the "Extra-Files:" line, and it will be considered as some banal documentation, leaving dpkg hands out of it (this is a "equivs" new version feature). When the package is installed, the "preinst" script will extract the files to "/etc/site/" (where our files will be), and will "dpkg-divert" the original files, so dpkg don't loose those. Then a link is created between the "/etc/site/main-package.conf" and "/etc/main-package.conf". The original/default "/etc/main-package.conf" was renamed "/etc/main-package.conf.contrib" by "dpkg-divert" and will not be touched by us, only by dpkg upon upgrades of "main-package". 

This will make upgrades less "noisy" as the changes will be only the default ones (the user hasn't change it, so dpkg will only report improvements and news on the upgrades, no users modifications and other confusions will be reported. Finally a check is made if the configuration file was already "dpkg-diverted" before. This is done to verify that the file wasn't already "dpkg-diverted" (if the "main-package-config" package was/is already installed), obviously. If you need to restart a service to apply changes, comment out and adapt the commented lines with "update.rc-d" commands. When you remove the config package, links are removed and the original/default are "dpkg-diver --remove" back to their original filenames/place.

Before we build the "configuration package", we need the external files (main-package-config.tar.gz and README) on their places. You can find my sample README [here]("http://nonetdebs.unixpod.com/main-package/README"). Next, how I made my main-package-config.tar.gz file (you can download it from [here]("http://nonetdebs.unixpod.com/main-package/main-package-config.tar.gz")). It's just TAR of a directory:
> $ mkdir -p configs/main-package-config
$ cd configs/main-package-config
$ mkdir -p etc/site
$ cd etc/site
$ nano main-package.conf
Paste this:
> # This is our customized version of main-package.conf!
# Do whatever you want with it, dpkg will never find out ;)
To compress the file, type cd to the ~/configs/ directory, just outside main-package-config/etc/site directory, and run the "tar" command:> $ cd ../..
$ tar czvf main-package-config.tar.gz etc/
etc/
etc/site/
etc/site/main-package.confReady to run, lets build the "configuration package":
> $ cd ~/
$ equivs-build main-package-config[SIZE=4]


Install and verification[/SIZE]

If you didn't get any errors, now you can install the new dummy packages. We'll do it with bare dpkg. You can create a local repositories for your new packages based in this [help.ubuntu.com]("https://help.ubuntu.com/community/Repositories/Personal") page and then use "apt-get" to install them. We'll jump this step and install with dpkg. Install the dummy packages by this order (using dpkg):> $ sudo dpkg -i main-package_0.0.1_all.deb
[...]
$ sudo dpkg -i main-package-config_0.0.1_all.deb
Selecting previously deselected package main-package-config.
(Reading database ... 189873 files and directories currently installed.)
Unpacking main-package-config (from main-package-config_0.0.1_all.deb) ...
Setting up main-package-config (0.0.1) ...
etc/
etc/site/
etc/site/main-package.conf
Adding `diversion of /etc/main-package.conf to /etc/main-package.conf.distrib by main-package-config'On the "control" file of "main-package-config" we created a pre-dependency to "main-package". That's because the "main-package" must be completly installed and configured before "main-package" is called (for the case they are installed with apt-get and in the middle of a 20 package install), so we can change its files with "main-package-config. If it was just a dependency, "main-package-config" could be called before the configuration file of "main-package" (/etc/main-package.conf) was even installed (first dpkg installs the binaries of the packages, then it configures them). So "main-package-config" pre-depends on "main-package". We can't remove "main-package" without removing "main-package-config", but we can remove "main-package-config" without removing "main-package" (leaving the original/default files where they should be). Then we can remove "main-package". This works even with "--purge" to "main-package-config" - the original/default files of "main-package" will survive a "--purge" of "main-package-config" (normally they wouldn't, and if you later tried to install again "main-package", because it's configuration file was "purged" when "main-package-config" was "purged", the original files would never be installed again - dpkg had maked those "conffiles" as removed, so it wouldn't install them again - a typical "missing configuration files" situation after a user "rm" command).

Check what happened:
> $ ls -la /etc/main-package*
lrwxrwxrwx 1 root root 27 Mar 16 19:08 /etc/main-package.conf -> /etc/site/main-package.conf
-rw-r--r-- 1 root root 76 Mar 16 17:22 /etc/main-package.conf.distrib
$ ls -la /etc/main-package*     
lrwxrwxrwx 1 root root 27 Mar 16 19:08 [COLOR=Lime]/etc/main-package.conf -> **[COLOR=Black]/etc/site/main-package.conf[/COLOR]**[/COLOR]
-rw-r--r-- 1 root root 76 Mar 16 17:22 [COLOR=Red]/etc/main-package.conf.distrib[/COLOR]
$ cat /etc/main-package.conf
[B] # This is our customized version of main-package.conf!
# Do whatever you want with it, dpkg will never find out ;)[/B] $ ls -la /etc/site/
-rw-r--r--   1 root root  115 Mar 16 17:36 main-package.confRemove the "configuration package":
> $ sudo apt-get remove main-package-config --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  main-package-config*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
Need to get 0B of archives.
After unpacking 24.6kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 189877 files and directories currently installed.)
Removing main-package-config ...
Removing `diversion of /etc/main-package.conf to /etc/main-package.conf.distrib by main-package-config'
Check again:
> $ ls -la /etc/main-package*
-rw-r--r-- 1 root root 76 Mar 16 17:22 **/etc/main-package.conf**
$ cat /etc/main-package.conf[B]
# Original main-package.conf file.
# Do not touch it!! It belongs to dpkg.[/B]
$ ls -la /etc/site/
-rw-r--r--   1 myuser myuser  115 Mar 16 17:36 main-package.conf
All this can be tested and is working with the dummy packages. I made this today, so I didn't (and will not with this dummy packages) see any upgrades to verify if all works as stated, but the rationale is there, so it just *should* work.

If you survived this looooong post, or just still didn't fall asleep, and made the effort to try all this, please confirm if it worked with you and/or what didn't.

EDIT1: fixed bug. Extracted files in /etc/site/ where with normal user owner (from inside the archive). --no-same-owner in tar extract command to extract them as root (owner's who's extracting).
EDIT2: loong post...

---

### Post by afrodeity on 2009-12-03
I need to create a dummy package for libkrb5-3 callled libkrb53. Uncertain if main-package would be libkrb5-3 or libkrb53? Sorry, total noob.

---

### Post by jimcooncat on 2010-08-14
Do you think this would work well?

custom-openssh-server (metapackage)
depends: custom-openssh-server-config, openssh-server

custom-openssh-server-config (adds non-standard port)
contains: /etc/ssh/sshd_config

openssh-server (straight from the official repo)

------------------
The idea here is to install our custom config before installing the package we want. Good packages are not supposed to overwrite configuration files.

So when we add our metapackage to a preseed, it would automatically do the right thing. If openssh gets a security update, version numbering would work correctly. 

Since we could have some sensitive information in the config files, we could use an ssh repository with apt, or at a minimum only make our personal repository only available on the local network.

Can anyone explain the downsides to this approach?

---

