---
title: "Unmet Dependencies"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by redlabel on 2012-09-07
Hey there.  I'm new to ubuntu and have run into a problem I can't solve.

I've tried to install java runtime 7 and have wound up with an unmet dependency problem. 

I'm new, so i have no idea what the fudge this means.  

Whenever I try install something new I get the following error: 

```
The following packages have unmet dependencies:
 openjdk-7-jre-headless : Depends: openjdk-7-jre-lib (= 7u7-2.3.2-1ubuntu1) but 7~u3-2.1.1~pre1-1ubuntu4 is installed

```

After running ```
sudo apt-get -f install
```

I get this error:

```
dpkg: dependency problems prevent configuration of openjdk-7-jre-headless:amd64:
 openjdk-7-jre-headless:amd64 depends on openjdk-7-jre-lib (= 7u7-2.3.2-1ubuntu1); however:
  Version of openjdk-7-jre-lib on system is 7~u3-2.1.1~pre1-1ubuntu4.

dpkg: error processing openjdk-7-jre-headless:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-7-jre-headless (>= 7~u3-2.1.1~pre1-1) | java6-runtime-headless; however:
  Package openjdk-7-jre-headless:amd64 is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-7-jre-headless:amd64 which provides java6-runtime-headless is not configured yet.

dpkg: error processing ca-certificates-java (--configure):No apport report written because MaxReports is reached already

 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-7-jre-jamvm:amd64:
 icedtea-7-jre-jamvm:amd64 depends on openjdk-7-jre-headless (= 7u7-2.3.2-1ubuntu1); however:
  Package openjdk-7-jre-headless:amd64 is not configured yet.

dpkg: error processing icedtea-7-jre-jamvm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-7-jre-lib:
 openjdk-7-jre-lib depends on openjdk-7-jre-headless (>= 7~b130~pre0); however:
  Package openjdk-7-jre-headless:amd64 is not configured yet.

dpkg: error processing openjdk-7-jre-lib (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 openjdk-7-jre-headless:amd64
 ca-certificates-java
 icedtea-7-jre-jamvm:amd64
 openjdk-7-jre-lib

```

Help would be much appreciated!

Thanks

---

### Post by Bashing-om on 2012-09-07
redlabel; Hi ! Welcome to the forum.

   Lets clean up dpkg ... then try your package install again.
Here is oldfred's great instructions to do so:


oldfres's methology for restoring:
Then try ( all the # are comments do not type anything after a #)
#if not chroot use:  /chroot not for use by new users/
sudo -i
#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
All that does is update it again.
#to get out of the super user mode from sudo -i 
exit 



[INDENT]regards <==BDQ
[/INDENT] 
As you are new to ubuntu, do not hesitate to inguire about the above code or any hesitations about implementing the code. (entering man <the command inquiring about i.e. man apt-get ) in terminal is a great way to learn what a command entails.
[INDENT]regards <==BDQ

[/INDENT]

---

### Post by fuzzmo on 2012-09-17
Just want to say thanks as that sorted out my issue nicely :)

---

### Post by Bashing-om on 2012-09-17
You do good work.

 Please mark the thread as solved from the thread tools menu.

[INDENT]happy ubuntu'n <==BDQ
[/INDENT]

---

### Post by lesliebino on 2013-07-17
> **Bashing-om said:**
> You do good work.

 Please mark the thread as solved from the thread tools menu.[INDENT]happy ubuntu'n <==BDQ
[/INDENT]


HI Bashing-om, 
I like to tell you that I have the same error but doesn't let to pass any of those commands. e.g. can't be upgrade that gives this error:

    You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 openjdk-7-jre-headless : Depends: openjdk-7-jre-lib (= 7u15-2.3.7-0ubuntu1~12.04.1) but 7u21-2.3.9-0ubuntu0.12.04.1 is installed
                          Recommends: icedtea-7-jre-jamvm (= 7u15-2.3.7-0ubuntu1~12.04.1) but it is not installed
E: Unmet dependencies. Try using -f.

If I try apt-get -f install, still gives error. 
so basically all doors closed for me. 

any idea please? thanks

---

### Post by Bashing-om on 2013-07-17
lesliebino; Hi !

Well yeah.. try this: (Americanism/southern dialect) 
```

sudo apt-get update
sudo apt-get purge openjdk-7-jre-headless
sudo rm /var/cache/apt/archives/openjdk-7-jre-headless
sudo apt-get install openjdk-7-jre-headless
sudo apt-get -f install

```
What results ?

[INDENT][INDENT]my little bit to help[/INDENT][/INDENT]

---

### Post by gleedadswell on 2013-07-17
Hi lesliebino,

Before proceeding be VERY sure that your package lists are not just out of date.  Manually uninstalling and installing packages can occasionally get you into hot water.  So double check that you have run the sequence of commands in post #2 and then retry the install. The most important step is probably apt-get update.  If that still doesn't work then you could do

```
apt-get purge 7u21-2.3.9-0ubuntu0.12.04.1
apt-get install openjdk-7-jre-lib

```

and then retry the install you are trying to do.  However, a few words of warning:

1. If you deliberately installed a development version of java for new functionality this might get rid of that functionality.

2. When you purge 7u21-2.3.9-0ubuntu0.12.04.1 it is likely to remove a lot of other packages at the same time (look at the list of packages to be removed before giving it permission to proceed).  Most of those packages (or slightly older versions of them) should be reinstalled when you install openjdk-7-jre-lib, which appears to be an essentially equivalent package.  But it is possible some won't and you will have to install them yourself.  Compare the list of packages being installed with the list being uninstalled.

At first I guessed that maybe you installed 7u21-2.3.9-0ubuntu0.12.04.1 knowingly or unknowingly from a development branch of the repositories? If I'm interpreting the problem correctly it is that 7u21-2.3.9-0ubuntu0.12.04.1, which is installed, is a newer version than openjdk-7-jre-lib, which is a dependency of the package you are trying to install. The package manager is, somewhat reasonably but annoyingly, refusing to install an older version of a package you already have.  The last time I ran into a problem like what you are describing I was running debian-testing.  The dependency problems I had were severe enough to scare me away from doing that on any computer that I'm trying to get serious work done on.

However, as far as I can tell, 7u21-2.3.9-0ubuntu0.12.04.1 is the current version, not a development version.  So I really think your package lists are just out of date.  Do the commands from post #2, even if you think you've already done them, just to be sure.

---

### Post by Bashing-om on 2013-07-17
Great advice!
For the record I show:
> 
sysop@1304mini:~$ apt-cache show openjdk-7-jre-headless
Package: openjdk-7-jre-headless
Priority: optional
Section: java
Installed-Size: 48293
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: OpenJDK Team <openjdk@lists.launchpad.net>
Architecture: amd64
Source: openjdk-7
Version: 7u21-2.3.9-1ubuntu1
--snip--
Recommends: icedtea-7-jre-jamvm (= 7u21-2.3.9-1ubuntu1)


[INDENT][INDENT]safety is no accident[/INDENT][/INDENT]

---

