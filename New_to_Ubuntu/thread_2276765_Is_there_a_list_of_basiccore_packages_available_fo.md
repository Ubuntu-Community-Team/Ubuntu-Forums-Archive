---
title: "Is there a list of basic/core packages available for a fresh install of ubuntu?"
date: 2015-05-04
forum: New to Ubuntu
---

### Post by rosie3 on 2015-05-04
Hi there,

I am new to owning my own linux system. I need to use several bioinformatics packages for work, however each package seems to have many dependencies, of which also have many dependencies..

Is there a (or several) basic packages that contain many of the commonly used tools/packages that most programs require, just as a starting point? or is there a list of these core packages somewhere that I can work through installing?

Thank you and kind regards,

Rosie

---

### Post by wildmanne39 on 2015-05-04
When you try to install the applications you need it brings up the dependencies needed and it should offer to install them along with the application and is that not happening? if it is just let it install them, sometimes the dependencies are not available and that is where the issue begins.
 
> Is there a (or several) basic packages that contain many of the commonly used tools/packages that most programs require, just as a starting point? or is there a list of these core packages somewhere that I can work through installing?
Not that I know of. Each application as you are finding out has its own dependencies and you just install them as needed.

You really do not want to just install a lot of dependencies that you may or may not use anyway it would just clutter up your system and may slow it down.

---

### Post by grahammechanical on 2015-05-04
As far as I know there are two package formats used in Linux. Ubuntu is in the process of bringing a third package method called Snap packaging or Snappy packaging.

Ubuntu is built on Debian and so Ubuntu uses the Debian package format. It is simply call deb. It is my understanding that a deb package has to be constructed in such a way that the installer will know what dependencies have to be installed along with the particular package.

So, if we are installing deb packages all the dependences should be taken care of by the dpkg utility. This is especially true of applications installed through the Ubuntu software Centre.

[https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html)

If for some reason the package has dependencies that cannot be installed and if we are installing from the command line we will get an error message telling us about the packages that are needed.

So, are these bioinformatic packages already packaged in the deb package format? Does the code needed to be complied as a deb package? If a package is labelled as for Ubuntu, then all the dependencies should be taken care of. There may be problems if the package was compiled for an old version of Ubuntu and we are using a later version.

The Ubuntu Software Centre has Unipro ugene - a unified bioinformatics toolkit.

[http://ugene.unipro.ru/](http://ugene.unipro.ru/)

[https://www.biostars.org/p/16778/](https://www.biostars.org/p/16778/)

[http://www.bioinformatics.org/wiki/Software](http://www.bioinformatics.org/wiki/Software)

And then there is this

[http://environmentalomics.org/bio-linux/](http://environmentalomics.org/bio-linux/)
> 
Bio-Linux 8 adds more than 250 bioinformatics packages to an [Ubuntu Linux 14.04 LTS]("https://help.ubuntu.com/14.04/ubuntu-help/index.html") base, providing around 50 graphical applications and several hundred command line tools. The [Galaxy environment]("http://environmentalomics.org/bio-linux-galaxy/") for browser-based data analysis and workflow construction is also incorporated in Bio-Linux 8.

> **You can [install Bio-Linux ]("http://environmentalomics.org/bio-linux-installation/")on your machine**,  either as the only operating system, or as part of a dual-boot set-up  which allows you to use your current system and Bio-Linux on the same  hardware.

 **Bio-Linux can also run Live from a DVD or a USB stick.** This  runs in the memory of your machine and does not involve installing  anything. This is a great, no-hassle way to try out Bio-Linux,  demonstrate or teach with it, or to work with it when you are on the  move.



I think that is a much better way then trying to install 250 bioinformatics packages individually to an existing Ubuntu 14.04 installation. But if you want to do it that way Bio-Linux gives this information

[http://nebc.nerc.ac.uk/nebc_website_frozen/nebc.nerc.ac.uk//tools/bio-linux-7/other-bl-docs/package-repository](http://nebc.nerc.ac.uk/nebc_website_frozen/nebc.nerc.ac.uk//tools/bio-linux-7/other-bl-docs/package-repository)

Regards.

---

### Post by rosie3 on 2015-05-04
Dear Wild Man and grahammechanical,

Thank you for your reponses. I have encountered as you have described, failed installs with prompts to install dependencies, with some dependencies as basic as compilers like gcc.

I am installing from command line and some of the bioinformatics packages are in addition to those in the toolkit you have suggested e.g. BEAST, Gubbins (thank you for this toolkit too). These packages are in different formats e.g. precompiled tar balls, can be installed with apt-get..

It looks like I'll just have to work through the list of dependencies suggested from failed installs ...

Thank you for help,

Rosie

---

### Post by sandyd on 2015-05-04
If you have a list of the specific programs you need, we may be able to help you further.

Some software is not in the repos, but are packaged in PPAs, or additional repositories that are not included by default in Ubuntu.

---

### Post by rosie3 on 2015-05-04
Dear sandyd,

Thank you for your help. Here are some programs which I will be using:


[LIST=1]
[*]Gubbins
[*]BEAST2
[*]Trimmomatic
[*]BWA
[*]Samtools
[*]VCFutils
[*]RAxML
[*]FigTree
[/LIST]

Thanks again,

Rosie

---

### Post by sandyd on 2015-05-04
> **rosie3 said:**
> Dear sandyd,

Thank you for your help. Here are some programs which I will be using:


[LIST=1]
[*]Gubbins - ([wishlist item]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=764232")) | [PPA]("https://launchpad.net/~ap13/+archive/ubuntu/gubbins")
[*]BEAST2
[*]Trimmomatic - in repos (trimmomatic)
[*]BWA - in repos (bwa)
[*]Samtools - in repos (samtools)
[*]VCFutils - [in samtools?]("http://packages.ubuntu.com/trusty/i386/samtools/filelist")
[*]RAxML - in repos (ramxml)
[*]FigTree - in repos (figtree)
[/LIST]

Thanks again,

Rosie

A lot of them have been added/mantained by Debian MED team, BEAST2 was apparently in consideration, but it never made it into the repos as far as I can tell.

---

### Post by rosie3 on 2015-05-05
Dear grahammechanical, 

Great find with Bio-Linux. Thanks for that. It will be very helpful.

I have started the painful process of installing of all the dependencies  to get the additional packages working. Sandyd, thank you for pointing  out all the software available in the repositories, I was more getting  stuck on having to install all the basic linux tools to be able to  install these packages e.g. gcc, make, git, autoconf, python etc etc ...

Slowly, but surely, I'll get there.

Thanks everyone for all your speedy help so far.

---

### Post by dino99 on 2015-05-05
Maybe considering some other ways:
[https://wiki.ubuntu.com/Core](https://wiki.ubuntu.com/Core)
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)  (can be applied to other flavour than Lubuntu)

When ubuntu is installed (by default) it apply some meta-packages that can be ignored, except at least ubuntu-minimal. The others are: ubuntu-standard, xserver-xorg-video-all, xserver-xorg-input-all. And localepurge can set the minimal languages list used.

---

### Post by mastablasta on 2015-05-05
only for BEAST2 - the others, as you can see, are either in official repositories or have a PPA.

there should be a list of things you need in some readme or install file in the tarball.

---

