---
title: "Multiple apt-get problems"
date: 2016-01-15
forum: New to Ubuntu
---

### Post by swpffm on 2016-01-15
Dear Ubuntu-Community,

I am an Ubuntu 14.04.3 user for half a year or so and I am very happy with it. But currently I have multiple apt-get problems, that I do not manage to solve myself.

**Where does the problem come from?**

I am not sure about this. One thing is that I had installed texlive by apt-get before. Than I wanted to install some latex-package that I wasn't able to install by apt-get and so I uninstalled my apt-get texlive and reinstalled it by the [install-tl script]("https://www.tug.org/texlive/quickinstall.html"). I am not sure if this is the problem, but since than I got apt get errors more frequently.
[B]
Error messages:[/B]

*Unable to correct problems, you have held broken packages*, e.g.:

```
$ sudo apt-get install libqt4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt4-dev : Depends: libqt4-dbus (= 4:4.6.2-0ubuntu5) but it is not going to be installed
              Depends: libqt4-qt3support (= 4:4.6.2-0ubuntu5) but it is not going to be installed
              Depends: libqt4-xml (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqtcore4 (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqtgui4 (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-network (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-svg (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-webkit (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-sql (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-script (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-scripttools (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-xmlpatterns (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-designer (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-help (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-assistant (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-test (= 4:4.6.2-0ubuntu5) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
              Depends: libqt4-multimedia (= 4:4.6.2-0ubuntu5) but it is not going to be installed
              Recommends: libqt4-opengl-dev (= 4:4.6.2-0ubuntu5) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

--

*Build-dependencies for package could not be satisfied*, e.g.:

```
$ sudo apt-get build-dep lilypond 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have unmet dependencies:
 dblatex : Depends: texlive-latex-extra (>= 2009) but it is not going to be installed
           Depends: texlive-math-extra (>= 2009) but it is not going to be installed
           Depends: texlive-extra-utils (>= 2009) but it is not going to be installed
 groff : Depends: groff-base (= 1.20.1-7) but 1.22.2-5 is to be installed
 guile-1.8-dev : Depends: libncurses5-dev but it is not going to be installed
                 Depends: libreadline6-dev but it is not going to be installed
                 Depends: libgmp-dev but it is not installable
 mftrace : Depends: texlive-base-bin
 texlive-fonts-recommended : Depends: texlive-base (>= 2009-1) but it is not going to be installed
 texlive-generic-recommended : Depends: texlive-base (>= 2009-1) but it is not going to be installed
 texlive-latex-base : Depends: texlive-base (>= 2009-1) but it is not going to be installed
                      Depends: texlive-binaries (>= 2009-1) but it is not going to be installed
 texlive-latex-recommended : Depends: texlive-binaries (>= 2009-1) but it is not going to be installed
 texlive-metapost : Depends: texlive-base (>= 2013.20130512) but it is not going to be installed
                    Depends: texlive-binaries (>= 2013.20130512) but it is not going to be installed
                    Depends: tex-common (>= 3) but 2.06 is to be installed
 ttf-dejavu : Depends: ttf-dejavu-core but it is not going to be installed
              Depends: ttf-dejavu-extra but it is not going to be installed
E: Build-dependencies for lilypond could not be satisfied.
```


*Reinstallation of package is not possible, it cannot be downloaded*, e.g.:

```
$ sudo apt-get install --reinstall zsh                                                                            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of zsh is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Those error messages are examples. They also occur when trying to install other packages.
[B]
What I have done so far:
[/B]
```
sudo apt-get update
sudo apt-get update --fix-missing
sudo apt-get upgrade
sudo apt-get upgrade -f
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoclean
sudo dpkg --configure -a
```

Nothing helped...


I appreciate any help or hints! Thanks alot!

---

### Post by deadflowr on 2016-01-15
Something is really wrong with the version of libqt4-dev it is trying to install.
The trusty version is : **4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1,**
but somehow the version it wants to install is : [B]4:4.6.2-0ubuntu5,

[/B]Could you post the output of:
```
apt-cache policy libqt4-dev
```
To see what repositories you seem to be pulling from, and why the version is not the accurate version.

Somehow I feel that once that is figured out, the rest will probably fall into place...

---

### Post by ian-weisser on 2016-01-15
[EDIT] deadflowr beat me to it. Well done!

---

### Post by swpffm on 2016-01-15
Thanks your answers. I think, I have some deep problems. I rebooted the  system and I only get a black screen. From GRUB I booted into a shell,  so:

```
$ apt-cache policy libqt4-dev
libqt-dev:
   Installed: (none)
   Candidate: 4:4.6.2-0ubuntu5
   Version table:
      4:4.6.2-0ubuntu5 0
         500 http://cz.archive.ubuntu.com/ubuntu/ lucid/main amd64 Packages
```

I consider reinstalling my system. Would be really annoying, cause my last backup is more than 2 weeks old (shame on me), but the black screen signals me that I may have messed my system?

---

### Post by deadflowr on 2016-01-15
Wow, that's insane.

Okay, so now that I've gotten that out...
See if you can check a few things:
Let's find out what version this is with
```
lsb_release -a
```
this should tell us what the version the system now thinks it is running.
I don't think that should have changed, but you never know.

Then probably more helpful, let's look at the repository sources.list
```
cat /etc/apt/sources.list
```

There are a multitude of other things we can look over, but i think these two will be simple to start with.

> [COLOR=#000000]Than I wanted to install some latex-package that I wasn't able to install by apt-get and so I uninstalled my apt-get texlive and reinstalled it by the [/COLOR][install-tl script]("https://www.tug.org/texlive/quickinstall.html")[COLOR=#000000]. I am not sure if this is the problem, but since than I got apt get errors more frequently.[/COLOR]

Indeed, I have a stronger than normal sense that something somewhere in the installer mucked up your stuff.

---

### Post by swpffm on 2016-01-15
Meanwhile I reinstalled my system with [this guide]("https://help.ubuntu.com/community/UbuntuReinstallation"). So I retained my data and I am not sure if this is useful nevertheless:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
```

```
$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu trusty main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ trusty-security universe main restricted multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates universe main restricted multiverse
deb http://archive.ubuntu.com/ubuntu trusty-backports universe main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty main universe restricted multiverse #Added by software-properties
```

But  straight away I came across the same situation where I once decided to  use the texlive installer: I get errors when installing texlive... So  now I am unsure if I should try the installer again or if there is a possibilities to get it installed via apt-get?

```
$ sudo apt-get install texlive texlive-lang-german texlive-doc-de texlive-latex-extra texlive-music 
[sudo] password for swpffm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fonts-lmodern fonts-texgyre latex-beamer latex-xcolor libptexenc1
  libruby1.9.1 libyaml-0-2 lmodern luatex m-tx musixtex pgf pmx
  preview-latex-style prosper ps2eps ruby ruby1.9.1 tex-common tex-gyre
  texlive-base texlive-binaries texlive-extra-utils texlive-font-utils
  texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-generic-recommended texlive-latex-base texlive-latex-base-doc
  texlive-latex-extra-doc texlive-latex-recommended
  texlive-latex-recommended-doc texlive-luatex texlive-pictures
  texlive-pictures-doc texlive-pstricks texlive-pstricks-doc tipa
Suggested packages:
  ri ruby-dev ruby1.9.1-examples ri1.9.1 graphviz ruby1.9.1-dev ruby-switch
  debhelper perl-tk chktex fragmaster xindy latexdiff lacheck latexmk dvidvi
  purifyeps dvipng psutils libfile-which-perl python-pygments dot2tex
  libtcltk-ruby
Recommended packages:
  musixlyr
The following NEW packages will be installed:
  fonts-lmodern fonts-texgyre latex-beamer latex-xcolor libptexenc1
  libruby1.9.1 libyaml-0-2 lmodern luatex m-tx musixtex pgf pmx
  preview-latex-style prosper ps2eps ruby ruby1.9.1 tex-common tex-gyre
  texlive texlive-base texlive-binaries texlive-doc-de texlive-extra-utils
  texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-generic-recommended texlive-lang-german texlive-latex-base
  texlive-latex-base-doc texlive-latex-extra texlive-latex-extra-doc
  texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex
  texlive-music texlive-pictures texlive-pictures-doc texlive-pstricks
  texlive-pstricks-doc tipa
0 upgraded, 43 newly installed, 0 to remove and 0 not upgraded.
Need to get 714 MB of archives.
After this operation, 1.104 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main tex-common all 4.04 [621 kB]
Get:2 http://security.ubuntu.com/ubuntu/ trusty-security/main libyaml-0-2 amd64 0.1.4-3ubuntu3.1 [48,1 kB]
Get:3 http://security.ubuntu.com/ubuntu/ trusty-security/main ruby1.9.1 amd64 1.9.3.484-2ubuntu1.2 [35,6 kB]
Get:4 http://security.ubuntu.com/ubuntu/ trusty-security/main libruby1.9.1 amd64 1.9.3.484-2ubuntu1.2 [2.645 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/main fonts-lmodern all 2.004.4-3 [6.380 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty/main lmodern all 2.004.4-3 [12,4 MB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/main fonts-texgyre all 2.004.2-4 [9.790 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ trusty/main tex-gyre all 2.004.2-4 [7.130 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty/main libptexenc1 amd64 2013.20130729.30972-2build3 [33,9 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-binaries amd64 2013.20130729.30972-2build3 [4.059 kB]
Get:11 http://archive.ubuntu.com/ubuntu/ trusty/main luatex amd64 0.76.0-3ubuntu1 [2.776 kB]
Get:12 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-base all 2013.20140215-1 [16,2 MB]
Get:13 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-latex-base all 2013.20140215-1 [828 kB]
Get:14 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-latex-recommended all 2013.20140215-1 [7.268 kB]
Get:15 http://archive.ubuntu.com/ubuntu/ trusty/main latex-xcolor all 2.11-1.1 [603 kB]
Get:16 http://archive.ubuntu.com/ubuntu/ trusty/main pgf all 2.10-1 [5.668 kB] 
Get:17 http://archive.ubuntu.com/ubuntu/ trusty/main latex-beamer all 3.24-1 [3.788 kB]
Get:18 http://archive.ubuntu.com/ubuntu/ trusty/main ruby all 1:1.9.3.4 [5.334 B]
Get:19 http://archive.ubuntu.com/ubuntu/ trusty/universe m-tx amd64 0.60d.ctan20131214-1 [532 kB]
Get:20 http://archive.ubuntu.com/ubuntu/ trusty/universe musixtex amd64 1:1.15.ctan20131214-1 [6.684 kB]
Get:21 http://archive.ubuntu.com/ubuntu/ trusty/universe pmx amd64 2.7.0.ctan20131214-1 [737 kB]
Get:22 http://archive.ubuntu.com/ubuntu/ trusty/main preview-latex-style all 11.87-1ubuntu2 [187 kB]
Get:23 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-generic-recommended all 2013.20140215-1 [2.114 kB]
Get:24 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-pstricks all 2013.20140215-2 [26,2 MB]
Get:25 http://archive.ubuntu.com/ubuntu/ trusty/main prosper all 1.00.4+cvs.2007.05.01-4 [449 kB]
Get:26 http://archive.ubuntu.com/ubuntu/ trusty/main ps2eps amd64 1.68-1build1 [34,4 kB]
Get:27 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-fonts-recommended all 2013.20140215-1 [5.715 kB]
Get:28 http://archive.ubuntu.com/ubuntu/ trusty/main texlive all 2013.20140215-1 [14,2 kB]
Get:29 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-extra-utils all 2013.20140215-2 [10,2 MB]
Get:30 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-font-utils all 2013.20140215-2 [1.712 kB]
Get:31 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-fonts-recommended-doc all 2013.20140215-1 [2.730 kB]
Get:32 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-lang-german all 2013.20140215-1 [21,7 MB]
Get:33 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-latex-base-doc all 2013.20140215-1 [37,1 MB]
Get:34 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-pictures all 2013.20140215-1 [2.414 kB]
Get:35 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-latex-extra all 2013.20140215-2 [7.286 kB]
Get:36 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-latex-extra-doc all 2013.20140215-2 [317 MB]
Get:37 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-latex-recommended-doc all 2013.20140215-1 [35,0 MB]
Get:38 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-luatex all 2013.20140215-1 [8.204 kB]
Get:39 http://archive.ubuntu.com/ubuntu/ trusty/universe texlive-music all 2013.20140215-2 [9.504 kB]
Get:40 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-pictures-doc all 2013.20140215-1 [58,0 MB]
Get:41 http://archive.ubuntu.com/ubuntu/ trusty/main texlive-pstricks-doc all 2013.20140215-2 [76,7 MB]
Get:42 http://archive.ubuntu.com/ubuntu/ trusty/main tipa all 2:1.3-19 [3.311 kB]
Get:43 http://archive.ubuntu.com/ubuntu/ trusty/universe texlive-doc-de all 2013.20140215-1 [15,3 kB]
Fetched 714 MB in 3min 21s (3.549 kB/s)                                        
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously unselected package libyaml-0-2:amd64.
(Reading database ... 198054 files and directories currently installed.)
Preparing to unpack .../libyaml-0-2_0.1.4-3ubuntu3.1_amd64.deb ...
Unpacking libyaml-0-2:amd64 (0.1.4-3ubuntu3.1) ...
Selecting previously unselected package tex-common.
Preparing to unpack .../tex-common_4.04_all.deb ...
Unpacking tex-common (4.04) ...
Selecting previously unselected package fonts-lmodern.
Preparing to unpack .../fonts-lmodern_2.004.4-3_all.deb ...
Unpacking fonts-lmodern (2.004.4-3) ...
Selecting previously unselected package lmodern.
Preparing to unpack .../lmodern_2.004.4-3_all.deb ...
Unpacking lmodern (2.004.4-3) ...
Selecting previously unselected package fonts-texgyre.
Preparing to unpack .../fonts-texgyre_2.004.2-4_all.deb ...
Unpacking fonts-texgyre (2.004.2-4) ...
Selecting previously unselected package tex-gyre.
Preparing to unpack .../tex-gyre_2.004.2-4_all.deb ...
Unpacking tex-gyre (2.004.2-4) ...
Selecting previously unselected package libptexenc1.
Preparing to unpack .../libptexenc1_2013.20130729.30972-2build3_amd64.deb ...
Unpacking libptexenc1 (2013.20130729.30972-2build3) ...
Selecting previously unselected package texlive-binaries.
Preparing to unpack .../texlive-binaries_2013.20130729.30972-2build3_amd64.deb ...
Unpacking texlive-binaries (2013.20130729.30972-2build3) ...
Selecting previously unselected package luatex.
Preparing to unpack .../luatex_0.76.0-3ubuntu1_amd64.deb ...
Unpacking luatex (0.76.0-3ubuntu1) ...
Selecting previously unselected package texlive-base.
Preparing to unpack .../texlive-base_2013.20140215-1_all.deb ...
Unpacking texlive-base (2013.20140215-1) ...
Selecting previously unselected package texlive-latex-base.
Preparing to unpack .../texlive-latex-base_2013.20140215-1_all.deb ...
Unpacking texlive-latex-base (2013.20140215-1) ...
Selecting previously unselected package texlive-latex-recommended.
Preparing to unpack .../texlive-latex-recommended_2013.20140215-1_all.deb ...
Unpacking texlive-latex-recommended (2013.20140215-1) ...
Selecting previously unselected package latex-xcolor.
Preparing to unpack .../latex-xcolor_2.11-1.1_all.deb ...
Unpacking latex-xcolor (2.11-1.1) ...
Selecting previously unselected package pgf.
Preparing to unpack .../archives/pgf_2.10-1_all.deb ...
Unpacking pgf (2.10-1) ...
Selecting previously unselected package latex-beamer.
Preparing to unpack .../latex-beamer_3.24-1_all.deb ...
Unpacking latex-beamer (3.24-1) ...
Selecting previously unselected package ruby.
Preparing to unpack .../ruby_1%3a1.9.3.4_all.deb ...
Unpacking ruby (1:1.9.3.4) ...
Selecting previously unselected package ruby1.9.1.
Preparing to unpack .../ruby1.9.1_1.9.3.484-2ubuntu1.2_amd64.deb ...
Unpacking ruby1.9.1 (1.9.3.484-2ubuntu1.2) ...
Selecting previously unselected package libruby1.9.1.
Preparing to unpack .../libruby1.9.1_1.9.3.484-2ubuntu1.2_amd64.deb ...
Unpacking libruby1.9.1 (1.9.3.484-2ubuntu1.2) ...
Selecting previously unselected package m-tx.
Preparing to unpack .../m-tx_0.60d.ctan20131214-1_amd64.deb ...
Unpacking m-tx (0.60d.ctan20131214-1) ...
Selecting previously unselected package musixtex.
Preparing to unpack .../musixtex_1%3a1.15.ctan20131214-1_amd64.deb ...
Unpacking musixtex (1:1.15.ctan20131214-1) ...
Selecting previously unselected package pmx.
Preparing to unpack .../pmx_2.7.0.ctan20131214-1_amd64.deb ...
Unpacking pmx (2.7.0.ctan20131214-1) ...
Selecting previously unselected package preview-latex-style.
Preparing to unpack .../preview-latex-style_11.87-1ubuntu2_all.deb ...
Unpacking preview-latex-style (11.87-1ubuntu2) ...
Selecting previously unselected package texlive-generic-recommended.
Preparing to unpack .../texlive-generic-recommended_2013.20140215-1_all.deb ...
Unpacking texlive-generic-recommended (2013.20140215-1) ...
Selecting previously unselected package texlive-pstricks.
Preparing to unpack .../texlive-pstricks_2013.20140215-2_all.deb ...
Unpacking texlive-pstricks (2013.20140215-2) ...
Selecting previously unselected package prosper.
Preparing to unpack .../prosper_1.00.4+cvs.2007.05.01-4_all.deb ...
Unpacking prosper (1.00.4+cvs.2007.05.01-4) ...
Selecting previously unselected package ps2eps.
Preparing to unpack .../ps2eps_1.68-1build1_amd64.deb ...
Unpacking ps2eps (1.68-1build1) ...
Selecting previously unselected package texlive-fonts-recommended.
Preparing to unpack .../texlive-fonts-recommended_2013.20140215-1_all.deb ...
Unpacking texlive-fonts-recommended (2013.20140215-1) ...
Selecting previously unselected package texlive.
Preparing to unpack .../texlive_2013.20140215-1_all.deb ...
Unpacking texlive (2013.20140215-1) ...
Selecting previously unselected package texlive-extra-utils.
Preparing to unpack .../texlive-extra-utils_2013.20140215-2_all.deb ...
Unpacking texlive-extra-utils (2013.20140215-2) ...
Selecting previously unselected package texlive-font-utils.
Preparing to unpack .../texlive-font-utils_2013.20140215-2_all.deb ...
Unpacking texlive-font-utils (2013.20140215-2) ...
Selecting previously unselected package texlive-fonts-recommended-doc.
Preparing to unpack .../texlive-fonts-recommended-doc_2013.20140215-1_all.deb ...
Unpacking texlive-fonts-recommended-doc (2013.20140215-1) ...
Selecting previously unselected package texlive-lang-german.
Preparing to unpack .../texlive-lang-german_2013.20140215-1_all.deb ...
Unpacking texlive-lang-german (2013.20140215-1) ...
Selecting previously unselected package texlive-latex-base-doc.
Preparing to unpack .../texlive-latex-base-doc_2013.20140215-1_all.deb ...
Unpacking texlive-latex-base-doc (2013.20140215-1) ...
Selecting previously unselected package texlive-pictures.
Preparing to unpack .../texlive-pictures_2013.20140215-1_all.deb ...
Unpacking texlive-pictures (2013.20140215-1) ...
Selecting previously unselected package texlive-latex-extra.
Preparing to unpack .../texlive-latex-extra_2013.20140215-2_all.deb ...
Unpacking texlive-latex-extra (2013.20140215-2) ...
Selecting previously unselected package texlive-latex-extra-doc.
Preparing to unpack .../texlive-latex-extra-doc_2013.20140215-2_all.deb ...
Unpacking texlive-latex-extra-doc (2013.20140215-2) ...
Selecting previously unselected package texlive-latex-recommended-doc.
Preparing to unpack .../texlive-latex-recommended-doc_2013.20140215-1_all.deb ...
Unpacking texlive-latex-recommended-doc (2013.20140215-1) ...
Selecting previously unselected package texlive-luatex.
Preparing to unpack .../texlive-luatex_2013.20140215-1_all.deb ...
Unpacking texlive-luatex (2013.20140215-1) ...
Selecting previously unselected package texlive-music.
Preparing to unpack .../texlive-music_2013.20140215-2_all.deb ...
Unpacking texlive-music (2013.20140215-2) ...
Selecting previously unselected package texlive-pictures-doc.
Preparing to unpack .../texlive-pictures-doc_2013.20140215-1_all.deb ...
Unpacking texlive-pictures-doc (2013.20140215-1) ...
Selecting previously unselected package texlive-pstricks-doc.
Preparing to unpack .../texlive-pstricks-doc_2013.20140215-2_all.deb ...
Unpacking texlive-pstricks-doc (2013.20140215-2) ...
Selecting previously unselected package tipa.
Preparing to unpack .../tipa_2%3a1.3-19_all.deb ...
Unpacking tipa (2:1.3-19) ...
Selecting previously unselected package texlive-doc-de.
Preparing to unpack .../texlive-doc-de_2013.20140215-1_all.deb ...
Unpacking texlive-doc-de (2013.20140215-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 7 added doc-base files...
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Setting up libyaml-0-2:amd64 (0.1.4-3ubuntu3.1) ...
Setting up tex-common (4.04) ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
texlive-base is not ready, skipping fmtutil-sys --all call
Setting up fonts-lmodern (2.004.4-3) ...
Setting up fonts-texgyre (2.004.2-4) ...
Setting up libptexenc1 (2013.20130729.30972-2build3) ...
Setting up texlive-binaries (2013.20130729.30972-2build3) ...
update-alternatives: using /usr/bin/xdvi-xaw to provide /usr/bin/xdvi.bin (xdvi.bin) in auto mode
update-alternatives: using /usr/bin/bibtex.original to provide /usr/bin/bibtex (bibtex) in auto mode
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVEDIST... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Building format(s) --refresh.
    This may take some time... done.
Setting up luatex (0.76.0-3ubuntu1) ...
texlive-base is not ready, cannot create formats
Setting up texlive-base (2013.20140215-1) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVEDIST... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
/usr/bin/tl-paper: setting paper size for dvips to a4.
/usr/bin/tl-paper: setting paper size for dvipdfmx to a4.
/usr/bin/tl-paper: setting paper size for xdvi to a4.
/usr/bin/tl-paper: setting paper size for pdftex to a4.
Running mktexlsr. This may take some time... done.
Building format(s) --all.
    This may take some time... done.
Setting up preview-latex-style (11.87-1ubuntu2) ...
Setting up ps2eps (1.68-1build1) ...
Processing triggers for tex-common (4.04) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Setting up texlive-font-utils (2013.20140215-2) ...
Setting up texlive-fonts-recommended-doc (2013.20140215-1) ...
Setting up texlive-lang-german (2013.20140215-1) ...
Setting up texlive-latex-base-doc (2013.20140215-1) ...
Setting up texlive-pictures (2013.20140215-1) ...
Setting up texlive-latex-extra-doc (2013.20140215-2) ...
Setting up texlive-latex-recommended-doc (2013.20140215-1) ...
Setting up texlive-luatex (2013.20140215-1) ...
Setting up texlive-pictures-doc (2013.20140215-1) ...
Setting up texlive-pstricks-doc (2013.20140215-2) ...
Setting up lmodern (2.004.4-3) ...
Setting up tex-gyre (2.004.2-4) ...
Setting up texlive-latex-base (2013.20140215-1) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-latex-base.cnf.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.FPhwoVUg
Please include this file if you report a bug.

dpkg: error processing package texlive-latex-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.

dpkg: error processing package pgf (--configure):
 dependency problems - leaving unconfigured
dpkg:  dependency probleNo apport report written because the error message  indicates its a followup error from a previous failure.
                                                  No apport report written because the error message indicates its a  followup error from a previous failure.
                                                                            No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       ms prevent configuration of latex-beamer:
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package latex-beamer (--configure):
 dependency problems - leaving unconfigured
Setting up m-tx (0.60d.ctan20131214-1) ...
Setting up musixtex (1:1.15.ctan20131214-1) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/40musixtex.cnf.
    This may take some time... done.
dpkg: dependency problems prevent configuration of pmx:
 pmx depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package pmx (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up texlive-generic-recommended (2013.20140215-1) ...
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on pgf; however:
  Package pgf is not configured yet.

dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package prosper (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up texlive-fonts-recommended (2013.20140215-1) ...
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-latex-recommended (>= 2013.20130512); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                               dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                               dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on texlive-latex-recommended (>= 2013.20130512); however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-music:
 texlive-music depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-music depends on pmx; however:
  Package pmx is not configured yet.

dpkg: error processing package texlive-music (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package tipa (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for tex-common (4.04) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Building latex-based formats --byhyphen /var/lib/texmf/tex/generic/config/language.dat.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.hqSNsydO
Please include this file if you report a bug.

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-doc-de:
 texlive-doc-de depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-doc-de (--configure):
 dependency problems - leaving unconfigured
Setting up ruby (1:1.9.3.4) ...
Setting up ruby1.9.1 (1.9.3.484-2ubuntu1.2) ...
Setting up libruby1.9.1 (1.9.3.484-2ubuntu1.2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Errors were encountered while processing:
 texlive-latex-base
 texlive-latex-recommended
 latex-xcolor
 pgf
 latex-beamer
 pmx
 texlive-pstricks
 prosper
 texlive
 texlive-extra-utils
 texlive-latex-extra
 texlive-music
 tipa
 tex-common
 texlive-doc-de
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by SeijiSensei on 2016-01-15
> **swpffm said:**
> 
```
$ apt-cache policy libqt4-dev
libqt-dev:
   Installed: (none)
   Candidate: 4:4.6.2-0ubuntu5
   Version table:
      4:4.6.2-0ubuntu5 0
         500 http://cz.archive.ubuntu.com/ubuntu/ **lucid/main** amd64 Packages
```

You've got inconsistent repositories it appears.  That version comes from 10.04 (Lucid) while you're on 14.04 (Trusty). 
Take a look at /etc/apt/sources.list.  All the references should be to trusty, not lucid.  Lucid isn't even supported any longer.  If you don't see the problem there, look at the files in /etc/apt/sources.list.d/. They should all say "trusty" and not "lucid."

---

### Post by swpffm on 2016-01-15
Thanks. No idea why this happened, but meanwhile all repositories are trusty, see my current `/etc/apt/sources.list` above. But there are still those texlive issues:

```
$ sudo apt-get install -f  
[sudo] password for swpffm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up tex-common (4.04) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Building format(s) --all.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.KUhomh9L
Please include this file if you report a bug.

No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                           No apport report written because MaxReports is reached already
                                                                                                         No apport report written because MaxReports is reached already
                                                                                                                                                                       No apport report written because MaxReports is reached already
                                                            No apport report written because MaxReports is reached already
                                                                                                                          No apport report written because MaxReports is reached already
               No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                                                                                                           No apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
                                                                                              No apport report written because MaxReports is reached already
                                                                                                                                                            No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                                                                                                               dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-latex-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 latex-xcolor depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.

dpkg: error processing package pgf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pmx:
 pmx depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.
 pmx depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package pmx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on pgf; however:
  Package pgf is not configured yet.
 texlive-pstricks depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.

dpkg: error processing package prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-latex-recommended (>= 2013.20130512); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-extra-utils depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-latex-extra depends on texlive-latex-recommended (>= 2013.20130512); however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-music:
 texlive-music depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-music depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-music depends on pmx; however:
  Package pmx is not configured yet.

dpkg: error processing package texlive-music (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 tipa depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package tipa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-de:
 texlive-doc-de depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-doc-de (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-latex-base
 texlive-latex-recommended
 latex-xcolor
 pgf
 latex-beamer
 pmx
 texlive-pstricks
 prosper
 texlive
 texlive-extra-utils
 texlive-latex-extra
 texlive-music
 tipa
 texlive-doc-de
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by swpffm on 2016-01-16
Just wanted to mention that I have been game enough to try the texlive installer again...

I uninstalled everything related to tex with apt-get purge, than I manually removed remaining files by [this guide]("http://tex.stackexchange.com/questions/95483/how-to-remove-everything-related-to-tex-live-for-fresh-install-on-ubuntu"). Than I installed texlive by the installer again. Finally I told apt-get about my texlive by [this german guide]("https://wiki.ubuntuusers.de/TeX_Live_DVD-Installation/#Paketverwaltung-die-neue-TeX-Live-Version-mitteilen"). I think this last thing was the crucial thing that I have been missing before. (Other packages needed texlive but didn't know about this. So aptitude suggested weird workarounds.)

So everything is working now. Thanks alot for all hints deadflowr and SeijiSensei!

---

