---
title: "Lazarus: dependencies problem"
date: 2008-09-02
forum: Programming Talk
---

### Post by idanool on 2008-09-02
Hello!

I'm trying to install lazarus on Hardy, but I get the following errors:

> sudo apt-get install lazarus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lazarus: Depends: fp-units-gtk but it is not going to be installed
E: Broken packages


> sudo apt-get install lazarus fp-units-gtk  libgtk2.0-dev libcairo2-dev  libpango1.0-dev libpng12-dev libpng12-0 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpng12-0 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libpng12-dev: Depends: libpng12-0 (= 1.2.15~beta5-3) but 1.2.24-0ubuntu1~fta1 is to be installed
E: Broken packages

---

### Post by MentalNotes on 2008-09-02
The version of libpng you have installed, I'm guessing from a third-party repo, is breaking the dependecies for Lazarus. Your best bet is to find out what repo is causing the breakage and remove it from your sources.list then downgrade to the version that is needed by Lazarus.

---

### Post by nitro_n2o on 2008-09-02
try

sudo aptitude install lazarus

aptitude will try to do the removing and reinstalling work for you

---

### Post by cmay on 2008-09-02
[http://ubuntuforums.org/showthread.php?t=730077&highlight=lazarus](http://ubuntuforums.org/showthread.php?t=730077&highlight=lazarus)
you may also run into this problem when you have installed lazarus. there is a solution but however its a bit sad that the installation of lazarus  is not just easy and painless. i have just installed it also whitout any other problem than the sources are missing. i thought i would just mention it now so you dont have to ask specific for this problem when you have lazarus installed. good luck whit it.

---

### Post by idanool on 2008-09-02
Thanks!
downgrading libpng to the official version and delete the bad one from my local repository fixed the problem.

---

