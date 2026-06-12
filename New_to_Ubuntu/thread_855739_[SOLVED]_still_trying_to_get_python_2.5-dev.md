---
title: "[SOLVED] still trying to get python 2.5-dev"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-10
im assuming that the error i get:ick@rick-laptop:~$ sudo apt-get install python2.5-dev
[sudo] password for rick: 
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
  python2.5-dev: Depends: python2.5 (= 2.5.2-2ubuntu4) but 2.5.2-2ubuntu5 is to be installed
E: Broken packages
rick@rick-laptop:~$ 

i assume python 2.5 dev.2-2ubuntu5 isnt out ,i cant find it in the repositories,any suggestions,im trying to build blender from svn.
rick

---

### Post by brian_p on 2008-07-11
You are not alone:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg902534.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg902534.html)

---

### Post by rixtr66 on 2008-07-11
ahh well i guess that solves that problem!! 
time to wait.:)

---

### Post by tgilber1 on 2008-10-03
Obviously, your python package version is out of sync.  

1.  Go to packages.ubuntu.com and download the correct deb package to your computer.

e.g., [http://packages.ubuntu.com/hardy/amd64/python2.5](http://packages.ubuntu.com/hardy/amd64/python2.5) # is for amd64

2.  Do force remove/reinstall with dpkg - test this command with the --dry-run before actually trying it for real.

e.g., sudo dpkg --dry-run --force-remove-reinstreq -i python2.5_2.5.2-2ubuntu4.1_amd64.deb

3.  If the --dry-run is successful, then proceed to installing the file for real by removing the dry-run option

e.g., sudo dpkg --force-remove-reinstreq -i python2.5_2.5.2-2ubuntu4.1_amd64.deb

4.  Issue following command to verify package, 
 
e.g., dpkg -l python2.5

5.  Note, you may have other dependencies that may require the same actions as described in steps 3 and 4.  Case in point, python2.5-minimal must be updated before python2.5

---

