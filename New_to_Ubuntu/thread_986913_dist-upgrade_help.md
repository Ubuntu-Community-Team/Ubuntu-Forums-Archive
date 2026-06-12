---
title: "dist-upgrade help"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by adobrakic on 2008-11-19
For some reason, I can't get dist-upgrade to work. It doesn't upgrade three files, and wants to update one file but it's corrupt.

```
ado@ado-desktop ~ $ sudo apt-get dist-upgrade --force-yes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  acroread-debian-files
The following packages have been kept back:
  acroread mencoder mplayer
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/13.9kB of archives.
After this operation, 135kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `crossover-standard-demo' missing, assuming package has no files currently installed.
111800 files and directories currently installed.)
Unpacking acroread-debian-files (from .../acroread-debian-files_0.0.24medibuntu1.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread-debian-files_0.0.24medibuntu1.1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package acroread
Errors were encountered while processing:
 /var/cache/apt/archives/acroread-debian-files_0.0.24medibuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ado@ado-desktop ~ $ 

```

---

### Post by bscbrit on 2008-11-19
My guess is that dist-upgrade has rewritten your sources.list file to use the new distribution but it doesn't know about a new medibuntu source.  It cannot change it automatically and therefore, in the new sources.list it cannot find the packages that you have installed from the medibuntu source. Or, it is finding conflicting sources for acroread.  What is the content of your new /etc/apt/sources.list?

---

### Post by adobrakic on 2008-11-19
> ## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 5 Elyssa (stable) +++
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) elyssa main upstream import 

## +++ Backports (not as stable) +++
## deb [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa backport

## +++ Community (not as stable) +++
## deb [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa community

## +++ Romeo (unstable) +++
## deb [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa romeo

## +++ Source Repositories +++
## deb-src [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa main upstream import
## deb-src [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa community
## deb-src [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa backport
## deb-src [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa romeo

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 8.04 Hardy (stable) +++
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse 
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock


## +++ Backports & Proposed (not as stable) +++
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-proposed main restricted universe multiverse

## +++ Source Repositories +++
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted universe multiverse
## deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-proposed main restricted universe multiverse
##deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
##deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) hardy partner 

## +++ Medibuntu (stable) +++
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free 
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main 

## +++ LastFM (stable) +++
deb [http://apt.last.fm/](http://apt.last.fm/) debian stable 

deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) hardy/


  ff

---

### Post by kansasnoob on 2008-11-19
Uh, I don't quite think Mint is into full upgrade stage yet!

They're working on it!

---

### Post by bscbrit on 2008-11-20
I'm not sure that you should be running Mint, Medibuntu, LastFM and Hardy repos side by side. If they are identical then there is no difference between any of them - so what would be the point of having them all?  If they have different content then you are leaving yourself vulnerable to having inconsistencies in your packages.

It is difficult enough to keep the Ubuntu repos in step, but you appear to be freely mixing Mint, Ubuntu, Medibuntu and LastFM.  You should expect to experience package problems when carrying out a dist-upgrade - which you have.  The fact that you are upgrading Ubuntu from one version to another means that you will have to identify the equivalent versions in each of the other sets of repos and change the contents of your file manually.

This is not to say that some packages from each repo set cannot be persuaded to work nicely together but I don't think that you can expect the automatic upgrade to know which repos take priority when there is a conflict.  The fact that it is only holding back a few packages is quite an achievement.

Just of out of interest, and if you don't mind me asking, which packages do you need that are not in the Ubuntu Hardy repos? Acroread is obviously one. If there is enough demand for them they might get included in the appropriate repo,

---

### Post by adobrakic on 2008-11-21
Well I can take the LastFM one out for sure. But I don't really know about the other ones. I haven't been using Linux long, so I don't really know which repo holds what stuff, and if any of them hold the same stuff.

If that makes sense.

---

### Post by bscbrit on 2008-11-21
If you do a dist-upgrade but there are no upgraded versions of the additional programs that you have installed then you might find that you lose the use of those programs.  Mixing repos sources is always a risk. But if, say, acroread requires a library of xyz.1.0 **or later** then it is highly unlikely that acroread will stop working simply because you have upgraded to xyz.1.1.  There is a good chance that all will function as it does now - but there is no guarantee.

If you want to continue then I would suggest that you comment out each of the repos except for Hardy.

Then do the dist upgrade.  Check each of the additional programs e.g. acroread, to see if they still functions.  If they do, then all well and good, but if not then you will have to search for a repos that contains a version of acroread which is compatible with your upgrade.

On a completely different track, if you find that you are simply using numerous repos to enable you to continue to use Windows specific programs, then you might want to reconsider your dependence on those programs.  As the only one that you have named is acroread it is hard for me to make any firm constructive proposals.  There are, of course, .deb packages available direct from Adobe and the medibuntu repo has the package that you are already using and it shouldn't stop the dist-upgrade process. However, there are other perfectly good PDF readers (e.g. Evince) already in your ubuntu repos, or you can install a PDF plug-in to Firefox.  As I do not know how you are using acroread I cannot make any better suggestion.

I would be genuinely interested in what you need the different repos for - if there is something seriously lacking in Ubuntu then perhaps we can get it included in the future.  What do Mint or LastFM offer that Ubuntu doesn't?

---

### Post by adobrakic on 2008-11-21
```
I would be genuinely interested in what you need the different repos for - if there is something seriously lacking in Ubuntu then perhaps we can get it included in the future. What do Mint or LastFM offer that Ubuntu doesn't?
```

As for LastFM, I couldn't get that from the Ubuntu repos. But now that I've uninstalled that and don't need it anymore, it's not really an issue. Mint already came in the repos, so I don't really know how to answer your question.

Like I said in my previous post, I don't really know what each of these repos contain. So if they do have the same files in them, I'm completely oblivious to that fact.

Should I delete all of the repos, other than Ubuntu?

---

### Post by bscbrit on 2008-11-22
I would estimate that most Ubuntu users get by using only the standard Ubuntu repos i.e. Hardy or Intrepid.  If you say that Mint 'came in the repos' then I am assuming that it was Mint that you installed?  Ubuntu does not include the Mint repos but it is quite feasible that Mint does include the Ubuntu repos.  If you installed Mint then you will have to keep both the Mint and Hardy repos but, as you have found, you might encounter the occasional glitch because Mint and Hardy are not exactly in step.  You shouldn't really try to upgrade until the next version of Mint is released and I would recommend that, if this is the case, that you stay with the release that you have now.  Mint Version 6 is now at Release Candidate 1 stage so I would expect an upgrade in the next few weeks or so.

I'm not a Mint user but, after looking at their website, it seems that the main advantage of Mint over a standard Ubuntu distro is the automatic inclusion of media codecs.  The important word here is 'automatic' - all the same media codecs are available for Ubuntu but they have to be installed by the user after the installation of the base system is complete.  But Mint has a small but loyal following so it must be doing something right.  Again, I recommend that you leave your current version as it is and wait for Mint to upgrade to version 6.

Medibuntu is a packaging project which includes specific media packages which for legal reasons cannot be included in the base Ubuntu distro.  In some countries using the media codecs is illegal because they are viewed as sidestepping the laws regarding copyright or circumventing Digital Rights Management.  Other countries have, in my view, a far more sensible legal stance and allow you to view your own legally purchased media on whatever system you want.  The only package that I know you have downloaded from Medibuntu is acroread.  Only you can decide whether it is so important to you that you must keep it or whether one of the standard PDF readers would meet your needs.

LastFM I know nothing about.

What you have encountered appears to be an inconsistency in versions and/or packaging between the 3 repos that you are using - Ubuntu, Medibuntu and Mint.  You should not mix packages between the 3 repos unless you are happy to resolve the problems that will occur from time to time.  If you initially installed Mint then stick with that if it meets your needs.  By the way, this is not Ubuntu specific but exists in all of the other typical packaging systems.  If you were a Fedora user, for example, then there are repos which must not be used together because they simply do not work.

In short, stick with Mint but if you find that it does not do everything that you would like, come back to the forums with a specific question and I am sure someone will be able to suggest an alternative package that will do what you want.  You might also try removing acroread before commencing the upgrade and then re-installing it again afterwards.  That might solve your problem if it is simply a case of a corrupted acroread package.

---

### Post by adobrakic on 2008-11-22
I see what you mean
Thanks

---

