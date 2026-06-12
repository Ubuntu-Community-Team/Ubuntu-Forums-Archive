---
title: "Help with Java"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by huero on 2008-05-03
*****PROBLEM SOLVED *****

Hello,

I apologize in advance if this is something simple but I've searched and not been able to find a solution.  I believe I have Sun Java 6 properly installed on ubuntu 8.04 32 bit.  I would like to use the chatroom on this site and it seems to not load [http://www.kci.org](http://www.kci.org).  As far as I can tell java is installed properly as I followed an installation guide and also used the update-java-alternative script to point to the sun java.  I am also using Firefox 3.0b5 as my browser 

thanks

---

### Post by sloggerkhan on 2008-05-03
On my computer it seems to display the loading bar forever. I think it's most likely a website issue. Have you tested your java install at sun's website?
If that functions, you do not have a problem, they have a problem.
Any one of the following should help you verify your java install:
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)
[http://javatester.org/version.html](http://javatester.org/version.html)

---

### Post by Nepherte on 2008-05-03
That chatroom works over here. I can get to the user name & login box.
Are you sure you installed the java plugin for firefox too? Assuming you have java6:
```
sudo apt-get install sun-java6-plugin
```
You can verify that the plugin is installed by typing about:plugins in your firefox browser and see if it is listed there.

---

### Post by Standy on 2008-05-03
This is kinda annoying but.. i've been messing around with java, trying to get it to install... i have probably messed up a lot. trying to follow different guides etc. I am very new to this the past post did not help very much i get the following reply: 

~$ sudo apt-get install sun-java6-plugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

I've tried to install from synatpic manager but i cant find the "sun-java6-plugin" file.. (obviously means it's not there..)

any clues or hints to what i can do?

---

### Post by howlingmadhowie on 2008-05-03
you can download the firefox plugin as part of the jre from sun directly and then copy it to your firefox/plugins folder. it _should_ work, however you may need to install another plugin for firefox to enable java, as the sun plugin may not yet work with firefox3.

---

### Post by gandaran on 2008-05-03
> **Standy said:**
> This is kinda annoying but.. i've been messing around with java, trying to get it to install... i have probably messed up a lot. trying to follow different guides etc. I am very new to this the past post did not help very much i get the following reply: 

~$ sudo apt-get install sun-java6-plugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

I've tried to install from synatpic manager but i cant find the "sun-java6-plugin" file.. (obviously means it's not there..)

any clues or hints to what i can do?

probably means you haven't enabled all the repositories?

post the output of,  gedit /etc/apt/sources.list

---

### Post by Standy on 2008-05-03
It's alot of text, but.. here goes:


# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by phread59 on 2008-05-03
Try looking in Synaptic for the "restricted extras" file and add it.  I believe you will find the java plug ins in there.  That is all I did and I'm working fine.

Mark Shuman

---

### Post by huero on 2008-05-03
Thanks to all of you who replied!  I have solved the problem.  While I did have Java installed I didn't have the sun-java6-jdk package installed.  As soon as I installed it and did a "sudo update-java-alternatives -s sun-java6"  All is working..

---

### Post by kanna1620 on 2008-05-03
> **Nepherte said:**
> That chatroom works over here. I can get to the user name & login box.
Are you sure you installed the java plugin for firefox too? Assuming you have java6:
```
sudo apt-get install sun-java6-plugin
```
You can verify that the plugin is installed by typing about:plugins in your firefox browser and see if it is listed there.

Hi, I have installed the sun-java6-plugin and had the latest java installed from sun. But still my browser not able to run java applets. My browser is firefox-2. After upgrading to HH, it is not running any java thing in the browser. But before upgradation it worked so well. What to do? Help would be appreciated.

---

### Post by phread59 on 2008-05-03
Yea I just got that too.  I was just going to suggest doing a Java config.  I just went through the same thing.  Had the open source version selected as default.  had to switch it to the Sun java 6.  Glad you got squared away.

Mark Shuman

---

